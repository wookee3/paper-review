# Distill, Adapt, Distill: Training Small, In-Domain Models for Neural Machine Translation
[paper](https://www.aclweb.org/anthology/2020.ngt-1.12.pdf)
[code]()

---
## recommendation
1. using an adapted teacher gives the best or close to the best results
2. To get the full benefit of general-domain data, the small models must be directly pre-trained on general-domain data
```
Recommended distill and adapt training
1. Distill general-domain data to improve
general-domain student performance.
2. Adapt the best model from Step 1 to indomain data.
(2-10 BLEU better than no adaptation)
3. Adapt the teacher and distill again in-domain.
(0-2 BLEU better than no or non-adapted
teacher)
```
