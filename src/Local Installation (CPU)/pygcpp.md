---
order: 100000
icon: code-square
title: koboldcpp
---

Initially, the only way to run Pygmalion on CPU was through this repo: [AlpinDale/pygmalion.cpp](https://github.com/AlpinDale/pygmalion.cpp). However, thanks to the efforts of concedo from the KoboldAI team, we now have an easy-to-run executable for windows, and a compilable UI for Linux/MacOS/Android users.

## 6B model

[!file Pygmalion-6B 4bit (concedo)](https://huggingface.co/concedo/pygmalion-6bv3-ggml-ggjt/resolve/main/pygmalion-6b-v3-ggml-ggjt-q4_0.bin)

If the model above doesn't work for any reason, you can download the old one instead:

[!file Pygmalion-6B 4bit (alpindale)](https://huggingface.co/alpindale/pygmalion-6b-ggml/resolve/main/pygmalion-6b-v3-q4_0.bin)

## 7B model

You will need to obtain [your copy](https://docs.pygmalion.chat/pygmalion-7b/#merging-the-weights) of Pygmalion 7B by merging the original LLaMA (converted to HF format) with the XORed files in the [PygmalionAI/pygmalion-7b](https://huggingface.co/PygmalionAI/pygmalion-7b) repo. You will then have to convert the model to GGML format, and then quantize it down to 4bit/5bit. 

### Linux

#### Requirements
- [`git`](https://docs.pygmalion.chat/tools/git)
- `python`
#### Converstion
1. Obtain the merged weights.
2. Create a new folder and place the Pygmalion-7B weights (with its folder) in there.
3. Open a PowerShell/Terminal instance inside the folder and run:
```bash
git clone https://github.com/ggerganov/llama.cpp
```
4. Convert to GGML format by running this:
```bash
python3 llama.cpp/convert.py pygmalion-7b/ --outtype f32
```
> This will produce a 32-bit GGML model. We convert to 32-bit instead of 16-bit because the original Pygmalion-7B model is in BFloat-16 format, and direct conversion to FP-16 seems to damage accuracy.

5. Compile the quantize program:
```
pushd llama.cpp
make quantize
popd
```
6. Quantize the model:
```
./llama.cpp/quantize pygmalion-7b/model-f32.bin pygmalion-7b-ggml 5
```
> This will output the model in the `q4_2` format, which is the current best 4bit format for GGML. You can also q5_1 which has slightly better accuracy. Here's the full list of conversion types; note that q8_0 does not work with koboldcpp:

```
  type = "q4_0" or 2
  type = "q4_1" or 3
  type = "q4_2" or 5
  type = "q5_0" or 8
  type = "q5_1" or 9
  type = "q8_0" or 7
  ```

***
## Windows Guide

Running on Windows is exceedingly simple. You can download the `.exe` file from [here](https://github.com/LostRuins/koboldcpp/releases/latest), and the Pygmalion 6B model linked above.

Once you have both files downloaded, all you need to do is drag the `pygmalion-6b-v3-q4_0.bin` file and drop it into `koboldcpp.exe` file. This will load the model and start a Kobold instance in [localhost:5001](http://127.0.0.1:5001) on your browser. **You can also simply double-click on the .exe file.**

***
## MacOS Guide

The [ggml](https://github.com/ggerganov/ggml) library is primarily designed for Apple Silicon, and as such, it runs *the best* on native Mac. There are no pre-compiled binaries available for MacOS, but compiling it yourself should be very simple.

##### Requirements:
- Python
- C toolchain

##### Install the requirements:
1. Open a terminal.
2. Paste this command and press enter to execute it:
```bash
xcode-select --install
```
3. Install Python from [here](https://www.python.org/ftp/python/3.10.9/python-3.10.9-macos11.pkg).

##### Installation:

1. Download the latest release file from [here](https://github.com/LostRuins/koboldcpp/releases/latest). You're looking for the `Source code (zip)` file. 
2. Extract it anywhere you want. 
3. Open a Terminal inside the extracted folder.
4. Type in `make` and let it compile the program.
5. Once it's finished, download the model and place it inside the `koboldcpp` folder.
6. Run the model with:
```bash
python3 koboldcpp.py pygmalion-6b-v3-ggml-ggjt-q4_0.bin
```
7. Open your browser and navigate to [http://127.0.0.1:5001](http://127.0.0.1:5001).
8. You're done!

###### macOS Quickstart
If you want to launch it again later, all you need to do is open a terminal inside the `koboldcpp` folder, and run:
```bash
python3 koboldcpp.py pygmalion-6b-v3-ggml-ggjt-q4_0.bin
```
Make sure you bookmark [http://localhost:5001](http://localhost:5001) so you can easily open the Koboldcpp interface.

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
wget https://huggingface.co/concedo/pygmalion-6bv3-ggml-ggjt/resolve/main/pygmalion-6b-v3-ggml-ggjt-q4_0.bin   # Download the model, skip if you've already done this
python koboldcpp.py pygmalion-6b-v3-ggml-ggjt-q4_0.bin            # Load the model
```

Open your browser and navigate to [localhost:5001](http:127.0.0.1:5001). You're all set.

###### Linux Quickstart
If you want to launch it again later, all you need to do is open a terminal inside the `koboldcpp` folder, and running:
```bash
python3 koboldcpp.py pygmalion-6b-v3-ggml-ggjt-q4_0.bin
```
Make sure you bookmark [http://localhost:5001](http://localhost:5001) so you can easily open the Koboldcpp interface.


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
3. `pkg update && pkg upgrade`
4. `pkg install python clang python-pip git openssl`
5. `pip install psutil`
6. `git clone https://github.com/LostRuins/koboldcpp && cd koboldcpp`
7. `make`
8. `pkg install wget`
9. `wget https://huggingface.co/concedo/pygmalion-6bv3-ggml-ggjt/resolve/main/pygmalion-6b-v3-ggml-ggjt-q4_0.bin`
10. `python koboldcpp.py pygmalion-6b-v3-ggml-ggjt-q4_0.bin`
11. Switch to your browser (don't close Termux) and go to [localhost:5001](http://127.0.0.1:5001).
12. You're done!

##### Android Quickstart
If you want to launch it again, open Termux and make sure you're in the koboldcpp folder. You can confirm this by checking whether the bash prompt is `~ $` or `~/koboldcpp $`. If it's the former, run `cd koboldcpp`. If it's the latter, continue.

Type this in to run koboldcpp again:
```
python koboldcpp.py pygmalion-6b-v3-ggml-ggjt-q4_0.bin
```

Now open [http://localhost:5001](http://localhost:5001) on your browser.

***
## Connecting to Tavern

You can connect Pygmalion C++ to Tavern the same way you would the regular KoboldAI. There's a guide included [here](https://docs.pygmalion.chat/pygmalion-extras/sillytavern/).

## Connecting to Agnaistic

You can connect Pygmalion C++ to Agnaistic the same way you would the regular KoboldAI. There's a guide included [here](https://docs.pygmalion.chat/pygmalion-extras/agnaistic/).
