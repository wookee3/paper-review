# Detecting Anomalous Faces with 'No Peeking' Autoencoders

[paper](https://arxiv.org/pdf/1802.05798.pdf)  
[code]()

---
* Overview
    * inpaiting autoencoders


* method
  * 얼굴의 일부분을 box로 가린다음에 aucoencoder를 통과시키면, 가려진 부분은 나머지 얼굴에 따라 가장 대표적인 파트를 작성하게 됨
  * 실제 그림과의 차이인 residual loss를 이용하여 anomaly score 계산

 