---
order: 10000
icon: book
---

# Colab Notebooks

!!!danger Google has banned all PygmalionAI notebooks
Any notebook with the keyword `PygmalionAI` has a chance of banning your *Colab* account, so as of now, only Oobabooga' official notebook is functioning. And as such, I have removed the pages for other notebooks here. There are several unofficial ones that seem to work, however.


Running Pygmalion - or any Large Language Model - requires a significant amount of VRAM. The current absolute minimum requirement is 10GB for a comfortable experience. Anything lower, and you would either be unable to use the model, or generations will be too slow to be enjoyable. 

Google has generously offered free GPUs for in their [Colaboratory](https://colab.research.google.com). The Colab's free plan offers an NVIDIA T4 (16GB) GPU, which is more than enough to run the 6B Pygmalion Model. A [TPU v2-8](https://en.wikipedia.org/wiki/Tensor_Processing_Unit) is also available in the free plan, but availibility is low due to high demand.

### Notebooks

There are currently two backends to run the Pygmalion 6B model - [KoboldAI](https://github.com/henk717/KoboldAI) and [Text-Generation-WebUI](https://github.com/oobabooga/text-generation-webui) by oobabooga.

[TavernAI](https://github.com/TavernAI/TavernAI) is a frontend that connects to KoboldAI and essentially facilitates a connection to Pygmalion via Kobold while offering a pleasant looking User Interface. **TavernAI by itself doesn't run Pygmalion - therefore you do not need a powerful PC to run TavernAI.** You cannot use TavernAI with oobabooga's Text-Gen-WebUI.

!!!
If you're on Mobile, use either oobabooga's TextGen or TavernAI.
!!!

=== oobabooga (TextGen)
:desktop_computer:/:iphone: [Click here.](http://127.0.0.1:5005/google-colab/oobabooga) 
===

!!!danger Terminate your session!
When you're done using Pygmalion, please terminate your Colab session! You'll waste your quota otherwise, and might find yourself unable to connect to a GPU backend the next time you login.
![](/static/cloud1.png)
![](/static/cloud2.png)
!!!