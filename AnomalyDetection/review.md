# Summarization for Anomaly Detection
본 summary는 의료 데이터에 anomaly detection(이상치 탐지)를 적용하는 연구를 위한 요약으로 의료 데이터의 특징인 label이 없거나 거의 없는 경우에 사용되는 방법론을 위주로 구성되어있음. 또한, 이를 위한 augmentation이나 방법론을 위주로 정리함.  

---
## Why difficult?
1. 의료 데이터는 레이블된 데이터가 거의 없다
2. 레이블되지 않은 데이터도 많지 않다
3. (my opinion) 의료 데이터는 굉장히 dimension이 큰데 anomaly가 전체 이미지 중에 소수 부분에서만 나타나고 나머지는 정상적으로 보이는 경우가 대부분이다
4. 연구 결과가 adversarial attack과 같은 machine learning 시스템 공격에 대한 연구에도 활용될 수 있을 것임  

---
## Methods
* Augmentation  
anomaly detection 또는 의료 데이터를 위한 augmentation 방법론들의 모음  

* One-class classification  
one-class SVM이 가장 대표적인 방법론임. 최근에 제안되는 방법론들은 autoencoder를 통해 latent space를 배우고 이 space 상에서 one-class classification을 학습하거나 discriminator를 classifier로 사용함
[ref 5.](#ref5) discriminator를 classifier로 사용하며, reconstruction 결과를 anomaly score 계산에 활용  
[ref 6.](#ref6) 학습된 latent space 상에서 rbf svm classifier 학습

* Latent based model (GAN, VAE)  
neural network를 통해 학습된 latent space를 이용한 방법론들로 GAN, VAE를 활용하는 방법이 가장 대표적이다. latent space를 이용해 다양한 응용이 가능하며, 다르게 분류된 방법에서도 이를 활용하는 경우가 있다. anomaly score로 reconstruction loss나 discriminator loss를 주로 사용함.  
[ref 2.](#ref2) GAN을 적용하여 residual loss와 discriminator loss를 anomaly score로 anomaly detection 수행   
[ref 3.](#ref3) AnoGAN의 encoder가 없어서 시간이 오래걸린다는 점을 VAE를 도입해 개선한 모델. 실험결과에서 inference time 뿐만 아니라 성능도 우수하다고 나타나나 확인이 필요함  
[ref 7.](#ref7) Adversarial autoencoder에 image classifier와 informative negative mining을 도입하여 latent space 상의 out-of-distribution을 찾은 뒤 해당 영역을 in-distribution sample을 생성하도록 학습. 즉, 전체 latent space에서 out-of-distribution이 최대한 생성되지 않도록 함. 따라서 reconstruction error가 anomaly score로써 더 적합해짐

* density estimation based model  
classifier가 학습되있는 경우에 사용하는 방법론들이 최근에 대두됨.

* etc
  * Memory based model  
[ref 4.](#ref4) 일명 MemVAE로 쿼리 이미지를 latent space로 보내고 latent space 상에서 가까운 메모리를 보고 reconstruction error를 이용해 이상치를 탐지함. 정상인 데이터 수가 매우 적을 경우 성능이 떨어질 것으로 생각됨  

---
## References  
<a id="ref1"></a> 1. [Deep Learning for Anomaly Detection: A Survey](https://arxiv.org/abs/1901.03407.pdf)  
<a id="ref2"></a> 2. [Unsupervised Anomaly Detection with GANs to Guide Marker Discovery (AnoGAN)](./AnoGAN_/summary.md)  
<a id="ref3"></a> 3. [Deep Autoencoding Models for Unsupervised Anomaly Segmentation in Brain MR Images (AnoVAEGan)](./AnoVAEGan_/summary.md)  
<a id="ref4"></a> 4. [Memorizing Normality to Detect Anomaly: Memory-augmented Deep Autoencoder for Unsupervsied Anomaly Detection (MemVAE)](./MemAE_/summary.md)  
<a id="ref5"></a> 5. [Adversarially learned one-class classifier for novelty detection](./AdversarialOneClass/summary.md)  
<a id="ref6"></a> 6. [Satellite image forgery detection and localization using GAN and one-class classifier](./SatelliteClassifier/summary.md)  
<a id="ref7"></a> 7. [OCGAN: One-class Novelty Detection Using GANs with Constrained Latent Representations](./OCGAN_/summary.md)  
