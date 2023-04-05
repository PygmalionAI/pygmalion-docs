---
order: 1000000
icon: telescope
title: Overview
---

PygmalionAI is a Large Language Model, and as the name might imply, it needs a lot of computation power to run it. You need a minimum of 16GB VRAM to run the model -- without any optimizations, that is. Here's a list of all the GPUs that would work without any tweaks and out-of-the-box:

**Consumer-grade (Gaming) GPUs:**

GPU                 | Manufacturer      | VRAM { class="compact" }
---                 | ---               | ---
RTX 4090            | NVIDIA            | 24GB
RTX 4080            | NVIDIA            | 16GB
RTX 3090 Ti         | NVIDIA            | 24GB
RTX 3090            | NVIDIA            | 24GB
Titan RTX           | NVIDIA            | 24GB
Radeon RX 7900 XTX  | AMD               | 24GB
Radeon RX 6950 XT   | AMD               | 16GB
Radeon RX 6900 XT   | AMD               | 16GB
Radeon RX 7900 XT   | AMD               | 20GB
Radeon RX 6800 XT   | AMD               | 16GB
Radeon RX 6800      | AMD               | 16GB


!!!warning You card isn't listed here?
If you don't have any of these cards, but still have over 8GB of VRAM, chances are you can run the model just fine. You just have to make sure your card supports CUDA (NVIDIA) or ROCm (AMD). We'll get to that later.
!!!


Please continue to the GPU set-up section.
[!ref Setting up your GPU](http://127.0.0.1:5005/local-installation/gpu/)

