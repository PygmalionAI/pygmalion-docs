---
order: 1000
icon: ":spiral_note_pad:"
title: Soft Prompts
---

## What are Soft Prompts (SP) and do I need them?
A soft prompt is a file that modifies the style and behavior of the language model. It can create a bias towards the tone or the style of an author or series, and the model can then use this information to generate an output that fits your purposes for a specific bot(s).
Even if they can help the model to internalize lore, facts or information, they are not suited for it. SPs *do not* re-train model and as such, no new knowledge is acquired.



## Using Soft Prompts

### KoboldAI

#### Downloading and placing the SP

First, download your SP of choice from either the Discord or [this rentry](https://rentry.org/pygsoft){ target="_blank" } a generous anon is maintaining.

For using a Soft Prompt, the method is slighlty different depending on the way you are running the model.

##### Locally


If you're running KoboldAI locally on your PC (not using Google Colab), place the `.zip` file (don't extract!) inside the `\KoboldAI\softprompts` folder.

##### Google Colab

Make sure to check the `use_google_drive` option and granting access to your Google Drive in the pop-up.

![](/static/SP-Kobold-4.png)

Then on the left of the screen click on the folder icon. Navigate through the files to find the `\MyDrive\KoboldAI\softprompts` folder. Drag and drop your `.zip` file (don't extract!) inside. 

![](/static/SP-Kobold-5.png)


## Loading the Soft Prompt

Once it's done, go into the Kobold UI, make sure the model is loaded (this is done automatically on Colab), and click on the `Soft Prompt` tab.

!!!
For Google Colab user, you have to click on the remote URL provide by the colab to reach that UI !
!!!

![](/static/SP-Kobold-1.png)

Then select your Soft Prompt and click on the `load` button.

![](/static/SP-Kobold-2.png)

If your Soft Prompt is loaded, the light bulb should be green !

![](/static/SP-Kobold-3.png)


