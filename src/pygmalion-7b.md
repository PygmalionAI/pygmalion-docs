---
order: 1000
icon: zap
title: Pygmalion 7B
---

!!!info Pygmalion 13B
The same procedure can be applied to LLaMA 13B for obtaining the newly released Pygmalion and Metharme 13B models.
!!!

Due to the LLaMA licensing issues, the weights for Pygmalion-7B and Metharme-7B are released as XOR files - which means they're useless by themselves unless you combine them with the original LLaMA weights. You will need to apply for access to the weights [here](https://docs.google.com/forms/d/e/1FAIpQLSfqNECQnMkycAp2jP4Z9TFX0cGR4uf7b_fBxjY_OjhJILlKGA/viewform). Note that you will need a .edu email address for access. For more info, please refer to the #help-and-questions channel in our [Discord](https://discord.gg/pygmalionai).

## Models

### Chat Model (Pygmalion 7B)

This model is based on Meta's LLaMA 7B, fine-tuned with the regular Pygmalion 6B dataset. This model is purely for chatting and roleplaying purposes, and the same prompt formattings you're used to will work here.

### Instruction Model (Metharme 7B)

This is an experimental model with a new prompt format used during training. It is capable of Chatting, RolePlaying, and Storytelling all at once. The prompting format is entirely different from the Chat Models, so Tavern will likely *not work*. 

!!!warning The exact transformers commit might be incorrect!
I'm not sure exactly which commit we used for converting the original weights - just make sure your converted hashes match the ones [here](https://docs.alpindale.dev/pygmalion-7b/#file-hashes)
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
!!!danger The exact transformers commit might be incorrect!
I'm not sure exactly which commit we used for converting the original weights - just make sure your converted hashes match the ones [here](https://docs.alpindale.dev/pygmalion-7b/#file-hashes). If you find it's incorrect, please submit a PR or an [issue](https://github.com/AlpinDale/pygmalion-docs/issues){target="_blank"} with the correct commit hash.
!!!

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


2. Download this zip file and extract its contents inside the new pygmalion-7b folder:

[!file icon="download" text="Pygmalion 7B JSONs"](https://cdn.discordapp.com/attachments/1068926294017970237/1102062414905749514/pyg-7b.zip)

[!file icon="download" text="Metharme 7B JSONs"](https://cdn.discordapp.com/attachments/1068926294017970237/1102062681722204270/met-7b.zip)

## 7B File hashes

Make sure your files match these sha256 hashes:

- Merged Pygmalion-7B weights:
```
$ sha256sum pygmalion-7b/*
e6e95f80203ae4d3925d420e9eeb31fc11fa4d9a49b40d8c6499838365e3f5a8  config.json
062a37a6d986c38231880f5cce4fa9a0145aeefcf8be9ab23ddf7d600c037aea  generation_config.json
61bcb043c3c4dc4d567ffea91b3074c70d54089eb3f1872b945d7a4e32677edf  pytorch_model-00001-of-00002.bin
41ebe6971edc8f04b0784ef8ed54216fcd36f8a4d51faf415851c9b824769ba2  pytorch_model-00002-of-00002.bin
aca3c1facc89d12311a667c32e85ac86e625990992ea8a189e3b036ba371b931  pytorch_model.bin.index.json
ff3b4a612c4e447acb02d40071bddd989fe0da87eb5b7fe0dbadfc4f74de7531  special_tokens_map.json
9e7aa7d0f67f207036d981d7bbabfbf4b521c4c089c0280fcc08ef9c732634b5  tokenizer_config.json
f9ffc4aede0845ab65324ce5dccb823dca2427f9a0710981e5bc2398d73d8162  tokenizer.json
9e556afd44213b6bd1be2b850ebbbd98f5481437a8021afaf58ee7fb1818d347  tokenizer.model
```

- Original LLaMA 7B weights along with the `tokenizer.model` file (can be found in the root LLaMA directory):
```
$ sha256sum LLaMA/7B/*
7935c843a25ae265d60bf4543b90bfd91c4911b728412b5c1d5cff42a3cd5645  checklist.chk
700df0d3013b703a806d2ae7f1bfb8e59814e3d06ae78be0c66368a50059f33d  consolidated.00.pth
7e89e242ddc0dd6f060b43ca219ce8b3e8f08959a72cb3c0855df8bb04d46265  params.json
9e556afd44213b6bd1be2b850ebbbd98f5481437a8021afaf58ee7fb1818d347  tokenizer.model
```

- LLaMA 7B weights converted to HuggingFace format:
```
$ sha256sum llama-7b-hf/*
e4c3dea29aefc16c0e63825f9ae097dbf5cb5d7c320843a84257e11be3b452c8  config.json
fd7ff399e5568cc21a0a8414f43df88ef7c424995b9b97a90563165d2cf79efd  generation_config.json
0087155d6df07106c1d910bfeb6aab1be8e612dfbf2b56ddfb4ccbde7dbd50d0  pytorch_model-00001-of-00002.bin
461bc5e50200db7813ff99cc0b9316c48ccbd6aaaa31bf8cf7bee0b64bc3eda3  pytorch_model-00002-of-00002.bin
aca3c1facc89d12311a667c32e85ac86e625990992ea8a189e3b036ba371b931  pytorch_model.bin.index.json
ff3b4a612c4e447acb02d40071bddd989fe0da87eb5b7fe0dbadfc4f74de7531  special_tokens_map.json
380608719f3af6ef2b343e2ed53bf55556678609337e88a14f58cc49177b9e18  tokenizer_config.json
f9ffc4aede0845ab65324ce5dccb823dca2427f9a0710981e5bc2398d73d8162  tokenizer.json
9e556afd44213b6bd1be2b850ebbbd98f5481437a8021afaf58ee7fb1818d347  tokenizer.model
```

## 13B File Hashes

Metharme 13B Merged Weights:

```
$ sha256sum metharme-13b-merged/*
be2c276865d1b0759257c0934275f05e02ee520657c2d8ebe3f2a2db1562949a  config.json
a23652fc622a27b8863c39f524707796967095b2a85f334561b11422f71445a2  generation_config.json
07727e130b7e4ec66162920b4e090554e6c58e87d25b433ab8123eb3a55fd5e7  pytorch_model-00001-of-00003.bin
26b6f7e020c94347280d8952b054275fe2293267f9a0e99e1c2bf4df724d99d9  pytorch_model-00002-of-00003.bin
5d00548d2c28ced08ec7b4123749f20e9ca4af2a821724f9ec47a1c5cf0f66d4  pytorch_model-00003-of-00003.bin
72e91e29282dae48ea5562fcf4d6ca0d5a9c2a30ebc8d67174a19e192552a20b  pytorch_model.bin.index.json
bd87e244d21d45c358e5d822aeb2efd4e4d60127e43b648ed3efe7823fd35060  tokenizer_config.json
f9ffc4aede0845ab65324ce5dccb823dca2427f9a0710981e5bc2398d73d8162  tokenizer.json
68147850c080987172d24ad27a9ba2c65c71b46e248e8ee0f0c4eda90e2ca558  tokenizer.model
```

Converted LLaMA 13B weights:

```
$ sha256sum llama-13b-hf/*
ad440bbb8f4af8f499a905f13b073ce3abbc3d4c43d5570ba2583eb296b74727  config.json
fd7ff399e5568cc21a0a8414f43df88ef7c424995b9b97a90563165d2cf79efd  generation_config.json
dd20cdee2637408c6ab88c13f5c27d153bacd0e99f2d55f6a66fbd0269944436  pytorch_model-00001-of-00003.bin
1aba886c5f28d2e2e9b04ab3c4f5bc250c6b06efc1baa3f557677b3097f70e6a  pytorch_model-00002-of-00003.bin
eac58861ca5f3749c819676d908b906d3df38046c09efe055fe78d7678b718e7  pytorch_model-00003-of-00003.bin
92c31ad5e853e9a6660e248871f9bd0cd273518de7ec12ca893e1b1078c10898  pytorch_model.bin.index.json
380608719f3af6ef2b343e2ed53bf55556678609337e88a14f58cc49177b9e18  tokenizer_config.json
f9ffc4aede0845ab65324ce5dccb823dca2427f9a0710981e5bc2398d73d8162  tokenizer.json
9e556afd44213b6bd1be2b850ebbbd98f5481437a8021afaf58ee7fb1818d347  tokenizer.model
```