---
order: 1000
icon: zap
title: Pygmalion 7B
---

Due to the LLaMA licensing issues, the weights for Pygmalion-7B and Metharme-7B are released as XOR files - which means they're useless by themselves unless you combine them with the original LLaMA weights. You will need to apply for access to the weights [here](https://docs.google.com/forms/d/e/1FAIpQLSfqNECQnMkycAp2jP4Z9TFX0cGR4uf7b_fBxjY_OjhJILlKGA/viewform). Note that you will need a .edu email address for access. For more info, please refer to the #help-and-questions channel in our [Discord](https://discord.gg/pygmalionai).

## Chat Model (Pygmalion 7B)

This model is based on Meta's LLaMA 7B, fine-tuned with the regular Pygmalion 6B dataset. This model is purely for chatting and roleplaying purposes, and the same prompt formattings you're used to will work here.

## Instruction Model (Metharme 7B)

This is an experimental model with a new prompt format used during training. It is capable of Chatting, RolePlaying, and Storytelling all at once. The prompting format is entirely different from the Chat Models, so Tavern will likely *not work*. 

!!!warning These instructions are incomplete!
We're working on finalizng these guides.
!!!

## Merging the weights

**Note that this won't work on Windows. If you're using Windows, you will need to do this with WSL2**.

### Create a WSL2 environment (Windows Only)

Download Ubuntu from Microsoft Store (click on the image):

[-![](/static/microsoft.png)](https://apps.microsoft.com/store/detail/ubuntu/9PDXGNCFSCZV){target="_blank"}

<!-- 2. Reboot your PC.
3. Search for Ubuntu in Start Menu and continue to the next section. -->

You're done! Look up "Ubuntu" in the Start Menu and continue to the next section.

### Convert Original LLaMA weights to HF (optional)

#### Requirements
- `python==3.10`
- `git`

**This step can be skipped if you have the weights in HF format already.**
1. Acquire the original LLaMA weights. Apply for access [here](https://docs.google.com/forms/d/e/1FAIpQLSfqNECQnMkycAp2jP4Z9TFX0cGR4uf7b_fBxjY_OjhJILlKGA/viewform). Place them in a location you can easily remember.
2. Open a Terminal instance, and create a clean **Python 3.10** virtual environment:
```bash
python3.10 -m venv xor_venv
source xor_venv/bin/activate
```
3. Clone transformers and switch to the tested version:
```bash
git clone https://github.com/huggingface/transformers.git
cd transformers
git checkout d04ec99bec8a0b432fc03ed60cea9a1a20ebaf3c
pip install .
```

4. Download these **exact** dependency versions:
```bash
pip install torch==1.13.1 accelerate==0.18.0 sentencepiece==0.1.98 protobuf==3.20.1
```

5. Confirm versions by running this command: `pip freeze`. The output should look **exactly** like this:
```bash
accelerate==0.18.0
certifi==2022.12.7
charset-normalizer==3.1.0
filelock==3.12.0
huggingface-hub==0.13.4
idna==3.4
numpy==1.24.2
nvidia-cublas-cu11==11.10.3.66
nvidia-cuda-nvrtc-cu11==11.7.99
nvidia-cuda-runtime-cu11==11.7.99
nvidia-cudnn-cu11==8.5.0.96
packaging==23.1
protobuf==3.20.1
psutil==5.9.5
PyYAML==6.0
regex==2023.3.23
requests==2.28.2
sentencepiece==0.1.98
tokenizers==0.13.3
torch==1.13.1
tqdm==4.65.0
transformers @ file:///mnt/data/koepf/transformers
typing_extensions==4.5.0
urllib3==1.26.15
```

6. Run this in **root** transformers repo:

```bash
python src/transformers/models/llama/convert_llama_weights_to_hf.py --input_dir <input_path_llama_base>  --output_dir <output_path_llama7b_hf> --model_size 7B
```
> Replace `<input_path_llama_base>` with the path to the "LLaMA" folder (this is the folder with all the model variants, including 7B, 13B, 30B, and 65B). Same thing for `<output_path_llama7b_hf>` but for the output path. Can be anywhere you want it to be.

### Merge the weights

!!!danger `decapoda-research/llama-7b-hf` will **not** work!
decapoda-research's repo is severely outdated and will not work. You will need to have a set of 7B weights that have been converted in the past 2 weeks. Please apply for access to the LLaMA weights and convert them yourself.
!!!

1. Apply the XOR files by running the following command using the script provided in the [repo](https://huggingface.co/PygmalionAI/pygmalion-7b/blob/main/xor_codec.py){target="_blank"}:

```bash
python3 xor_codec.py \
  ./pygmalion-7b \
  ./xor_encoded_files \
  /path/to/hf-converted/llama-7b \
  --decode

```

> Replace `/path/to/hf-converted/llama-7b` with the location of your converted LLaMA-7B model.


2. Confirm the hashes by running `rhash -M *` (alternatively, `md5sum *`):

```
4608facb4910118f8dfa80f090cbc4dc  config.json
2917a1cafb895cf57e746cfd7696bfe5  generation_config.json
98764eb949eea16f8e2e1c2d3dea0066  pytorch_model-00001-of-00002.bin
be9ba2f37228a0a9ea0eaf6530aba4de  pytorch_model-00002-of-00002.bin
81648ef3915ed2e83d49fed93122d53e  pytorch_model.bin.index.json
6b2e0a735969660e720c27061ef3f3d3  special_tokens_map.json
fdb311c39b8659a5d5c1991339bafc09  tokenizer.json
eeec4125e9c7560836b4873b6f8e3025  tokenizer.model
f0b65b44265ba51881b1e1881102504f  tokenizer_config.json
```

3. Download this zip file and extract its contents inside the new pygmalion-7b folder:

[!file icon="download" text="Pygmalion 7B JSONs"](https://cdn.discordapp.com/attachments/1068926294017970237/1102062414905749514/pyg-7b.zip)

[!file icon="download" text="Metharme 7B JSONs"](https://cdn.discordapp.com/attachments/1068926294017970237/1102062681722204270/met-7b.zip)