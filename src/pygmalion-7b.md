---
order: 1000
icon: terminal
title: Pygmalion 7B
---

Due to the LLaMA licensing issues, the weights for Pygmalion-7B and Metharme-7B are released as XOR files - which means they're useless by themselves unless you combine them with the original LLaMA weights. You will need to apply for access to the weights [here](https://docs.google.com/forms/d/e/1FAIpQLSfqNECQnMkycAp2jP4Z9TFX0cGR4uf7b_fBxjY_OjhJILlKGA/viewform). Note that you will need a .edu email address for access. For more info, please refer to the #help-and-questions channel in our [Discord](https://discord.gg/pygmalionai).

## Chat Model (Pygmalion 7B)

This model is based on Meta's LLaMA 7B, fine-tuned with the regular Pygmalion 6B dataset. This model is purely for chatting and roleplaying purposes, and the same prompt formattings you're used to will work here.

## Instruction Model (Metharme 7B)

This is an experimental model with a new prompt format used during training. It is capable of Chatting, RolePlaying, and Storytelling all at once. The prompting format is entirely different from the Chat Models, so Tavern will likely *not work*. 

!!!warning These instructions are incomplete!
We're working on finalizng these
!!!

## Merging the weights

**Note that this won't work on Windows. If you're using Windows, you will need to do this with WSL2**.

### Convert Original LLaMA weights to HF (optional)
**This step can be skipped if you have the weights in HF format already.**
1. Acquire the original LLaMA weights. Apply for access [here](https://docs.google.com/forms/d/e/1FAIpQLSfqNECQnMkycAp2jP4Z9TFX0cGR4uf7b_fBxjY_OjhJILlKGA/viewform).
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

### Merge the weights

Apply the XOR files by running the following script using the script provided in the [repo](https://huggingface.co/pygmalion-7b):

```bash
python xor_codec.py pygmalion-7b/ llama7b_hf/
```
