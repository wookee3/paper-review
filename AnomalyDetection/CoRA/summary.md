# Learning Competitive and Discriminative Reconstructions for Anomaly Detection

[paper](https://arxiv.org/abs/1903.07058)  
[code]()

---
* Overview
  * 기존 reconstruction based 방법론들은 threshold를 잘 찾아줘야한다는 단점이 있음
  * 또한, outlier는 어떻게 생겼는지 모르기 때문에 overfitting이 발생하거나 threshold를 찾기 어려움
  * 하나의 인코더와 2개의 디코더를 활용해 latent space 상에서 분리가 되게 학습
  * positive data와 unlabeled data(normal, abnormal 섞임)가 주어졌을 때 쓰는 방법

* method
  * 하나의 encoder와 2개의 decoder(inlier,outlier)가 있는데 regularization을 추가해서 latent space 상에서 inlier와 outlier를 다르게 분포되도록 encoder를 학습함
  * decoder는 학습 때, 클러스터링처럼 라벨을 예측하도록 사용하는데 사용됨
  * neighborhood를 어떻게 정의하는지가 전혀 나와있지가 않아서 잘 모르겠음
    * 아마도 레이블이 같은애들이 neighborhood인거 같음

