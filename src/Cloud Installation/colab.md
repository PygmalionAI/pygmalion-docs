---
order: 10000
icon: book
---

# Colab Notebooks

!!!danger Google has banned PygmalionAI from Colab
Google has effectively banned all mentions of `PygmalionAI` in their Colabs. As a result of this, Kobold and Tavern's official Colabs will no longer work. Oobabooga's Text Generation WebUI still works, so we'll have a guide for that included here.
!!!

Running Pygmalion - or any large language model - requires a significant amount of VRAM. The current absolute minimum requirement is 10GB for a comfortable experience. Anything lower, and you would either be unable to use the model, or generations will be too slow to be enjoyable. 

Google has generously offered free GPUs for in their [Colaboratory](https://colab.research.google.com). The Colab's free plan offers an NVIDIA T4 GPU (16 GB of VRAM), which is more than enough to run Pygmalion-6B. A [TPU v2-8](https://en.wikipedia.org/wiki/Tensor_Processing_Unit) is also available in the free plan, but availibility is low due to high demand.

## Notebooks

### Oobabooga's Text Generation WebUI
![](/static/ooba-cloud1.PNG)

Each Colab notebook will greet you with a guide. For the sake of simplicity, visual guides will be included below. You can find the notebook [here](https://colab.research.google.com/github/oobabooga/AI-Notebooks/blob/main/Colab-TextGen-GPU.ipynb){target="_blank"}.

- Make sure you're signed in to your Google Account before you attempt running any of the notebooks.
- If you're on mobile, run this cell and keep the audio file playing:
![](/static/ooba-cloud.PNG)
!!!
You might be warned that the notebook is not authored by Google - you can ignore it and click on `Run anyway`.
!!!
- Run the second cell, and make sure the `save_logs_to_google_drive` option is checked. If you don't check this, your characters and chatlogs won't persist across sessions on the same account:
![](/static/ooba-cloud2.PNG)
- You'll be prompted to give the notebook access to your Google Drive files. Click on `Connect to Google Drive`. This will open a pop-up browser window where you'll give Colab access to your Google Account. **Select the account you wish to use, then scroll down and click on "Allow"**.
- Wait for the cell to finish running. You can find out whether it's finished by checking if the cell button is still spinning:
![](/static/ooba-cloud3.PNG)
- Scroll down to the third cell and finally run Pygmalion:
![](/static/ooba-cloud4.PNG)
!!!info What do these options mean?
- `model`: Use this option to select which version of the Pygmalion model you want - `original` is the first version of the model, `main` is the current stable release (v3), `dev` is the latest beta release.
- `text_streaming`: The generated text by the bot is displayed in real-time instead of waiting for the whole message to finish generating before showing it to you. 
- `cai_chat`: Will mimic the appearance of [Character.AI](https://beta.character.ai)'s user interface.
- `load_in_8bit`: Pygmalion 6B's weights are normally stored in 16-bit floating point precision. However, this option will load them in 8-bit integer precision instead, cutting down on the computational power required to run the model. Use this so you can increase context size to the maximum.
- `activate_silero_text_to_speech`: Use this option if you want TTS for your bots.
- `activate_sending_pictures`: Allows you to send pictures to your bots.
- `activate_character_bias`: Lets you add a snippet of text that'll be put before every reply your bot generates - but keeps it hidden from you. In simple terms, if you add `*yells*` in the character bias section, your character will yell every line.
- `chat_language`: Pygmalion is a primarily English-only model - this feature simply runs yours and your bot's responses through a translation service.
!!!
- Wait for the cell to finish loading Pygmalion. This cell **will not** stop running until you terminate your Colab session or manually stop it.
- Wait for the checkpoint shards to be loaded. This should take a few minutes at most. 
- Once the model is loaded, you can find your URL here:
![](/static/ooba-cloud5.PNG)

!!!success You're done!
You can now start chatting with any bot you want. You can find bots in our unofficial [Discord Server](https://discord.com/invite/pygmalionai).
!!!


## Usage Warning
!!!danger Terminate your session!
When you're done using Pygmalion, please terminate your Colab session! You'll waste your quota otherwise, and might find yourself unable to connect to a GPU backend the next time you login.
![](/static/cloud1.png)
![](/static/cloud2.png)
!!!