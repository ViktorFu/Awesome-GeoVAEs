# Awesome-GeoVAEs

<a href="https://github.com/sindresorhus/awesome"><img src="https://cdn.rawgit.com/sindresorhus/awesome/d7305f38d29fed78fa85652e3a63e154dd8e8829/media/badge.svg" alt="Awesome"></a>

A curated list of awesome research papers and resources on Variational Autoencoders with Geometric Priors (GeoVAEs).

**Geometric Priors in VAEs** are a class of techniques that constrain the latent space to a non-Euclidean manifold (e.g., a hypersphere or a hyperbolic space). This inductive bias helps the model learn more meaningful and structured representations that align with the intrinsic geometry of the data.

This list is organized by the type of geometric prior used. Contributions are welcome!

## Comparison of Geometric VAE Types

| Geometry Type | Core Idea | Advantages | Suitable Data Types |
|---------------|-----------|------------|---------------------|
| **Hyperbolic** | Models latent space as hyperbolic space with negative curvature | Efficiently embeds hierarchical structures, provides continuous hierarchical representation | Tree-structured, hierarchical data (text classification, social networks, bioinformatics) |
| **Hyperspherical** | Constrains latent space to unit hypersphere | Focuses on direction rather than magnitude, mitigates posterior collapse | Directional data where angular relationships matter (text embeddings, gene expression profiles) |
| **General Manifold** | Learns a general, curved latent space from data | Highly flexible, captures complex intrinsic structures, generates smooth transitions | Complex data with continuous, non-linear variations (physical systems, pose variations, medical imaging) |

## Contents

- [1. Hyperbolic VAEs](#1-hyperbolic-vaes)
- [2. Hyperspherical VAEs](#2-hyperspherical-vaes)
- [3. General Manifold VAEs](#3-general-manifold-vaes)

---

## 1. Hyperbolic VAEs

- **Core Idea**: Models the latent space as hyperbolic space with negative curvature. Since the volume of hyperbolic space grows exponentially with radius, it can efficiently embed tree-like or hierarchical structures.
- **Advantages**: Efficiently embeds hierarchical structures, provides continuous hierarchical representation, avoids "crowding" of leaf nodes in the embedding space.
- **Suitable Data Types**: **Tree-structured, hierarchical data** (such as text classification, social networks, bioinformatics, code structure analysis).

### Papers

- **[Continuous hierarchical representations with poincare variational autoencoders](https://arxiv.org/pdf/1901.06033.pdf)**. *Emile Mathieu, Charline Le Lan, Chris Maddison, Ryota Tomioka*. (NeurIPS 2019). [[Code]](https://github.com/emilemathieu/pvae)
- **[Latent variable modelling with hyperbolic nomalizing flows](https://arxiv.org/pdf/2002.06336.pdf)**. *Avishek Joey Bose, Ariella Smofsky, Lingkai Kung, et al*. (ICML 2020).
- **[A wrapped normal distribution on hyperbolic space for gradient-based learning](https://arxiv.org/pdf/1902.02992.pdf)**. *Yuki Nagano, Ryo Yamaguchi, Yasuhiro Fujita, Kento Koyama*. (ICML 2019).

---

## 2. Hyperspherical VAEs

- **Core Idea**: Constrains the latent space to the unit hypersphere, forcing all latent vectors to have L2 norm of 1. The model learns the "direction" of the data rather than its "magnitude." This is typically implemented via the von Mises-Fisher (vMF) distribution.
- **Advantages**: Focuses on direction rather than length, effectively mitigates posterior collapse, naturally suited for directional data.
- **Suitable Data Types**: **Directional data where angular relationships matter** (such as text embeddings, gene expression profiles, image styles).

### Papers

- **[Hyperspherical variational auto-encoders](https://arxiv.org/pdf/1804.00891.pdf)**. *Tim R. Davidson, Luca Falorsi, Nicola De Cao, Thomas Kipf, Jakub M. Tomczak*. (NeurIPS 2018). [[Code]](https://github.com/nicola-decao/s-vae-pytorch)
- **[Spherical Latent Spaces for stable variational autoencoders](https://arxiv.org/pdf/1808.10805.pdf)**. *Jiacheng Xu, Greg Durrett*. (EMNLP 2018). [[Code]](https://github.com/jiacheng-xu/vmf_vae_nlp)
- **[Disentanglement with hyperspherical latent spaces using diffusion variational autoencoders](https://openreview.net/pdf?id=SylFDSU6Sr)**. *Daniel Hain, Chris Williams, et al*. (NeurIPS 2019 Workshop).

---

## 3. General Manifold VAEs

- **Core Idea**: Does not assume a specific geometric shape, but rather assumes the latent space is a general, curved Riemannian manifold. The model aims to learn this manifold's intrinsic geometric structure directly from the data.
- **Advantages**: Highly flexible, can capture complex intrinsic structures, interpolation along the manifold's geodesics can generate smoother, more realistic transition samples.
- **Suitable Data Types**: **Complex data with continuous, non-linear variations** (such as physical system simulations, robot movements, object pose variations, disease progression in medical imaging).

### Papers

- **[Variational autoencoders with Riemannian brownian motion priors](https://arxiv.org/pdf/2002.05227.pdf)**. *Dimitris Kalatzis, David Eklund, Georgios Arvanitidis, Søren Hauberg*. (ICML 2020).
- **[Geometrically enriched latent spaces](https://arxiv.org/pdf/2008.00565.pdf)**. *Georgios Arvanitidis, Søren Hauberg, Bernhard Schölkopf*. (ICML 2020 Workshop).
- **[Data Generation in Low Sample Size Setting Using Manifold Sampling and a Geometry-Aware VAE](https://arxiv.org/pdf/2103.13751.pdf)**. *Clément Chadebec, Stéphanie Allassonnière*. (MICCAI 2021).
