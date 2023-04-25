---
order: 1000
icon: ":spiral_note_pad:"
title: Soft Prompts
---

## What are Soft Prompts (SP) and do I need them?
A soft prompt is a file that modifies the style and behavior of the language model. It can create a bias towards the tone or the style of an author or series, and the model can then use this information to generate an output that fits your purposes for a specific bot(s).
Even if they can help the model to internalize lore, facts or information, they are not suited for it. SPs *do not* re-train model and as such, no new knowledge is acquired. If you're interested in how softprompts work on a *technical* level, please refer to [this section]



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
For Google Colab user, please click on the remote URL provide by the colab to reach that UI!
!!!

![](/static/SP-Kobold-1.png)

Then select your Soft Prompt and click on the `load` button.

![](/static/SP-Kobold-2.png)

If your Soft Prompt is loaded, the light bulb should be green!

![](/static/SP-Kobold-3.png)


## How do Soft Prompts work?

Refer to [this paper](https://arxiv.org/abs/2104.08691) for a more detailed overview, and this [wiki page](https://github-wiki-see.page/m/KoboldAI/KoboldAI-Client/wiki/Soft-Prompts) for a more in-depth and human-readable explanation.

Soft prompting is an alternative to model [fine-tuning](https://huggingface.co/docs/transformers/training) that freezes the weights of a model and updates the parameters of a prompt to adapt the model to different downstream tasks. This results in a "soft prompt". 

The advantage of soft prompting is that it allows the same model to be used for mutliple tasks by appending the appropriate prompts at inference time. This makes batching across different tasks easier. Soft prompts trained for a single model across multiple tasks will often be of the same token length. The vectors of values of the tokens can be considered as model parameters, and the model can be further trained by adjusting only the weights of these prompts.

Prompt tuning performs better with larger models, and using more than 20 tokens doesn't yield significant performance gains.

**TL;DR**, Soft prompts are learnable vectors that are concatenated to the input text and optimized end-to-end over a training dataset. Mixtures of soft prompts can be used to query LMs, allowing us to learn which prompts are most effective and how to ensemble them.

## How do I create a Soft Prompt?

Creating a softprompt for a a GPT-J model needs several times the computation power it takes to inference the model. KoboldAI has a [Colab Notebook](https://colab.research.google.com/gist/henk717/281fd57ebd2e88d852ef9dcc3f29bebf/easy-softprompt-tuner.ipynb#sandboxMode=true). As of now (2023-04-22), Colab's TPUs have a driver issue and so the Easy Tuner won't work. You can instead refer to [this repo](https://github.com/exelents/soft-prompt-tuning) for GPU tuning - though you'll likely need a powerful GPU.
