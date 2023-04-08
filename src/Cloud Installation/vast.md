---
order: 100
icon: cloud
title: Vast AI
---

[Vast AI](https://vast.ai) is a cloud computing service that provides high-end consumer and datacenter GPUs for very cheap prices. You can easily rent one of their many GPUs and use them to run Pygmalion AI.

## Why Vast.ai?
Google Colab offers free GPUs, however, Google is quite restrictive about how the end-user makes use of their notebooks. They have already banned PygmalionAI specifically from their notebooks, so Colab users will be very limited in what they can do. Due to their cheap prices, vast.ai should be quite affordable for the majority of users. 

## Get started

Use [this url](https://cloud.vast.ai/?ref_id=59151&template_id=7fa3f8c321d7055490fe5d3bc5834528) to set up a PygmalionAI docker template. This will install all the necessary requirements to run PygmalionAI via a docker image.

After opening the URL, you'll be prompted to sign up if it's your first time using vast.ai's services. 

You'll be greeted with the Instances page, where you can select which GPU to use. For PygmalionAI, the cheaptest and best option is an NVIDIA RTX A5000 24GB, which allows for the maximum context size at 2048 tokens. 
![](/static/vast1.png)

Make sure you set the Disk size to at least 40GB, and the price to the increasing order, as demonstrated in the screenshot above. 

Assuming you've set up a [billing plan](https://cloud.vast.ai/billing/), you should be able to immediately rent your desired machine and get started.

Click on "Rent" next to your selected GPU to get started. 
![](/static/vast2.png)


Now, head on over to your [Instances page](https://cloud.vast.ai/instances/) and wait for your machine to setup everything for you.

!!!info This can take a while!
Depending on the download speed of the machine you selected, it could take up to 5 minutes. If it's especially slow at 100mbps, it could potentially take 20 minutes. Make sure you select a machine with a fast internet connection.
!!!

![](/static/vast3.png)
![](/static/vast4.png)

Once it's finished loading, click on the logs button to view your remote url:
![](/static/vast5.png)
![](/static/vast6.png)

!!!info This can also take a while!
This process can take up to 3 minutes, so it's advised to close and re-open the logs window until the url shows up at the end.
!!!

Now, paste the URL in a browser tab and you're ready to use Kobold! You can load Pygmalion 6B by clicking on `Models` on the top-left corner of the screen, selecting the `Chat models` section, selecting Pygmalion 6B, and then clicking on `Load`. This will download the model for you. Keep in mind that the download is 16GB, but if you've chosen a machine with a fast download speed, it shouldn't take long. The steps should be familiar for users running locally, so you can also refer to the [Local installation guide for Kobold](https://docs.alpindale.dev/local-installation-(gpu)/kobold/).

!!!success You're done!
You're now ready to use PygmalionAI! Make sure you delete (or stop, if you don't mind paying for the hourly storage charges of 0.8 cents/hr) your instance so you won't be billed when you're not using your instance. If you delete the instance, you'll have to go through the process of setting it up again, but stopping and resuming should pick up from where you left off. 
!!!

## Connecting your instance to TavernAI

You can easily use TavernAI along with Kobold. Follow the instructions in the [Tavern guide](https://docs.alpindale.dev/local-installation-(gpu)/tavern/) but instead of inputting `localhost:5000/api`, use your `trycloudflare.com` link. Assuming your URL was `https://pieces-strictly-transparency-luther.trycloudflare.com/new_ui`, you would paste it as `https://pieces-strictly-transparency-luther.trycloudflare.com/api` inside Tavern. Note that the `new_ui` part is removed and replaced with `/api`. 

