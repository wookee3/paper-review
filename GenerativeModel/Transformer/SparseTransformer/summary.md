# Generative Modeling with Sparse Transformers

[paper](https://arxiv.org/abs/1904.10509)  
[code](https://github.com/openai/sparse_attention)

---
* Overview
  * 기존 transformer는 self-attention을 위해 $O(N^2)$의 계산량이 필요하기 때문에 이를 sparse attention으로 수정해서 $O(N\sqrt{N})$으로 줄임