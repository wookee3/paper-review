# Domain Adaptation & Knowledge Distillation
Language modeling 분야에서 활용되는 DA 및 KD 방법론 정리하였으며, 추후 music generator에서 활용하기 위한 방법론을 위주로 정리

---
## Domain adaptation
* General domain 혹은 특정 도메인 데이터로 학습되어 있는 모델을 initial model로 specific domain data로 추가 학습하는 방법
* 대표적으로 pre-train되어 있는 모델을 fine-tuning하는 방법이 있음
* 추후, 다양한 장르나 스타일의 노래를 생성하는 모델을 학습할 때 활용
  * 이 외에도 few-shot 기반의 generative model 학습 기법도 정리 예정
---
## Knowledge distillation
* 많은 데이터로 학습된 teacher model을 기반으로 student model이 학습할 수 있도록 하는방법
* 토큰 확률간의 차이(KLD)를 minimization하는 방법을 주로 사용함
* 주로 작은 네트워크를 학습할 때 주로 활용하며, teacher model과 student model은 같은 데이터를 활용함
* 추후 빠른 inference를 위해 사이즈가 작은 모델을 학습하는 것에 활용
---
## Plan
* [Music](../../music/StyleTransfer/overview.md)  
* https://www.aclweb.org/anthology/2020.acl-main.692.pdf

---
## References
[1] [Distill, Adapt, Distill:
Training Small, In-Domain Models for Neural Machine Translation](https://www.aclweb.org/anthology/2020.ngt-1.12.pdf)  
[2]  
[3]  
[4]  
[5]  
[6]  
[7]  
[8]  
[9]  
[10]  
