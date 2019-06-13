# Graph matching 문제란?
* Graph matching 문제는 2개의 그래프가 주어졌을 때, 이 둘의 관계를 예측하는 문제이며, 정확하게 일치한지 그래프를 맞추는 exact matching, 그렇지 않은 inexact matching이 있음
* 기존의 방법론들은 두 그래프 간의 affinity score를 maximization하도록 각 그래프의 노드들간의 mapping을 구하는 방식(quadratic assignment problem)이나 두 그래프간의 edit distance를 계산하는 방법을 사용
  * affinity matrix라던가 mapping의 다양성 등에 변주를 든 variation이 존재함
* 최근의 딥러닝 기반 모델에서는 위의 방식이 아닌 node나 graph 자체의 representation을 학습하여, 이들 간이 similarity를 학습하는 방식이 많이 활용됨
  * 기존의 방법론의 내용이 확장되는 형태로 기존의 방법론들도 알아둘 필요가 있음
* subgraph들의 유사도를 활용하는 방안도 많이 이용됨

# 참고 사항
* 본 내용은 scene graph간의 graph matching을 목적으로 하는 연구를 위한 정리이기 때문에 exact graph matching 분야는 제외되어있음

# 참고 문헌
[[1] Yanardag, Pinar, and S. V. N. Vishwanathan. "Deep graph kernels." KDD, 2015. - graph kernels](./DeepGraphKernels/summary.md)