---
order: 1
icon: question
title: FAQ
---

# Frequently Asked Questions

### My character has terrible memory!
This could be due to the limited context size. Pygmalion 6B has a maximum context size of 2048 [tokens](https://en.wikipedia.org/wiki/Lexical_analysis#Tokenization). This includes your character description, example messages, and all your chatlogs. The description and examples are placed at the top of the context memory - all your subsequent chat logs are placed beneath them. This means that if your character description + examples chats are 400 tokens, you'll only have 1648 tokens left for your messages. The bot will forgot everything past those 1648 tokens.

Character editors/creators such as TavernAI's will give you a token count for your character, but you can also use OpenAI's tokenizer service.

[!ref OpenAI Tokenizer](https://platform.openai.com/tokenizer)

### My character's responses are too short!
The character will mimic the example chats and greeting message's style. Keep these in mind if you want to create a verbose character:
- Descriptive and verbose greeting message and example chats.
- Descriptive and verbose responses by the user (you!).
- Re-generate the response until you see a satisfactory one.
- Manually edit the character's response to make it more verbose.

### My character is generating nonsense!
Your Temperature or Repetition Penalty settings are likely too high. The recommended range for Temperature (for chatbots) is between `0.5` to `0.9`. The range for Repetition Penalty is between `1.1` to `1.2`.

### My character is not responding anymore!
You have probably run out of memory (VRAM)
If you are using a free access to a Colab notebooks, the GPU provide by Google can't handle a max out context size (2048 tokens). The VRAM is filled quickly and the model can't generate anything more.
The fix depend of which UI you are using.

##### For Text-Gen (Oobabooga) you need to check the "load_in_8bit" option under the 3rd cell before running it.

![ContextSizeOoba'](https://user-images.githubusercontent.com/127881989/225087631-c4e6c91d-6a20-417c-a321-7cc7a5660216.png)

##### For TavernAI, running the model in 8bit is not available. The only solution is to slide down the context size to around 1400 in the settings tab.

![Contextsize Tavern](https://user-images.githubusercontent.com/127881989/225088042-24837247-e9a6-45ed-82cb-8ff7e214e159.png)

### Do you keep/share any of my data/chat?
The Pygmalion project team does not collect any data other than the chat logs you explicitly consent to donating for the training dataset.
This project is done out of passion, and no one has any intention of collecting, analyzing, or selling any of your data.
(ALPIN Tho to be fair I don't know how much "access" google have on the activity of their GPU/TPU, so to be totally transparent wa should add something about that, if you have more info)

### I always hear about Softprompt, what are they ? How are they made ?
A soft prompt is a way to modify the style and behavior of your AI. 
A softprompt is made by taking a (possibly) huge amount of information, and making it more tokens efficient.
Even if people tend to use it that way, softprompt are not made to add context, lore, etc to the story. But yes, it might work for that if the dataset use to make the softprompt was big enough and made of good quality data.
(ALPIN tell me if we should add a "How to make a SP" Tho it's not really Pyg related and there's rentry about that already)

### Which UI should I use, there's so many of them ?
TavernAI, Text-gen (Oobabooga), KoboldAI, other
It's up to you, every UI tend to add the same features as the other and try to be compatible with character from other UI as well.
(ALPIN, should we talk about the fat that Tavern don't throw the raw output of the model etc ?)

### I'm using Google Colab, how much quota I have ?
The amount of time you can use when using a free access to Google Colab highly depend of the traffic and your usage patterns.
Google say that you can use a Colab Notebook for at most 12 hours if you don't have Compute Unit. Pygmalion users tend to say it's less.

#### How to avoid running out of quota ?
First, when you use a Colab Notebook, use it. Running a Notebook and doing something beside is not really worth it. But the most common mistake made by user is to forget to PROPERLY closed stop their Runtime. Closing the Colab's tab is not enough, and can consume your Quota, or worse your Compute Unit if you have some.
For that, when you STOP using the AI, you should close your session like this :
![Shutdown](https://user-images.githubusercontent.com/127881989/225102379-b863a77e-b8e2-41aa-a0bd-b3dcf22775e2.png)



#### I run out of Quota, what do I do now ?
If you run out of quota, there's different solution. For the more patient of you, you can just wait, your account should have access to a GPU in less than a day.
If you don't want to wait, you can just switch to another google account that don't run out of free access. With 2 or 3 Google Account you should be able to use have access to a GPU to run the notebook without problem.

#### What's a Compute Unit (CU) ? Should I buy some ?
A CU is a unit that you can buy to be sure to be granted access to a GPU, and even better one.
Pricing for Compute Engine is based on per-second usage of the machine types, persistent disks, and other resources that you select for your virtual machines.
So it's up to you.
(ALPIN, should we talk about Horde as well ?)

