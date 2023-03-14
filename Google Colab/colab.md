---
order: 100
icon: book
---

# Colab Notebooks

Running Pygmalion - or any Large Language Model - requires a significant amount of VRAM. The current absolute minimum requirement is 10GB for a comfortable experience. Anything lower, and you would either be unable to use the model, or generations will be too slow to be enjoyable. 

Google has generously offered free GPUs for in their [Colaboratory](https://colab.research.google.com). The Colab's free plan offers an NVIDIA T4 (16GB) GPU, which is more than enough to run the 6B Pygmalion Model. A [TPU v2-8](https://en.wikipedia.org/wiki/Tensor_Processing_Unit) is also available in the free plan, but availibility is low due to high demand.

### Notebooks

There are currently two backends to run the Pygmalion 6B model - [KoboldAI](https://github.com/henk717/KoboldAI) and [Text-Generation-WebUI](https://github.com/oobabooga/text-generation-webui) by oobabooga.

[TavernAI](https://github.com/TavernAI/TavernAI) is a frontend that connects to KoboldAI and essentially facilitates a connection to Pygmalion via Kobold while offering a pleasant looking User Interface. **TavernAI by itself doesn't run Pygmalion - therefore you do not need a powerful PC to run TavernAI.** You cannot use TavernAI with oobabooga's Text-Gen-WebUI.

!!!
If you're on Mobile, use either oobabooga's TextGen or TavernAI.
!!!

+++ KoboldAI
[Click here.](https://colab.research.google.com/github/koboldai/KoboldAI-Client/blob/main/colab/GPU.ipynb)
+++ oobabooga (TextGen)
[Click here.](https://colab.research.google.com/github/oobabooga/AI-Notebooks/blob/main/Colab-TextGen-GPU.ipynb)
+++ TavernAI
[Click here.](https://colab.research.google.com/github/TavernAI/TavernAI/blob/main/colab/GPU.ipynb)


