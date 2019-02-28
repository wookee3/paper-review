# Preventing Posterior collapse with delta-VAEs

[paper](https://openreview.net/forum?id=BJe0Gn0cY7)   
[code]()

---
* Overview
  * Proposing an alternative that utilizes the most powerful generative models as decoders, whilst optimising the variational lower bound all while ensuring that the latent variables preserve and encode userful information
  * $\delta-vae$ achieves this by constraining the ariational family for the posterior to have a minimum distance to the prior

* How?
  - KL divergence between the posterior and prior is lower bounded by design
  - Choosing

* Experiments

* My opinions
