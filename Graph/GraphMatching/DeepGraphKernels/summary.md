# Deep Graph Kernels

[paper](https://dl.acm.org/citation.cfm?id=2783417)  
[code]()

keyword: Graph kernel, 

---
* Overview
  * 기존 Graph kernel의 단점을 개선한 방법
    * $M$을 도입하여, 커널이 비슷한 graph를 similar하게 나타내는 커널을 학습(M이 없으면, diagonal 부분만 값이 커지게 됨)
![kernel](./kernel.PNG)

* 기존 graph kernel method에 대한 정리 - [참고자료](https://www.ethz.ch/content/dam/ethz/special-interest/bsse/borgwardt-lab/documents/slides/CA10_WeisfeilerLehman.pdf)
  * Walk based graph kernels
    * 두 그래프의 공통적인 walk 갯수를 세서 이를 사용
  * Product graph kernels
    * 두 graph의 product graph를 생성한 뒤에 walk 기반 계산 
    * 계산량이 $O(n^6)$로 매우 많음 
  * Sortest path kernel
  * Graphlet kernel
  * Weisfeiler-Lehman kernel

* method
  * $M$을 어떻게 사용하고 학습하느냐를 본 연구에서 제안
    * sub-structure similarity via edit distance
      * sub-graph들에 대해 edit distance를 계산하여 $M$ 계산
    * sub-structure similarity via learning
      * word vector를 학습
  * 각 그래프에 대해 subgraphs를 생성하고, 이들에 대한 $M$을 계산한 뒤에 위 수식에 따라 kernel matrix를 계산