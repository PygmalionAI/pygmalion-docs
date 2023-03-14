---
order: 100
icon: cloud
title: Oobabooga
---

# Text Generation WebUI

Each Colab notebook will greet you with a guide. For the sake of simplicity, visual guides will be included below. You can find the notebook [here](https://colab.research.google.com/github/koboldai/KoboldAI-Client/blob/main/colab/GPU.ipynb). **Middle click** or right-click and open in a new tab if you want to follow along with this guide!

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
- `text_streaming`: The generated text by the bot is displayed in real-time instead of waiting for the whole message to finish generating before showing it to you. 
- `cai_chat`: Will mimic the appearance of [Character.AI](beta.character.ai)'s user interface.
- `load_in_8bit`: Pygmalion 6B's weights are in Floating Point 16 bits, this will load them in Integer 8 bits instead - which cuts down on the computation power required. Use this so you can increase context size to the maximum.
- `activate_silero_text_to_speech`: Use this option if you want TTS for your bots.
- `activate_sending_pictures`: No idea
- `activate_character_bias`: No idea
- `chat_language`: Pygmalion is a primarily English-only model - this feature simply runs yours and your bot's responses through a translation service.
!!!