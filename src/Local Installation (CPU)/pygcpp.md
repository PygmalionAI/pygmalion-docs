---
order: 100000
icon: code-square
title: Pygmalion C++
---

Initially, the only way to run Pygmalion C++ was through this repo: [AlpinDale/pygmalion.cpp](https://github.com/AlpinDale/pygmalion.cpp). However, thanks to the efforts of concedo from the KoboldAI team, we now have an easy-to-run executable for windows, and a compilable UI for Linux/MacOS/Android users. 

***
## Windows Guide

Running on Windows is exceedingly simple. You can download the `.exe` file from [here](https://github.com/LostRuins/koboldcpp/releases/latest), and the converted 4-bit quantized Pygmalion 6B model from [here](https://huggingface.co/alpindale/pygmalion-6b-ggml/resolve/main/pygmalion-6b-v3-q4_0.bin).

Once you have both files downloaded, all you need to do is drag the `pygmalion-6b-v3-q4_0.bin` file and drop it into `koboldcpp.exe` file. This will load the model and start a Kobold instance in [localhost:8000](http://127.0.0.1:8000) on your browser.

***
## MacOS Guide

The [ggml](https://github.com/ggerganov/ggml) library is primarily designed for Apple Silicon, and as such, it runs *the best* on native Mac. There are no pre-compiled binaries available for MacOS, but compiling it yourself should be very simple.

##### Requirements:
- Python
- C toolchain

##### Installation:

1. Download the latest release file from [here](https://github.com/LostRuins/koboldcpp/releases/latest). You're looking for the `Source code (zip)` file. 
2. Extract it anywhere you want. 
3. Open a Terminal inside the extracted folder.
4. Type in `make` and let it compile the program.
5. Once it's finished, download the model by running this inside the terminal:
```bash
curl -o pygmalion-6b-v3-q4_0.bin https://huggingface.co/alpindale/pygmalion-6b-ggml/resolve/main/pygmalion-6b-v3-q4_0.bin
```
6. Run the model with:
```bash
python koboldcpp.py pygmalion-6b-v3-q4_0.bin
```
7. Open your browser and navigate to [http://127.0.0.1:8000](http://127.0.0.1:8000).
8. You're done!

!!!info No module named 'psutil'?
If you receive such an error doing step 6, run `pip install psutil` and then try again.
!!!
***
## Linux Guide

##### Requirements:
- `python`
- `gcc`
- `python-pip`
- `git`
- `wget`

##### Installation:

Run these commands in order:

```bash
git clone https://github.com/LostRuins/koboldcpp        # Clone the koboldcpp repo
cd koboldcpp                                            # Change directories to the repo
make                                                    # Compile binaries
wget https://huggingface.co/alpindale/pygmalion-6b-ggml/resolve/main/pygmalion-6b-v3-q4_0.bin   # Download the model
python koboldcpp.py pygmalion-6b-v3-q4_0.bin            # Load the model
```

Open your browser and navigate to [localhost:8000](http:127.0.0.1:8000). You're all set.

!!!info No module named 'psutil'?
If you receive such an error doing step 6, run `pip install psutil` and then try again.
!!!

***
## Android

!!!danger System requirements
Your phone needs to have at least 8GB of RAM to run Pygmalion C++. Modern phones use over 4GB of RAM by themselves, so you won't be left with much room for Pygmalion C++ if you don't have at least 8GB.
!!!

##### Requirements:
- [Termux](https://f-droid.org/repo/com.termux_118.apk)

Install Termux from F-Droid.

##### Installation:

1. Open Termux.
2. Type in the following commands one by one and press enter to run them:
3. `pkg install python clang python-pip git`
4. `pip install psutil`
5. `git clone https://github.com/LostRuins/koboldcpp && cd koboldcpp`
6. `make`
7. `wget https://huggingface.co/alpindale/pygmalion-6b-ggml/resolve/main/pygmalion-6b-v3-q4_0.bin`
8. `python koboldcpp.py pygmalion-6b-v3-q4_0.bin`
9. Switch to your browser (don't close Termux) and go to [localhost:8000](http://127.0.0.1:8000).
10. You're done!


## Connecting to Tavern

You can connect Pygmalion C++ to Tavern the same way you would the regular KoboldAI. There's a guide included [here](https://alpindale.github.io/pygmalion-docs/local-installation-(gpu)/tavern/). Note that this won't work for Android, as TavernAI is currently not available for Android locally.