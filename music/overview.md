# Symbolic representation
* 분류 기준이 orthogonal 하지 않기 때문에 중복이있거나 해당되는데 메인이 아니라서 빠지는 것이 있을 수 있음. 이에 자세한 내용은 설명글에 들어가서 확인 필요
* 최적화 방법, 문제의 종류 및 네트워크 특징 등 3가지 기준으로 분류

---
## Optimization
### Language modeling - MLE loss (RNN 계열 + Transformer 계열)
* 대부분의 경우 이 loss function을 기본으로 사용하고 있으며, 대표적인 music generative model을 기술
* [MusicTransformer](./MusicTransformer/MusicTransformer.md)
* [MusicVAE]()

### GAN
* [Can GAN originate new electronic dance music genres?—Generating novelrhythm patterns using GAN with Genre Ambiguity Loss](https://arxiv.org/pdf/2011.13062.pdf)
* [MuseGAN]()
* [MIDINet]()

### Reinforcement learning

---
## Problem
* 기본적인 language modeling은 제외
### Controlled generation

### Inpainting

### Accompaniment

### Style transfer + conversion
--- 
## Network structure
### Transformer
* [MusicTransformer](./MusicTransformer/MusicTransformer.md)
### VAE

### CNN
---
# Audio
* [Jukebox]()

--- 
# 평가방법