# MB-iSTFT-VITS-8000Hz
### About this repository
This repository is a fork of [https://github.com/MasayaKawamura/MB-iSTFT-VITS](https://github.com/MasayaKawamura/MB-iSTFT-VITS)by Masaya Kawamura, Yuma Shirahata, Ryuichi Yamamoto, Kentaro Tachibana. The original repository is official for [paper](https://arxiv.org/abs/2210.15975).
In this fork, I have added config file [ljs_mb_istft_vits_8k.json] (configs/ljs_mb_istft_vits_8k.json) and modified prameter values of ConvTranspose1d used in Generator of model for training 8000Hz data.

### 1. Pre-requisites
0. Python >= 3.8
0. Clone this repository
0. Install python requirements. Please refer [requirements.txt](requirements.txt)
    1. You may need to install espeak first: `apt-get install espeak`
    2. Note: you can use older version of torch and torchvision, and you have to remove prameter "return_complex" when you call torch.stft in [mel_processing.py] (mel_processing.py) and [stft_loss.py] (stft_loss.py)
0. Download datasets
    1. Download and extract the [LJ Speech dataset](https://keithito.com/LJ-Speech-Dataset/), then rename or create a link to the dataset folder: `ln -s /path/to/LJSpeech-1.1/wavs DUMMY1`
0. Build Monotonic Alignment Search and run preprocessing if you use your own datasets.
```sh
# Cython-version Monotonoic Alignment Search
cd monotonic_align
mkdir monotonic_align
python setup.py build_ext --inplace
```

### 2. Training
In the case of MB-iSTFT-VITS training, run the following script
```sh
python train_latest.py -c configs/ljs_mb_istft_vits_8k.json -m ljs_mb_istft_vits

```
After the training, you can check inference audio using [inference.ipynb](inference.ipynb)

### 3. To do
0. Update ljs_istft_vits_8k.json and ljs_ms_istft_vits_8k.json

## References
- https://github.com/jaywalnut310/vits.git
- https://github.com/rishikksh20/iSTFTNet-pytorch.git
- https://github.com/rishikksh20/melgan.git
