---
order: 100
icon: note
title: TextGen WebUI
---

Oobabooga's Text Generation WebUI is a gradio frontend for running large language models. 

Unlike KoboldAI, it can be used as a standalone front-end - more importantly, you cannot connect Oobabooga's Text Generation WebUI to Tavern. 

![](/static/ooba-cloud1.PNG)


## Automatic Installation
Please make sure you've read the [Overview](https://alpindale.github.io/pygmalion-docs/local-installation-overview) and [Setting up your GPU](https://alpindale.github.io/pygmalion-docs/local-installation/gpu) pages first. 

### Windows

Oobabooga has generously created a one-click installation script for Text-Gen WebUI. You can download it here:

[!file Text-Gen WebUI Windows Installer](https://github.com/oobabooga/one-click-installers/archive/refs/heads/oobabooga-windows.zip)

Simply extract the `one-click-installers-oobabooga-windows.zip` file and click on `install.bat`. That will install everything for you. Once the installation is finished, open the `start-webui.bat` file.


### Linux

Oobabooga has created a one-click installer for Linux as well. Simply download the `.zip` file below, open a terminal instance in the extracted directory and run `chmod +x install.sh` and then `./install.sh`.

[!file Text-Gen WebUI Linux Installer](https://github.com/oobabooga/one-click-installers/archive/refs/heads/oobabooga-linux.zip)


## Manual Installation
You can also manually install the WebUI. This method is recommended because it's more fun. The following guide is applicable to both Windows and Linux, though the primary audience is Linux users.

#### Requirements
- python
- git
- miniconda

***
#### Installation steps
- Install miniconda:

[!file Miniconda3 Windows](https://repo.anaconda.com/miniconda/Miniconda3-latest-Windows-x86_64.exe)
[!file Miniconda 3 Linux](https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh)

!!!info
For Windows, it's simply a matter of double-clicking the downloaded `.exe` file for installation. For linux, you'll need to make it an executable by running `chmod +x Miniconda3-latest-Linux-x86_64.sh` and then running the installer script with `./Miniconda3-latest-Linux-x86_64.sh` in your terminal.
!!!

- Create a conda environment for TextGen:
```
conda create -n textgen
conda activate textgen
conda install torchvision torchaudio pytorch-cuda=11.7 git -c pytorch -c nvidia
git clone https://github.com/oobabooga/text-generation-webui
cd text-generation-webui
pip install -r requirements.txt 
```
!!!warning Are you using an AMD GPU?
If you are, replace the third command with this:
`pip3 install torch torchvision torchaudio --extra-index-url https://download.pytorch.org/whl/rocm5.2`
!!!

- Run the web server:
```
python server.py --cai-chat --auto-devices --no-stream
```
!!!info 
By default, oobabooga's TextGen will load the first model (in alphabetical order) placed in your models folder. You can specify which model to load with the `--model` argument, followed by your model name *as it's named in the `models` folder*. Here's an example of how you'd run Pygmalion-6b:

`python server.py --model PygmalionAI/pygmalion-6b --cai-chat --auto-devices --no-stream`

The `PygmalionAI/` part is for if you want to download the model first. If you already have `pygmalion-6b` downloaded in your models folder, then simply do `--model pygmalion-6b`.
!!!
!!!warning Do you have less than 16GB VRAM?
Please don't forget to pass the `--load-in-8bit` argument too if you have a low VRAM PC! `--auto-devices` should take care of the memory assignment if you have less 10GB VRAM.
!!!

You can view the full list of commands [here](https://github.com/oobabooga/text-generation-webui#starting-the-web-ui){target="_blank"}