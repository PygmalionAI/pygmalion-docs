---
order: 1000
icon: note
title: KoboldAI 4bit
---

KoboldAI is a browser-based front-end for AI-assisted writing and chatting with multiple local and remote AI models. 

This guide is for users with less than 10GB of VRAM. Pygmalion 6B with 4bit quantization can run on GPUs with 6GB of VRAM and above.

Use the Table of Contents to navigate.

![](/static/KoboldAI-newui.PNG)

## Requirements

Please make sure you :

- Have read the [Overview](https://docs.alpindale.dev/local-installation-(gpu)/overview/#overview) and Setting up your GPU pages first. 
- Have Git installed, tutorial [here](https://docs.alpindale.dev/tools/git/#whats-git-and-do-i-need-it).
- Don't have a `B:` Drive (Windows only)



## Installation

### Windows

The Windows Guide was written with the help of Peepy (lunarlemon#4643).

#### Installing 0cc4m's KoboldAI fork

This fork require a manual installation, you can easily do it by following the instructions below.

First create a folder where you want it to be.

Go inside that folder and open a PowerShell by holding down the Shift key while right-clicking. From the context menu, select the option to `Open PowerShell Window here`.

![](/static/OpenPSWindows.PNG)




Now that you have opened PowerShell, you need to run a few commands. (Copy paste the command and press enter).

First you want to clone the Kobold-4bit repository: `git clone https://github.com/0cc4m/KoboldAI -b latestgptq --recurse-submodules`

It shouldn't take more than a few seconds to clone it.

Once it's done, run : `cd KoboldAI`. This will take you to the KoboldAI directory you just downloaded.

This is how your PowerShell look like so far:

![](/static/KoboldAI-4bit-1.PNG)


You can now close this PowerShell.



Go into your KoboldAI folder and search for the `install_requirements.bat` file. Make a right click on it and choose `Run as administrator`.

When running the `install_requirements.bat` command, it will first ask you which way you want to install it. The choice is up to you but we recommend the `1. Temporary Drive Letter` (Press 1 and enter).


![](/static/KoboldAI-4bit-2.PNG)


After that, The command prompt will take a few minutes to install all the Kobold requirements and create a umamba virtual environment. This environment will keep all the dependencies safely secured in one folder to prevent conflicts with external packages.

When the end of the prompt look like this, you can press any key to close it.

![](/static/KoboldAI-4bit-5.PNG)


Now, go back into your Kobold folder again, and open the `play.bat` file.



![](/static/KoboldAI-4bit-6.PNG)

It should open a tab on your browser with this url `http://localhost:5000`

However, you want to change it to : `http://localhost:5000/new_ui`

Once in the new UI, go to the "Interface" tab and turn on `Experimental UI` option.

![](/static/KoboldAI-4bit-7.PNG)

This is what allows for 4bit (or on Linux, also 8bit!)

After you've done that, congrats! You're almost there. You need to download the model now.


#### Downloading the model

In your Kobold folder, navigate to the `models` folder. 

![](/static/KoboldAI-4bit-8.PNG)

Open PowerShell inside the folder and download the model with [git](https://docs.alpindale.dev/tools/git):
```bash
git clone https://huggingface.co/OccamRazor/pygmalion-6b-gptq-4bit
```

The model should be downloaded in your `models` folder.

!!!warning Rename your model file if you download from another repo!
The current GPTQ implementation on Kobold needs your model name to be either `4bit.pt`/`4bit.safetensors` or `4bit-128g.pt`/`4bit-128g.safetensors`. Please rename them appropriately:
![](/static/KoboldAI-4bit-9.PNG)
!!!


!!!info
At that point, all the installation part is done.
!!!

#### Loading the model

On the Kobold URL `http://localhost:5000/new_ui`, click on the `home` tab, then on `Load Model`

![](/static/KoboldAI-4bit-10.PNG)

On the list, pick the `Load a model from it's directory` option.

![](/static/KoboldAI-4bit-11.PNG)

Pick the model we just downloaded, ***MAKE SURE THE 4 BIT MODE IS ON***, then click on load !

![](/static/KoboldAI-4bit-12.PNG)

!!!success
The model will now be loaded and be ready to be use, if you want to use it with SillyTavern, please go [here](https://docs.alpindale.dev/local-installation-(gpu)/sillytavern/#connect-sillytavern).
!!!


### Linux

With Linux, you should be able to get both 8bit and 4bit support using Occam's fork. For 8bit, you will need the [original model](https://huggingface.co/PygmalionAI/pygmalion-6b). For 4-bit, you can download any of the GPTQ quantized models.

#### Requirements
- `git`
- `python==3.10.9`
- `aria2`
- `cmake`
- `make`
- `gcc`

#### Installation

1. Clone Occam's fork of KoboldAI
```bash
git clone https://github.com/0cc4m/KoboldAI -b latestgptq --recurse-submodules && cd KoboldAI
```

2. Install the Kobold requirements
```bash
chmod +x install_requirements.sh \
./install_requirements.sh
```
!!!info
This is a 2.5GB download.
!!!

3. Download the 4bit Pygmalion model from [here](https://huggingface.co/OccamRazor/pygmalion-6b-gptq-4bit) and place all the files inside Kobold's `models` folder. Create a separate folder for the model first.
!!!danger Rename the model if you download from another repo!
The model needs to be named either `4bit.pt`/`4bit.safetensors` or `4bit-128g.pt`/`4bit-128g.safetensors` to work. Make sure you properly rename it. 
!!!
4. Start KoboldAI by running `./play.sh`.

5. Navigate to the NewUI (you can simply add `new_ui` at the end of the URL) and activate the Experimental UI.
![](/static/KoboldAI-4bit-7.PNG)

6. Click on `Load Model` on the left-side menu and choose the following option: 
![](/static/KoboldAI-4bit-10.PNG)

7. On the list, pick the `Load a model from it's directory` option.

![](/static/KoboldAI-4bit-11.PNG)

8. Pick the model we just downloaded, ***MAKE SURE THE 4 BIT MODE IS ON***, then click on load !

![](/static/KoboldAI-4bit-12.PNG)

!!!success Enjoy!
You can now run Pygmalion 6B on your low VRAM GPU. Rejoice.
!!!






