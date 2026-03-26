# Efficient Mixture Learning in Black-Box Variational Inference
Code for reproducing results for [Efficient Mixture Learning in Black-Box Variational Inference](https://arxiv.org/pdf/2406.07083) - Proceedings of the 41 st International Conference on Machine Learning (ICML), Vienna, Austria. PMLR 235, 2024.

## Abstract
Mixture variational distributions in black box variational inference (BBVI) have demonstrated impressive results in challenging density estimation tasks. However, currently scaling the number of mixture components can lead to a linear increase in the number of learnable parameters and a quadratic increase in inference time due to the evaluation of the evidence lower bound (ELBO). Our two key contributions address these limitations. First, we introduce the novel Multiple Importance Sampling Variational Autoencoder (*MISVAE*), which amortizes the mapping from input to mixture-parameter space using one-hot encodings. Fortunately, with *MISVAE*, each additional mixture component incurs a negligible increase in network parameters. Second, we construct two new estimators of the ELBO for mixtures in BBVI, enabling a tremendous reduction in inference time with marginal or even improved impact on performance. Collectively, our contributions enable scalability to hundreds of mixture components and provide superior estimation performance in shorter time, with fewer network parameters compared to previous Mixture VAEs. Experimenting with *MISVAE*, we achieve astonishing, SOTA results on MNIST. Furthermore, we empirically validate our estimators in other BBVI settings, including Bayesian phylogenetic inference, where we improve inference times for the SOTA mixture model on eight data sets. 

## How to train on MNIST
**Note** that in the codebase, the parameter `--S` corresponds to 'A' in the paper terminology, and `--n_A` corresponds to 'S' in the paper. The `--estimator` parameter can be set to either 's2a' or 's2s', depending on the desired estimator. To train on MNIST with $A=20$ and $S=2$ using the 's2a' estimator, for example, one would use the command:

```
python -m mnist_train --L_final 1000 --S 20 --estimator s2a --n_A 2
```
