# Deep Anomaly Detection Using Geometric Transformations

[paper](https://arxiv.org/abs/1805.10917.pdf)  
[code](https://github.com/izikgo/AnomalyDetectionTransformations)

---
* Overview
  * Reconstruction-based anomaly score
    * reconstruction error를 anomaly score로 간주하거나 reconstruction probability를 계산
  * Reconstruction-based representation learning
    * 확률분포를 예측해서 low-density 영역에 이미지가 분포하면 anomaly sample로 간주
  * 본 연구에서는 geometric transformation을 이용해 transformation 종류를 정답으로 하는 레이블 데이터를 생성하여 학습하고, 이에 대한 예측값을 anomaly score로 활용

* method
  * normality score  
  $n_{S}(x)=\sum_{i=0}^{k-1}\log{p(y(T_{i}(x))|T_{i})}$  
  $p(y(T_{i}(x))|T_{i}) \sim Dir(\alpha_{i})$
  * algorithm
    * training
      1. $|T|$개의 geometric transformation을 적용해 총 $|T||S|$개의 데이터 생성 
      2. 어떤 geometric transformation을 적용한건지 예측하는 classifier 학습
    * inference
      1. $n_{S}(x)$ 값을 기준으로 계산
