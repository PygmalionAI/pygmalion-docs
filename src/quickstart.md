---
order: 10000
icon: rocket
title: Quickstart
---

![](/static/quickstart.png)


There are multiple ways to run a large language model like Pygmalion, including using cloud computing instances or locally installed software. For users who want to run the model locally, it's important to ensure that their computer meets the minimum requirements, including having a GPU with enough memory. Outlined below are instructions for Windows Users to find out which criteria they meet so they can quickly get started.

## Windows

### Identifying your GPU

Find out what GPU you're using (if any at all) by performing the following steps:

1. Press the `Windows Key` + `R`. This will open the `Run` window.
2. Type in `dxdiag` and press enter.
![](/static/quick1.jpg)
!!! 
You might be greeted with a dialogue box if it's the first time launcing `dxdiag`. You can pick whatever option you want, it doesn't matter.
!!!
3. Look for the `Display` tab on the top side of the window. Depending on your PC/Laptop, there might be two Display tabs - aptly named "Display 1" and "Display 2". In that case, click on "Display 2" instead.
4. Look for the `Display Memory (VRAM) part of the screen.
![](/static/quick2.jpg)
5. Proceed to the [next section](https://docs.alpindale.dev/quickstart/#what-to-do-now)
!!!danger Are you using an AMD GPU?
Unfortunately, the framework required to enable compute on AMD GPUs (ROCm) is currently unavailable on Windows. While we wait for AMD to add ROCm support to Windows, you will either have to switch to Linux or use the Cloud/C++ solutions.
!!!

## Linux

### Identifying your GPU
Use the following command to find out whether you have a discrete GPU or not:
```bash
lspci -k | grep -A 2 -E "(VGA|3D)"
```
If you have a dedicated GPU, you should see something like this; an NVIDIA card with the Kernel drive in use being `nvidia`:
![](/static/quick3.png)

In that case, run `nvidia-smi` to view your VRAM amount. Then continue to the [next section](https://docs.alpindale.dev/quickstart/#what-to-do-now). If the kernel driver in use is not `nvidia` or `nvidia-lts`, you will need to install the nvidia drivers for your distro. 

If you don't have a discrete GPU, you would see something like this:
![](/static/quick4.png)
In that case, proceed to [this section](https://docs.alpindale.dev/quickstart/#i-have-no-vram)





## What to do now?

There are several options, depending on how much VRAM your system had. Outlined below are the multiple scenarios and the recommended method of running Pygmalion for each. Please use the Table of Contents for navigating.

### I have no VRAM!
In this case, your only choice is to whether run on the Cloud or use Pygmalion C++ to run the model on your CPU.

##### Cloud
There are several options for running on the cloud - Google Colab and GPU rental services.

**Google Colab** is free, but there are restrictions for the end user. Namely: daily/weekly usage quotas and a less powerful GPU. If you want to take this route, please refer to either the [TextGen WebUI](https://docs.alpindale.dev/cloud-installation/colab) for running Pygmalion itself or [KoboldAI Notebooks](https://docs.alpindale.dev/cloud-installation/koboldai) for the various Mixed Models. 

**GPU Rental services**, such as [vast.ai](https://docs.alpindale.dev/cloud-installation/vast) are another option. They're paid services, but with the added benefits of powerful GPUs, virtually no quotas (since you pay hourly and on-the-go), and next to no restrictions on your usage. The included guide for vast.ai in these docs provide a docker image for KoboldAI which will make running Pygmalion very simple for the average user.

##### Pygmalion C++
If you have a decent CPU, you can run Pygmalion with no GPU required, using the GGML framework for Machine Learning. Please refer to [the guide](https://docs.alpindale.dev/local-installation-(cpu)/pygcpp) for instructions on how to proceed.

### I have less than 4GB!
In that case, please refer to the section above for Cloud and C++ options.

### I have 6GB or more but less than 10GB!

Please refer to the [4-bit guide](https://docs.alpindale.dev/local-installation-(gpu)/koboldai4bit). Alternatively, you can also use one of the Cloud options if you find the 4bit model undesirable.

### I have 10GB or more but less than 16GB!

Please refer to the [TextGen WebUI guide](https://docs.alpindale.dev/local-installation-(gpu)/oobabooga) to run Pygmalion at 8bit precision. Make sure you pass the `--load-in-8bit` argument when launching the WebUI. Alternatively, if you're using Linux, you can also use KoboldAI for 8-bit precision mode. Please refer to the [4-bit guide](https://docs.alpindale.dev/local-installation-(gpu)/koboldai4bit) for instructions.

### I have 16GB or more!

You have the recommended amount of VRAM for the 6B model. You may pick whatever option you want - all the guides here will work for you. You can get started [here](https://docs.alpindale.dev/local-installation-(gpu)/overview).


