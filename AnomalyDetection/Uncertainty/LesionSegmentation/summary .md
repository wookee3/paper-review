# Uncertainty quantification using Beaysian neural networks in classification: Application to ischemic stroke lesion segmentation

[paper](https://openreview.net/forum?id=Sk_P2Q9sG)  
[code]()

---
* Overview
  * Gal의 방법의 단점을 개선하는 방향으로 진행

* method
  * Dropout as bnn 방식을 적용하되, 추가 파라미터 없이, aleatoric과 epistemic uncertainty를 계산
  * 기존의 방식의 단점은 probability가 아니라 logit을 사용한다는 점과 diagonal covariance matrix를 사용해서 label간 correlation이 고려가 안되는 단점을 개선
