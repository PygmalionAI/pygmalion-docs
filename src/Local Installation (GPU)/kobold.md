---
order: 1000
icon: note
title: KoboldAI
---

KoboldAI is a browser-based front-end for AI-assisted writing and chatting with multiple local and remote AI models. 

KoboldAI also supports PygmalionAI - although most primarily use it to load Pygmalion, and then connect Kobold to Tavern. You can still use Kobold in its New UI with Chat mode. 

![](/static/KoboldAI-newui.PNG)

## Installation

Please make sure you've read the Overview and Setting up your GPU pages first. 

### Windows

- Make sure you don't have a `B:` Drive.
- Download KoboldAI and run the `.exe` file:

[!file KoboldAI](https://koboldai.org/windows)
- When you reach this part, type `2` and press enter.
![](/static/kobold-local-3.png)
- Search for KoboldAI in the Start Menu and launch it.
!!!warning
Don't launch KoboldAI as Administrator!
!!!

### Linux

##### Requirements
- `git`

##### Installation
- Clone the repo:
```
git clone https://github.com/henk717/KoboldAI && cd KoboldAI
```
- Launch KoboldAI
```
./play.sh       # for NVIDIA
./play-rocm.sh  # for AMD
```

## Using KoboldAI

Once you've launched KoboldAI, click on `AI` on the top-left corner of the screen, then click on `Chat Models` and select `PygmalionAI/pygmalion-6b`. You can then click on `Load`.

![](/static/kobold-local.png)

!!!danger Is your VRAM less than 16GB?
Loading 28/28 layers on GPU needs around 16GB VRAM. You can assign fewer layers based on how much VRAM your GPU has access to. **Do not put any layers on Disk!**
!!!
