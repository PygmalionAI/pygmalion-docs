---
order: 1000
icon: ":desktop_computer:"
title: Soft Prompts
---

## What's a Soft Prompts (SP) and do I need them?
In this case, a soft prompt is a file that gonna modify the style and behavior of a model. It can suggests the tone, fictional universe, or the style of an author you're looking for and the model can then use this information to generate an output that fits your request.
Even if they can help the model to internalize some lore, facts or information, they shouldn't be used for this, the model could mixed up things or be unable to extract the right information.



## How to use them?

### KoboladAI

#### Downloading and placing the SP

First, download your SP of choice from either the Discord or [this Rentry](https://rentry.org/pygsoft){ target="_blank" } a generous anon is maintaining.

For using a Soft Prompt, the method is slighlty different depending on the way you are running the model.

##### Locally


To load a Soft Prompts into KoboldAI, place the `.zip` file (don't extract!) inside the `\KoboldAI\softprompts` folder.

##### Google Colab

You gonna have to check the `use_google_drive` option and granting access to your Google Drive in the pop-up.

![](/static/SP-Kobold-4.png)

Then on the left of the screen click on the folder icon. Naviguate through the files to find the `\MyDrive\KoboldAI\softprompts` folder. Drag and drop your `.zip` file (don't extract!) inside. 


![](/static/SP-Kobold-5.png)

## Loading the Soft Prompt

Once it's done, go into the Kobold UI, and click on the `Soft Prompt` tab.

!!!
For Google Colab user, you have to click on the remote URL provide by the colab to reach that UI !
!!!

![](/static/SP-Kobold-1.png)

Then select your Soft Prompt and click on the `load` button.

![](/static/SP-Kobold-2.png)

If your Soft Prompt is loaded, the light bulb should be green !

![](/static/SP-Kobold-3.png)


