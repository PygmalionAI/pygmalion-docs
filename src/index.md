---
order: 100000
icon: home
---
![](/static/1500x500.jpeg)
# What is PygmalionAI?

PygmalionAI is an open-source large language model (**LLM**) based on EleutherAI's [GPT-J 6B](https://huggingface.co/EleutherAI/gpt-j-6b){ target="_blank" } and Meta AI's [LLaMA 7B](https://ai.facebook.com/blog/large-language-model-llama-meta-ai/){ target="_blank" }.

In simple terms, Pygmalion is an AI fine-tuned for chatting and roleplaying purposes. The current actively supported Pygmalion AI model is the 7B variant, based on Meta AI's LLaMA model.

## Features
- **Unrestricted**: No measures have been put in place to restrict the output.
- **Low VRAM requirement**: With only 18GB (or less) VRAM required, Pygmalion offers better chat capability than much larger language models with relatively minimal resources.
- **Fine-tuned for RP**: Our curated dataset of high-quality roleplaying data ensures that your bot will be the optimal RP partner.
- **Free and Open-Source**: Both the model weights and the code used to train it are completely open-source, and you can modify/re-distribute it for whatever purpose you want.*
- **Regularly updated**: Pygmalion is regularly updated with new data to improve the model even further.

!!!
`*` Pygmalion-6B uses the [CreativeML Open RAIL-M](https://huggingface.co/spaces/CompVis/stable-diffusion-license){ target="_blank" } license, which is also used by Stable Diffusion. Pygmalion-7B uses LLaMA's license, which is non-commercial.
!!!

## How do I use Pygmalion?

Language models, including Pygmalion, generally run on GPUs since they need access to fast memory and massive processing power in order to output coherent text at an acceptable speed. Pygmalion is no different. You need a powerful GPU to run the model. 

If you don't have a powerful enough GPU, there are alternative solutions. Running the models at lower precision allows even low-vram GPUs to be utilized, and with frameworks such as [GGML](https://github.com/ggerganov/ggml){ target="_blank" }, running the Pygmalion models purely on CPU has been made possible.

These docs will attempt to explain all the possible methods for running the AI, and in a language that is easy to understand. Please navigate to the next section to begin using Pygmalion.
