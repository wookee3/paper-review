# DeepWalk: Online Learning of Social Representation

[paper](http://www.perozzi.net/publications/14_kdd_deepwalk.pdf)  
[code](https://github.com/phanein/deepwalk)

---
* Overview
  * node embedding을 학습하는 방법으로 random walk의 결과인 subgraph를 문장으로 생각하고 word vector를 학습하는 skip-gram 방법을 적용함
  * 학습된 embedding을 이용하여, large-scale network의 multi-label classification문제에서 높은 성능을 보여줌
  * 추후 Online learning이 가능하다는 장점이 있음

* Method
  * 