---
order: 10000
icon: book
---

# Colab Notebooks

!!!danger Google has banned PygmalionAI from Colab
Google has effectively banned all mentions of `PygmalionAI` in their Colabs. As a result of this, Kobold and Tavern's official Colabs will no longer work. Oobabooga's Text Generation WebUI still works, so we'll have a guide for that included here.
!!!

Running Pygmalion - or any large language model - requires a significant amount of VRAM. The current absolute minimum requirement is 10GB for a comfortable experience. Anything lower, and you would either be unable to use the model, or generations will be too slow to be enjoyable. 

Google has generously offered free GPUs for in their [Colaboratory](https://colab.research.google.com). The Colab's free plan offers an NVIDIA T4 GPU (16 GB of VRAM), which is more than enough to run Pygmalion-6B. A [TPU v2-8](https://en.wikipedia.org/wiki/Tensor_Processing_Unit) is also available in the free plan, but availibility is low due to high demand.

### Notebooks

=== oobabooga (TextGen)
:desktop_computer:/:iphone: [Click here.](http://127.0.0.1:5005/google-colab/oobabooga) 

===

!!!danger Terminate your session!
When you're done using Pygmalion, please terminate your Colab session! You'll waste your quota otherwise, and might find yourself unable to connect to a GPU backend the next time you login.
![](/static/cloud1.png)
![](/static/cloud2.png)
!!!