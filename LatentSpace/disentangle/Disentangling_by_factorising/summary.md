# Disentagling by Factorising

[paper](https://arxiv.org/pdf/1802.05983.pdf)   
[code]()

---
* Overview
  * Proposing FactorVAE, a method that disentagles by encouraging the distributionof representations to be factorial and hence independent across the dimensions
  * Highlighting the problems of a comonly used disentaglement metric and introduce a new metric that does not suffer from them

* Model  
![model](./model.png)
  - Assume that factors vary independently, we wish for a factorial distribution $q(z) = \prod_{j=1}^{d}q(z_j)$
  - Loss function  $\frac{1}{N}\sum_{1}^{N}\left[\mathbb{E}_{q(z|x^{(i)})}\left[\log p(x^{(i)}|z)\right] - KL(q(z|x^{(i)})||p(z)) \\ - \gamma KL(q(z)|\bar{q}(z)) \right]$
  - $q(z)$ and $\bar{q}(z)$ is not tractable, use another method.
    1. Choosing a datapoint from $x(i)$  
![algorithm](./algorithm.png)
  - metric
    1. Choose a factor k
    2. generate data with this factor fixed but all other factors varying randomly
    3. obtain their representations
    4. normalise each dimension by its empirical standard deviation over the full datasets
    5. take the empirical variance in each dimension of these normalised representations
    6. the index of the dimension with the lowest variance and the target index k provide one training input/output example for the classifier
![metric](./metric.png)
* Experiments

* My opinions
