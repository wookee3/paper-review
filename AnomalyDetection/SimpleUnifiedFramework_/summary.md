# A Simple Unified Framework for Detecting Out-of-Distribution Samples and Adversarial Attacks

[paper](https://arxiv.org/abs/1807.03888.pdf)  
[code](https://github.com/pokaxpoka/deep_Mahalanobis_detector)

---

* overview
  * pre-trained softmax neural classifier가 있을 때, mahalanobis distance 기반의 방법론을 제안
  * 제안된 방법론은 abnormal sample 뿐만 아니라 adversarial attack도 감지할 수 있다는 특징이 있음
  * medical image에서는 unsupervised이고 데이터 수가 매우 적은 상황이기 때문에 사용이 쉽지는 않음 (pre-trained softmax neural classifier가 없을 것으로 생각됨)

* method
  * pre-trained softmax neural classifier를 이용해 generative classifier를 만듬
  * pre-trained neural net의 output을 $f(x)$라고 할 때, $f(x)$가 class-conditional gaussian distribution을 따른다고 가정하고 score를 계산함.
  * 이렇게 할 경우 단순히 classification boundary에서 멀어서, 잘분류 되는 것으로 보이는 abnormal sample들이 걸러지게 됨 (label에 대한 overfitting이 방지됨)
  * 이 외에 input pre-processing, feature ensemble의 calibration techniques이 반영됨
