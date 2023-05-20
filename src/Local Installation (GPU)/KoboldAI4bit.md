---
order: 1000
icon: note
title: KoboldAI 4bit
---

KoboldAI is a browser-based front-end for AI-assisted writing and chatting with multiple local and remote AI models. 

This guide is for users with less than 10GB of VRAM. Pygmalion 6B and 7B with 4bit quantization can run on GPUs with 6GB of VRAM and above.

Use the Table of Contents to navigate.

![](/static/KoboldAI-newui.PNG)

## Requirements

Please make sure you :

- Have read the [Overview](https://docs.alpindale.dev/local-installation-(gpu)/overview/#overview) and Setting up your GPU pages first. 
- Have Git installed, tutorial [here](https://docs.alpindale.dev/tools/git/#whats-git-and-do-i-need-it).
- Don't have a `B:` Drive (Windows only)



## Installation

### Windows

Download the Kobold **exe**cutable file from here:

[!button KoboldAI](https://github.com/henk717/KoboldAI/releases)

Run the .exe file and follow the instructions until you have an installed copy of KoboldAI. But you're not done yet!

Download this file and place it inside the newly installed KoboldAI folder:

[!button 4bit Patch](https://cdn.discordapp.com/attachments/1067465338905702572/1105952533421228032/update-koboldai-occam-4bit.bat)

Once in the KoboldAI folder, you may simply double-click on the `update-koboldai-occam-4bit.bat` file and it'll patch your KoboldAI installation to support 4bit!

<!-- The Windows Guide was written with the help of Peepy (lunarlemon#4643).

#### Installing 0cc4m's KoboldAI fork

This fork require a manual installation, you can easily do it by following the instructions below.

First create a folder where you want it to be.

Go inside that folder and open a PowerShell by holding down the Shift key while right-clicking. From the context menu, select the option to `Open PowerShell Window here`.

![](/static/OpenPSWindows.PNG)




Now that you have opened PowerShell, you need to run a few commands. (Copy paste the command and press enter).

First you want to clone the Kobold-4bit repository: 
```bash
git clone https://github.com/0cc4m/KoboldAI -b latestgptq --recurse-submodules
``` 
!!!warning
Make sure you've read the [git installation guide](https://docs.alpindale.dev/tools/git/).
!!!

It shouldn't take more than a few seconds to clone it.

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

This is what allows for 4bit (or on Linux, also 8bit!) -->

After you've done that, congrats! You're almost there. You need to download the model now.


#### Downloading the model

In your Kobold folder, navigate to the `models` folder. 

![](/static/KoboldAI-4bit-8.PNG)

Right click on the models folder and select "Open in Terminal". You may download a model now using [git](https://docs.alpindale.dev/tools/git) clone commands.
There are two models to choose from. If you run
```bash
git lfs clone https://huggingface.co/OccamRazor/pygmalion-6b-gptq-4bit
```
it will download the main Pygmalion version, V3.

As an alternative, Pygmalion Version 8 Part 4 is also available for download. In comparison to V3, V8 was fine tuned on a larger dataset which according to user feedback improved coherency and general knowledge of the model at the cost of being a little less inclined to engage in NSFW roleplay. To download it, run
```bash
git lfs clone https://huggingface.co/mayaeary/pygmalion-6b_dev-4bit-128g
```
instead.

Your preferred model should be downloaded in your `models` folder. The following steps are identical no matter which model you've downloaded.

!!!warning Rename your model file!
The current GPTQ implementation on Kobold needs your model name to be either `4bit.pt`/`4bit.safetensors` or `4bit-128g.pt`/`4bit-128g.safetensors`. **This is the file, and not the folder itself! Look for the ~4GB file inside the folder you've downloaded!** Please rename them appropriately:
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
The model will now be loaded and be ready to be use, if you want to use it with SillyTavern or Agnaistic, please go [here](https://docs.alpindale.dev/pygmalion-extras/sillytavern/#connect-sillytavern),  or the [Agnaistic Guide](https://docs.alpindale.dev/pygmalion-extras/agnaistic/) here.
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
./install_requirements.sh cuda
```
!!!info
This is a 2.5GB download.
!!!

3. Navigate to your Kobold folder and right click on the models folder. Choose Actions -> Open Terminal Here. As the steps for downloading a model are the same for Windows, you may refer to this part of the guide: [Downloading the model](https://docs.alpindale.dev/local-installation-(gpu)/koboldai4bit/#downloading-the-model).

!!!danger Rename the model file!
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
You can now run Pygmalion 6B on your low VRAM GPU. Rejoice. Pygmalion 7B will require the same process, so you shouldn't have any trouble.
!!!






