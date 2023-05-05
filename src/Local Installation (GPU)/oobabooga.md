---
order: 100
icon: note
title: TextGen WebUI
---

Oobabooga's Text Generation WebUI is a gradio frontend for running large language models. 

Unlike KoboldAI, it can be used as a standalone front-end - you can still connect to SillyTavern though.

![](/static/ooba-cloud1.PNG)


## Automatic Installation
Please make sure you've read the [Overview](https://docs.alpindale.dev/pygmalion-docs/local-installation-(gpu)/overview/) and [Setting up your GPU](https://docs.alpindale.dev/pygmalion-docs/local-installation-(gpu)/gpu/) pages first. 

### Windows

Oobabooga has generously created a one-click installation script for Text-Gen WebUI. You can download it here:

[!file Text-Gen WebUI Windows Installer](https://github.com/oobabooga/one-click-installers/archive/refs/heads/oobabooga-windows.zip)

Simply extract the `oobabooga-windows.zip` file and click on the`start_windows.bat` file. This will install everything you need.

For GPUs with low VRAM, you will need to use either 8bit or 4bit mode. For 4bit, refer to [KoboldAI 4bit](https://docs.alpindale.dev/local-installation-(gpu)/koboldai4bit/) guide to obtain the model. Place the model inside oobabooga's `models` folder, and rename the large file inside your model folder to `4bit-128g.safetensors` (this will vary between different quantization techniques).

To enable **8-bit mode**, open the `webui.py` file with a text editor (notepad will work fine), and search for: `# put your flags here!`. The line will look like this:
```py
def run_model():
    os.chdir("text-generation-webui")
    run_cmd("python server.py --chat --model-menu", environment=True)  # put your flags here!
```
Change that to this:
```py
def run_model():
    os.chdir("text-generation-webui")
    run_cmd("python server.py --chat --load-in-8bit --auto-devices --xformers --api", environment=True)  # put your flags here!
```

To enable **4-bit mode**, change that line to:
```py
def run_model():
    os.chdir("text-generation-webui")
    run_cmd("python server.py --chat --wbits 4 --groupsize 128 --model_type llama --api", environment=True)  # put your flags here!
```
> Change the `groupsize` value and the `--model_type` according to the model you're loading.

If you want to, you can connect Oobabooga to [SillyTavern](https://docs.alpindale.dev/pygmalion-extras/sillytavern/).


### Linux

Oobabooga has created a one-click installer for Linux as well. Simply download the `.zip` file below, open a terminal instance in the extracted directory and run `chmod +x install.sh` and then `./install.sh`.

[!file Text-Gen WebUI Linux Installer](https://github.com/oobabooga/one-click-installers/archive/refs/heads/oobabooga-linux.zip)

If you want to, you can connect Oobabooga to [SillyTavern](https://docs.alpindale.dev/pygmalion-extras/sillytavern/).

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

You can view the full list of commands [here](https://github.com/oobabooga/text-generation-webui#starting-the-web-ui){target="_blank"}.

If you want to, you can connect Oobabooga to [SillyTavern](https://docs.alpindale.dev/pygmalion-extras/sillytavern/).