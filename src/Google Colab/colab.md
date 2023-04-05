---
order: 10000
icon: book
---

# Colab Notebooks

Running Pygmalion - or any large language model - requires a significant amount of VRAM. The current absolute minimum requirement is 10GB for a comfortable experience. Anything lower, and you would either be unable to use the model, or generations will be too slow to be enjoyable. 

Google has generously offered free GPUs for in their [Colaboratory](https://colab.research.google.com). The Colab's free plan offers an NVIDIA T4 GPU (16 GB of VRAM), which is more than enough to run Pygmalion-6B. A [TPU v2-8](https://en.wikipedia.org/wiki/Tensor_Processing_Unit) is also available in the free plan, but availibility is low due to high demand.

### Notebooks

There are currently two backends to run the Pygmalion 6B model - [KoboldAI](https://github.com/henk717/KoboldAI) and [Text-Generation-WebUI](https://github.com/oobabooga/text-generation-webui) by oobabooga.

[TavernAI](https://github.com/TavernAI/TavernAI) is a frontend that connects to KoboldAI and essentially facilitates a connection to Pygmalion via Kobold while offering a pleasant looking User Interface. **TavernAI by itself doesn't run Pygmalion - therefore you do not need a powerful PC to run TavernAI.** You cannot use TavernAI with oobabooga's Text-Gen-WebUI.

!!!
If you're on Mobile, use either oobabooga's TextGen or TavernAI.
!!!

=== KoboldAI
:desktop_computer: [Click here.](http://127.0.0.1:5005/google-colab/kobold)
=== oobabooga (TextGen)
:desktop_computer:/:iphone: [Click here.](http://127.0.0.1:5005/google-colab/oobabooga) 
=== TavernAI
:desktop_computer:/:iphone: [Click here.](http://127.0.0.1:5005/google-colab/tavern) 
===

!!!danger Terminate your session!
When you're done using Pygmalion, please terminate your Colab session! You'll waste your quota otherwise, and might find yourself unable to connect to a GPU backend the next time you login.
![](/static/cloud1.png)
![](/static/cloud2.png)
!!!