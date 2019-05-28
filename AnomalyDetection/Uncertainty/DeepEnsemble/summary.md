# Simple and Scalable Predictive Uncertainty Estimation using Deep Ensembles

[paper](https://arxiv.org/pdf/1612.01474.pdf)
[code]()

---
* Overview
  * Bayesian neural network를 이용해 uncertainty를 측정하는 방법은 성능이 좋지만 학습하기가 어렵고, 시간이 많이 소요됨
  * Non-bayesian neural network를 이용해 uncertainty를 측정하는 방법을 제안함

* method
  * density network를 이용해 output의 확률분포를 모델링을 함
    * (in regression) density network의 sigma가 measurement noise를 효과적으로 측정해줌
      * 데이터가 내제하고 있는 noise를 의미
  * 여러개의 네트워트를 학습하여 uniformly weighted mixture model로 ensemble을 수행
  * Adversarial example을 추가하여 학습

* result
  * 분류 및 예측 성능 향상이 있음
  * OOD sample에 대한 비교
    * (in classification) OOD sample에 대한 prediction probability의 entropy가 더 커야함 
    * 예측값 확률의 가장큰 값을 threshold로 쳐낸 결과 정확도가 향상됨