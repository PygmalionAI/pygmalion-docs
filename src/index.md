---
order: 100000
icon: home
---
![](static/1500x500.jpeg)
# What is PygmalionAI?

PygmalionAI is an open-source large language model (**LLM**) based on EleutherAI's [GPT-J 6B](https://huggingface.co/EleutherAI/gpt-j-6b){ target="_blank" }. 

In simple terms, Pygmalion is an AI fine-tuned for chatting and roleplaying purposes. The current actively supported Pygmalion AI model is the 6B variant, a model with 6 billion parameters. 

## Features
- **Unrestricted**: No measures have been put in place to restrict the output.
- **Low VRAM requirement**: With only 16GB (or less) VRAM required, Pygmalion offers better chat capability than much larger language models with relatively minimal resources.
- **Fine-tuned for RP**: Our curated dataset of high-quality roleplaying data ensures that your bot will be the optimal RP partner.
- **Free and Open-Source**: Both the model weights and the code used to train it are completely open-source, and you can modify/re-distribute it for whatever purpose you want.*
- **Regularly updated**: Pygmalion is regularly updated with new data to improve the model even further.

!!!
`*` PygmalionAI uses the [CreativeML Open RAIL-M](https://huggingface.co/spaces/CompVis/stable-diffusion-license){ target="_blank" } license, which is also used by Stable Diffusion.
!!!

## How do I use Pygmalion?

Language models, including Pygmalion, generally run on GPUs since they need access to fast memory and massive processing power in order to output coherent text at an acceptable speed. Pygmalion is no different. You need a powerful GPU to run the model. 

If you don't have a powerful enough GPU, there are luckily alternative solutions. Google's [Colaboratory](https://colab.research.google.com){ target="_blank" } offers free GPUs for all users - though for a limited time. We have ready-made notebooks that you can run to access Pygmalion. You can also use Colab on your mobile phone.

These docs will attempt to explain all the possible methods for running the AI, and in a language that is easy to understand. We will start with Google Colab, as it's generally the easiest method.