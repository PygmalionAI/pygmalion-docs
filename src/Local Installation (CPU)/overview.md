---
order: 1000000
icon: telescope
title: Overview
---

Due to recent strides in the AI field, it is now possible to run Large Language Models entirely on CPU with surprisingly decent speeds. One such library is [GGML](https://github.com/ggerganov/ggml). This makes it possible to run Pygmalion 6B even on mobile phones! (Provided you have at least 8GB of RAM.) In this section, you'll find guides for CPU inferencing, applicable to both PCs (irregardless of your Operating System) and Mobile Phones (Android only for now).

The system requirement for Pygmalion C++ is about 4-6GB of RAM. This isn't VRAM, and you don't even need to have a GPU at all!

!!!warning Inference speed
Pygmalion C++ will take a few minutes to process your input tokens when you first load a character. This is normal and won't be repeated every time you type in a prompt for your bot.
!!!

Please continue to the next section.