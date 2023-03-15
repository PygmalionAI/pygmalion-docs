---
order: 100000
icon: gear
title: Setting up your GPU
---

Consumer-grade GPUs are designed for Video Processing and 3D rendering - they're not *specifically* made for Language Processing models. However, GPU vendors such as NVIDIA and AMD have released toolkits for enabling computation for their GPUs. Only a handful of AMD GPUs are supposed, but the majority of NVIDIA cards can be setup easily. 

!!!info
Keep in mind that the most important factor for AI is VRAM (Video Memory), not the processing power. e.g. an RTX 2070 (8GB) is better than an RTX 4050 (6GB) when it comes to AI inference.
!!!
Please refer to the links below to check if your GPU is compatible:

[!button icon="/static/icons/nvidia.svg" text="NVIDIA" target="blank"](https://developer.nvidia.com/cuda-gpus) - 
[!button icon="/static/icons/amd.svg"text="AMD" target="blank"](https://github.com/ROCm/ROCm.github.io/blob/master/hardware.md)

If your GPU is supported, please proceed with the installation.

## NVIDIA

NVIDIA Cards are mostly supported - though it's not recommended to use GPUs with less than 8GB of VRAM. 

The setup process will be different for both Windows and Linux (MacOS currently not supported). 

### Windows
The official [Game-Ready Drivers](https://www.nvidia.com/en-us/geforce/drivers/) provided by NVIDIA will setup CUDA for you, and that's all you need to do!

### Linux
CUDA installation is relatively easy for Linux (unless you're on Fedora). For this particular guide, we'll be covering three base distros - [Arch Linux](https://www.archlinux.org) and [Debian](https://www.debian.org/). More will be added later.

#### Arch Linux
- Install the NVIDIA drivers (if they aren't already installed):
```
pacman -S nvidia
```
!!!warning Are you using the LTS kernel?
If you're on the LTS Arch Linux Kernel, then please install `nvidia-lts` instead. You can find what Kernel you're using by running `uname -r`
!!!
- Install CUDA and (optionally) cuDNN:
```
pacman -S cuda cudnn
```
- You're done! Verify installation by running `nvcc -v`.

#### Debian
- Install the NVIDIA drivers (if they aren't already installed):
```
apt update && apt install nvidia-driver-525
```
- Install CUDA:
```
apt install nvidia-cuda-toolkit
```
- You're done! Verify installation by running `nvcc -v`.


## AMD

ROCm is (currently) not supported by Windows. You cannot run any language model on Windows if you have an AMD card - this isn't a Pygmalion-only issue. You will need to either dual-boot Linux or switch to Linux entirely if you wish to run language models on your AMD GPU.

### Linux
The ROCm installation is only (relatively) easy on Arch Linux. For other distros, you need to manually install the binaries by building ROCm from source (not recommended for beginners). 

Installing Arch Linux is not easy for a beginner, therefore look into [Manjaro](https://manjaro.org) or [EndeavourOS](https://endeavouros.com) - they both use an Arch Linux base.

#### Arch Linux
- Install GPU drivers by following [the official guide](https://wiki.archlinux.org/title/AMDGPU).
- Install an AUR Helper. We'll use [paru](https://aur.archlinux.org/packages/paru) for this guide:
```
sudo pacman -S git
git clone https://aur.archlinux.org/paru.git && cd paru
makepkg -si
```
- Install ROCm:
```
paru -S rocm-hip-sdk rocm-opencl-sdk
```

#### Not using Arch Linux?
AMD has a comprehensive guide for installing ROCm. Please refere to their guide on the installation.

[!button icon="/static/icons/amd.svg" target="blank" text="ROCm Install Guide"](https://docs.amd.com/bundle/ROCm-Getting-Started-Guide-v5.3/page/How_to_Install_ROCm.html)


