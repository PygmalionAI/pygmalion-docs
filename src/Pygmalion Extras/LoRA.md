---
order: 100
icon: file-symlink-file
title: LoRA
---

Low-Rank Adaptation (LoRA) is a paradigm of natural language processing (NLP) that freezes the pre-trained model weights and injects trainable rank decomposition matrices into each layer of the Transformer architecture. Compared to GPT-175B fine-tuned with [Adam](https://arxiv.org/abs/1412.6980), LoRA can reduce the number of trainable parameters by 10,000 times and the GPU memory requirements by 3 times. Refer to the paper below:

[!ref icon="rocket" text="LoRA: Low-Rank Adaptation of Large Language Models"](https://arxiv.org/abs/2106.09685)

## Low-Rank Adaptation

LoRAs are preferred when the traditional fine-tuning methods prove to be too computationally expensive. As demonstrated by Edward Hu et al., training a LoRA is at least 3 times less resource intensive as a native fine-tune. This can be further reduced with INT4 LoRA tuning - made possible by [GPTQ](https://github.com/IST-DASLab/gptq). 

Some of the key advantages LoRAs possess are:

- A pre-trained model can be shared and used to build many small LoRA modules for different downstream tasks. We can freeze the shared model and efficiently switch tasks by replacing the matrices `A` and `B` as demonstrated below, reducing the storage requirement and task-switching overhead significantly.

-![Figure 1](/static/lora.png)

- LoRA makes training more efficient and lowers the hardware barrier to entry by up to 3 times (over 10 times if used in conjunction with GPTQ) when using adaptive optimizers since we don't need to calculate the gradients or maintain the optimizer states for most parameters. Instead we only optimize the injected, *much smaller* low-rank matrices.

- The simple linear design allows us to merge the trainable matrices with the frozen weights when deployed, ***instroducing no inference latency*** compared to a fully fine-tuned model, by construction.

- LoRA is orthogonal to many prior methods and can be combined with many of them, such as prefix-tuning and prompt-tuning.

***

LoRAs were originally designed for LLMs, but they can be used for other objectives, such as diffusion models. The docs here will focus on the language modeling objective of LoRAs. We try to maximize the likelihood of a predicted word given the previous words in a sentence. Imagine we're given a GPT model $\Rho_\Phi(y|x)$ which is parametrized by $\Phi$. For example, $\Rho_\Phi(y|x)$ can be a generic model based on the [Transformers](https://github.com/huggingface/transformers) architecure. Now imagine we will need to adapt this large model to different downstream tasks, such as summarization, machine reading comprehension, and natural language to SQL (NL2SQL). We'll represent each downstream task by a training dataset of context-target pairs: $\large {Z=\text{\textbraceleft}(x_i,y_i)\text{\textbraceright}}_{i = 1,...N}$ where both $x_i$ and $y_i$ are sequences of tokens. For example, in summarization, $x_i$ is the content of the article and $y_i$ is its summary. During full fine-tuning, the model is initialized to pre-trained weights $\Phi_0$ and updated to $\Phi_0 + \Delta\Phi$ by repeatedly following the gradient to maximize the conditional language modeling objective:

$$
\huge{\overset{max}\varPhi \sum_{(x,y)\in\Z}\overset{|y|}\sum_{t=1}\log\Large{(P_\Phi(y_t|x,y<_t))}}
$$

One of the main disadvantages for full fine-tuning is that for *each* downstream task, we learn a *different* set of parameters $\Delta\Phi$, whose dimensions $|\Delta\Phi|$ equals $|\Phi_0|$. If the model is large (such as GPT-3 with 175 Billion parameters ($|\Phi_0|$)), storing and running independent instances of the model for different tasks would be extremely difficult.

LoRAs aim to solve this exact problem. The task-specific parameter increment $\Delta\Phi = \Delta\Phi(\Theta)$ is encoded by a much smaller-sized set of parameters $\Theta$ with $|\Theta| \ll |\Phi_0|$. The task of finding $\Delta\Phi$ then becomes optimizing over $\Theta$:

$$
\huge{\overset{max}\varPhi \sum_{(x,y)\in\Z}\overset{|y|}\sum_{t=1}\log\Large{(p_{\Phi _0}+\Delta\Phi(\Theta)(y_t|x,y<_t))}}
$$

LoRA uses a low-rank representation to encode $\Delta\Phi$ that's both compute and memory efficient. When the model is GPT-3 175B, the number of trainable parameters $|\Theta|$ can be as small as 0.01% of $|\Theta_0|$!

### How does it work?

A neural network contains many dense layers which perform matrix multiplication. The weight matrices in these layers ususally have full-rank. When adapting a specific task, GPT models have a low "instrisic dimension" and can still learn efficiently despite a random projection to a smaller subspace. Inspired by this, Edward Hu et al. hypothesized that the updates to the weights also have a low "instrinsic rank" during adaptation. For a pre-trained weight matrix $W_0 \in \R^{d x k}$, we constrain its update by representing the latter with a low-rank decomposition $W_0 + \Delta W = W_0 + B A$ are multiplied with the same input, and their respective output vectors are summed coordinate-wise. For $h = W_0x$, our modified forward pass yields:

$$
\Large{h = W_0 x + \Delta W_x = W_0 x + B A_x}
$$

Edward Hu et al. illustrate the reparametrization in Figure 1. They used a random Gaussian initialization for $A$ and zero for $B$, so $\Delta W = B A$ is zero at the beginning of the training. We then scale $\Delta W_x$ by $\large{\frac{\alpha}{r}}$, where $\alpha$ is a constant in $r$. When optimizing with [Adam](https://arxiv.org/abs/1412.6980), tuning $a$ is roughly the same as tuning the learning rate if we scale the initialization appropriately. As a result, we simply set $a$ to the first $r$ we try and do not tune it. This scaling helps to reduce the need to retune hyperparameters when we vary $r$. This method introduces **no additional inference latency**. When deployed in production, we can explicitly compute and store $W = W_0 + B A$ and perform inference as usual. Note that both $W_0$ and $B A$ are in $\R^{d x k}$. When we need to switch to another downstream ask (switch LoRA adapters), we can recover $W_0$ by subtracting $B A$ and then adding a different $B' A'$, a quick operation with very little memory overhead.

### What are the benefits of LoRA?

The most significant benefit comes from the reduction in memory and storage usage. For a large model, such as GPT-J, trained with Adam, we reduce that VRAM usage by up to 2/3 if $r \ll d_{model}$ as we do not need to store the optimizer states for the frozen params. On GPT-3 175B, we can reduce the VRAM consumption during training from 1.2TB to 350GB. With $r = 4$ and only the query and value projection matrices being adapted, the checkpoint size is reduced by roughly 10,000x (from 350GB to 35MB). This allows us to train with significantly fewer GPUs and avoid I/O bottlenecks. Another benefit is that we can switch between tasks while deployed at a much lower cost by only swapping the LoRA weights as opposed to all the parameters. This allows for creation of many customized models that can be swapped in and out on the fly. 

LoRA also has its limitations. For example, it's not straightforward to batch inputs to different tasks with different $A$ and $B$ in a single forward pass, if one chooses to absorb $A$ and $B$ into $W$ to eliminate additional latency. Though it's possible to not merge the weights and dynamically choose the LoRA modules to use for samples in a batch for scenarios where latency is not very important.


## How do I train a LoRA?

The [xTuring](https://github.com/stochasticai/xturing) repository contains code for both LoRA and full fine-tuning of LLMs such as LLaMA, GPT-J, and more. The current GPT-J (Pygmalion 6B) training code is only compatible with Alpaca and GPT4All dataset formats, so it will likely be useless for most users. There's currently work being done on creating INT4 LoRA training code for GPT-J, so please be patient and keep an eye out for any updates here.

## How do I load a LoRA?

First, choose what LoRA you want to use. We have a list in the [Discord Server](https://discord.com/invite/pygmalionai). The steps will differ for both Kobold and Oobabooga (TextGen WebUI).

### Oobabooga (TextGen WebUI)
Currently, the easiest way to load a LoRA is via Oobabooga. Open a PowerShell/Terminal instance (press Shift + Righ-Click inside the folder and not on a file, then select "Open in PowerShell), and run this command:

```bash
python3 download-model.py tloen/alpaca-lora-7b
```
>Replace `tloen/alpaca-lora-7b` with the name of the LoRA repo you want. For example, if the link in the Discord post for the LoRA says `https://huggingface.co/nomic-ai/gpt4all-lora`, then you'll have to put `nomic-ai/gpt4all-lora` in there instead.

Then you can launch Oobabooga normally and then select the LoRA from the "Parameters" tab.

### KoboldAI

To use a LoRA with KoboldAI, you will need to merge the LoRA with the base model first. First, grab the LoRA you want from the [Discord Server](https://discord.com/invite/pygmalionai). You can use [`git lfs`](https://docs.alpindale.dev/tools/git) to download the LoRA. Place the downloaded LoRA (if you're on Windows, the default download path is C:\Users\<username>) inside KoboldAI's `models` folder. 

Then grab the merge script from [here](https://github.com/AlpinDale/lora-merge/blob/main/merge.py) and place it in the `models` folder of your KoboldAI directory.

Assuming your Pygmalion model folder is named "pygmalion-7b", open a PowerShell/Terminal instance inside the `models` folder (on Windows, press Shift + Right-Click inside the folder and choose "Open in Powershell"), and type this command in:
```bash
python3 merge.py --base_model pygmalion-7b --lora alpaca-lora --output pygmalion-7b-alpaca-lora
```
>Replace `alpaca-lora` with the name of the LoRA folder!

Now, you can load the new model from the `pygmalion-7b-alpaca-lora` folder, or whatever else you decided to name it.

### koboldcpp

Using LoRAs with [koboldcpp](https://docs.alpindale.dev/local-installation-(cpu)/pygcpp/) requires converting the LoRA to the ggml format first. To do this, grab the LoRA you want from the [Discord Server](https://discord.com/invite/pygmalionai). You can use [`git lfs`](https://docs.alpindale.dev/tools/git) to download the LoRA.

Download [the lora-to-ggml script](https://github.com/ggerganov/llama.cpp/blob/master/convert-lora-to-ggml.py) from the llama.cpp repo, and place as the LoRA folder, but not inside it.

Then you can convert the LoRA using this command:

```bash
python3 convert-lora-to-ggml.py alpaca-lora alpaca-lora-ggml
```
>Replace `alpaca-lora` with the name of the LoRA folder you've downloaded. Same for the output folder.

Place the converted folder in a path you can easily remember, preferably inside the koboldcpp folder (or where the .exe file is for windows).

Then you can run this command:

```bash
python koboldcpp.py --lora alpaca-lora-ggml --nommap --unbantokens
```
>Replace the `alpaca-lora-ggml` with the LoRA folder name. You can add any other arguments you want aside from these.


### KoboldAI 4bit

There's no way to directly use a LoRA in Kobold, not even in the 4bit branch. You will need to merge it with the *base* model, and then convert it to 4bit. The conversion process for 7B takes about 9GB of VRAM so it might be impossible for most users. If you still want to attempt it, follow the steps for KoboldAI until you get a merged model. Then use the [GPTQ-for-LLaMA](https://github.com/qwopqwop200/GPTQ-for-LLaMa) repo to convert the model to 4bit GPTQ format. There are guides in the repo on how to do that.

