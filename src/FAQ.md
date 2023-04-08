---
order: 1000
icon: question
title: FAQ
---

# Frequently Asked Questions

### How do I use the latest `dev` (v8) version?

If you're running on Google Colab, all notebooks have an option for downloading the `dev` (beta) model. Look for either `Pygmalion 6B Dev` or `Pygmalion 6B Experimental`. 

If you're running locally, make sure `git` is installed and run the following command inside your `KoboldAI/models` or `text-generation-webui/models` folder:
```
git lfs clone https://huggingface.co/PygmalionAI/pygmalion-6b --branch dev
```
If it says `git lfs` was not recognized as a command, please install `git-lfs` with your package manager (Linux) or download [the installer](https://git-lfs.com/) for Windows.

### My character has terrible memory!
This could be due to the limited context size. Pygmalion 6B has a maximum context size of 2048 [tokens](https://en.wikipedia.org/wiki/Lexical_analysis#Tokenization){ target="_blank" }. This includes your character description, example messages, and all your chatlogs. The description and examples are placed at the top of the context memory - all your subsequent chat logs are placed beneath them. This means that if your character description + examples chats are 400 tokens, you'll only have 1648 tokens left for your messages. The bot will forget everything past those 1648 tokens.

Character editors/creators such as TavernAI's will give you a token count for your character, but you can also use OpenAI's tokenizer service.

[!ref OpenAI Tokenizer](https://platform.openai.com/tokenizer)

### My character's responses are too short!
The character will mimic the example chats and greeting message's style. Keep these in mind if you want to create a verbose character:
- Be descriptive and verbose in your greeting message and example chats.
- Be descriptive and verbose in responses by the user (you!).
- Re-generate the response until you see a satisfactory one.
- Manually edit the character's response to make it more verbose.

### My character is generating nonsense!
Your temperature or repetition penalty settings are likely too high. The recommended range for temperature (for chatbots) is between `0.5` to `0.9` and the ideal range for repetition penalty is between `1.1` to `1.2`.

### My character is not responding anymore!
You have probably run out of GPU memory (also known as VRAM).
If you are using the free Google Colab plan, the GPU provided by Google can't handle the maximum context size (2048 tokens). If you have 16GB of VRAM, please tweak the context size to 1400-1600 (proportionally lower according to your VRAM size).
##### For Text-Gen (Oobabooga) you need to check the `load_in_8bit` option under the 3rd cell before running it.

![](/static/oobactx.png)

##### For TavernAI, running the model in 8bit is not available. The only solution is to slide down the context size to around 1400 (or 1600) in the settings tab.

![](/static/tavernctx.png)

### Do you keep/share any of my data/chat?
The Pygmalion project team does not collect any data other than the chat logs you explicitly consent to donating for the training dataset.
This project is done out of passion, and no one has any intention of collecting, analyzing, or selling any of your data. The Colab notebook automatically passes the `--quiet` argument in KoboldAI, which means your/the bot's responses aren't printed out for Google to see. 

### What are Softprompts? Do I need them?
A soft prompt is a way to modify the style and behavior of your AI. 

They're made by taking a (possibly) huge amount of information and compressing them into a small number of tokens, then feeding it into the embedding layer of the model.
Even if people tend to use it that way, softprompt are not made to add context, lore, etc to the story. But yes, it might work for that if the dataset use to make the softprompt was big enough and made use of good quality data.

### How do I use Softprompts?
- Download your SP of choice from either the Discord or [this Rentry](https://rentry.org/pygsoft){ target="_blank" } a generous anon is maintaining.
- **If you're running locally**: place the `.zip` file (don't extract!) inside the `softprompts` folder - both Oobabooga and KoboldAI have the same folder.
- **If you're using Google Colab**, open your [Google Drive](https://drive.google.com){ target="_blank" } and find the `KoboldAI/softprompts` folder and upload your `.zip` file there.
- Make sure Pygmalion is loaded, then an option for Softprompts should appear.

### Which UI should I use? There's so many of them.
It's up to you, every UI tends to add the same features others as well as try to be compatible with characters from other UIs as well.
If you want to focus on story generation, we recommend using KoboldAI. For chat purposes, TavernAI has the best user interface, followed by Oobabooga. There are other TavernAI alternatives (e.g. miku.gg), but it's up to you in the end. Please refer to their respective pages for a preview of the UI.

[!button text="KoboldAI"](https://docs.alpindale.dev/local-installation-(gpu)/kobold) - 
[!button text="Text-Gen-WebUI"](https://docs.alpindale.dev/local-installation-(gpu)/oobabooga/) - 
[!button text="TavernAI"](https://docs.alpindale.dev/local-installation-(gpu)/tavern/)

### I'm using Google Colab, how much time do I have to use their GPUs?
The amount of time you can use when using the free plan for Google Colab highly depends on the traffic Colab recieves and your usage patterns.
Google says that you can use a Colab Notebook for at most 12 hours if you don't have Compute Units. Pygmalion users tend to say it's less - usually anywhere from two to six hours.

#### How to avoid reaching the GPU quota?
When you're done using Pygmalion, please terminate your Colab session! You'll waste your quota otherwise, and might find yourself unable to connect to a GPU backend the next time you login.
![](/static/cloud1.png)
![](/static/cloud2.png)



#### I've out of GPU time, what do I do now?
If you've run out of GPU time, you can do nothing but wait for your quota to reset. Alternatively, you can purchase Colab Pro to increase your daily/weekly quota.


#### What's a Compute Unit (CU)? Should I buy one?
A CU is a unit that you can buy to be sure to be granted access to a powerful GPU.
Pricing for Compute Engine is based on per-second usage of the machine types, persistent disks, and other resources that you select for your virtual machines.
So it's up to you.

#### I've run out of quota, but I can't buy a Compute Unit! What do I do?
In that case, you can use [Kobold Horde](https://lite.koboldai.net){ target="_blank" }. Generous users are donating their GPU power to the Horde so that people can use them to run language models. Pygmalion is a popular model, so you'll always find people hosting it. Keep in mind that there are more Horde users than workers, so you might have to wait a bit longer for responses.

