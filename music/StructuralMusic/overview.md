# Structural music generation
* 구조를 가지는 음악을 생성하는 것이 목적으로 최종적으로는 32마디 혹은 64마디의 긴 노래를 만들어야 함
* 음악 구조의 가장 기본적인 단위는 주로 마디를 사용하며, 이에 대한 연구가 필요
---

* 문제점
  * 음악의 가장 기본적인 단위는 마디이나 time signature에 따라 마디의 기준이 달라진다는 문제점이 있음    
  * 마디를 사용하지 않을 경우 과연 어떻게 구조를 찾을 것인가?  


* 논의사항
  * 마디를 기본적인 단위로 활용할 때
    * time signature에 따라서 마디를 구성하는 기준이 달라지기 때문에 이에 대한 처리가 필요함
      * downbeat tracking을 하면 time signature를 찾을 수 있나?
    * 또한, 중간에 time signature가 달라지는 경우 어떻게 할 것인지에 대한 논의가 필요함
      * 짧은 마디만 사용할 경우 크게 문제가 안되지만, 긴 melody를 사용하는 경우 중간에 바뀌어서 구조가 바뀌게 됨
    * 해결방안
      1. 4/4 곡만 사용하고, time signature가 발생하는 경우에는 노래 사용하지 않기
      2. 클래식이나 folk송 같이 장르를 통일하여 사용
      3. ...

  * 마디를 사용하지 않을 경우
    * 자기가 알아서 구조를 찾는 방법 (unsupervised)
      * 방법론적으로 어려우며, 상대적으로 난이도가 높음
      * 텍스트에서 활용하는 copy, modify등의 operation을 학습하는 방법 (사용하는 경우도 활용 가능)
      * segmentaiton 필요
    * 다른 음악의 구조 단위를 활용하는 방법 (verse, chorus, ...)
      * 위의 구조를 제공해주는 데이터가 없음
      * 만약, melody, chord extraction을 통해 구한 데이터가 잘 작동한다면, ultimate-guitar에서 crawling한 데이터를 활용할 수 있음

* 방법론
  * jukebox나 vqcpc같은 최신 논문들을 살펴보면 주로 활용하는 방법은 vq-vae를 통해 discrete latent space를 학습하고, 학습된 latent space에 autoregressive language model을 적용해 prior를 학습함. generation시 학습된 prior network에서 latent를 generation하고 이를 이용해 노래를 생성함
  * 위와 같이 할 경우 long-term을 접근하기가 수월해지고, multi-resolution을 보기가 상대적으로 수월함
  * 생성 결과가 continuous에 비해 떨어지는 부분이 없기 때문에 이 방법으로 한것으로 보임
    
  * melody representation
    * melody representation을 어떻게 할 것인가?

  * 마디를 기본적인 단위로 활용할 때
    * VQ-CPC 방식을 기본적으로 생각하고 있음

  * 구조를 활용해서 melody를 copy하여, 멜로디를 만든 다음에 variation을 추가로 주는 방법
