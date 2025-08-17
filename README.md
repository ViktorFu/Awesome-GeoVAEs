# Awesome-GeoVAEs

<a href="https://github.comsindresorhus/awesome"><img src="https://cdn.rawgit.com/sindresorhus/awesome/d7305f38d29fed78fa85652e3a63e154dd8e8829/media/badge.svg" alt="Awesome"></a>

A curated list of awesome research papers, code, and resources for **Variational Autoencoders with Geometric Priors (GeoVAEs)**.

Geometric Priors in VAEs are a class of techniques that impose a structural inductive bias on the latent space by constraining it to a **non-Euclidean manifold** (e.g., a hypersphere or a hyperbolic space). Instead of a flat, unstructured latent space, this approach helps the model learn more meaningful representations that naturally align with the intrinsic geometry of the data, leading to better disentanglement, generalization, and sample quality.

This list is organized by the type of geometric prior used. Contributions are always welcome!

---

## Quick Look: Comparison of Geometries

| Geometry Type      | Core Idea                                                    | Key Advantages                                                              | Best For...                                                                                             |
| ------------------ | ------------------------------------------------------------ | --------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------- |
| **Hyperbolic**     | Models the latent space as a negatively curved space.         | **Efficiently embeds hierarchies**; provides continuous tree-like representations. | Tree-structured data (e.g., taxonomies, social networks, file systems, NLP parse trees).                |
| **Hyperspherical** | Constrains latent vectors to the surface of a unit hypersphere. | **Focuses on direction, not magnitude**; mitigates posterior collapse.      | Directional data where angular relationships matter (e.g., text embeddings, gene expression profiles). |
| **General Manifold** | Learns a general, curved latent space directly from data.    | **Highly flexible**; captures complex intrinsic structures; generates smooth transitions. | Data with continuous, non-linear variations (e.g., object poses, physical simulations, medical imaging). |

---

## Contents

- [1. Hyperbolic VAEs](#1-hyperbolic-vaes)
- [2. Hyperspherical VAEs](#2-hyperspherical-vaes)
- [3. General Manifold VAEs](#3-general-manifold-vaes)
  - [3.1. Geometry-Aware & Structure-Preserving](#31-geometry-aware--structure-preserving)
  - [3.2. Hamiltonian, Symplectic, and Lie Group VAEs](#32-hamiltonian-symplectic-and-lie-group-vaes)
- [4. Foundational Papers & Concepts](#4-foundational-papers--concepts)
- [5. Contributing](#5-contributing)

---

## 1. Hyperbolic VAEs

*   **Analogy**: Think of the latent space as the canopy of a massive tree. There is exponentially more room as you move away from the "trunk" (the origin), making it perfect for representing things that branch out.
*   **Core Idea**: Models the latent space as a hyperbolic space with constant negative curvature. Since the volume of hyperbolic space grows exponentially with the radius, it can embed tree-like or hierarchical structures with very low distortion and high efficiency.
*   **Advantages**:
    *   **Superior Hierarchy Embedding**: Can represent deep hierarchies in very low dimensions.
    *   **Continuous Representation**: Provides a smooth, continuous representation of discrete tree structures.
    *   **Avoids Crowding**: Prevents leaf nodes from collapsing onto each other in the embedding space.

### Papers

- **[Continuous hierarchical representations with poincare variational autoencoders](https://arxiv.org/pdf/1901.06033.pdf)**. *Emile Mathieu, Charline Le Lan, Chris Maddison, Ryota Tomioka*. (NeurIPS 2019). [[Code]](https://github.com/emilemathieu/pvae)
- **[Latent variable modelling with hyperbolic nomalizing flows](https://arxiv.org/pdf/2002.06336.pdf)**. *Avishek Joey Bose, Ariella Smofsky, Lingkai Kung, et al*. (ICML 2020).
- **[A wrapped normal distribution on hyperbolic space for gradient-based learning](https://arxiv.org/pdf/1902.02992.pdf)**. *Yuki Nagano, Ryo Yamaguchi, Yasuhiro Fujita, Kento Koyama*. (ICML 2019).

---

## 2. Hyperspherical VAEs

*   **Analogy**: Imagine the latent space as the surface of a globe. Every point is defined by its direction (latitude/longitude) from the center, not its distance.
*   **Core Idea**: Constrains the latent space to the surface of a unit hypersphere, forcing all latent vectors to have an L2 norm of 1. The model learns the "direction" of the data rather than its "magnitude." This is typically implemented using the von Mises-Fisher (vMF) distribution as a prior.
*   **Advantages**:
    *   **Directional Focus**: Isolates angular relationships by removing magnitude as a factor of variation.
    *   **Mitigates Posterior Collapse**: Prevents latent codes from collapsing to the origin, a common VAE failure mode.
    *   **Natural for Certain Data**: Aligns well with data where normalization is a standard preprocessing step.

### Papers

- **[Hyperspherical variational auto-encoders](https://arxiv.org/pdf/1804.00891.pdf)**. *Tim R. Davidson, Luca Falorsi, Nicola De Cao, Thomas Kipf, Jakub M. Tomczak*. (NeurIPS 2018). [[Code]](https://github.com/nicola-decao/s-vae-pytorch)
- **[Spherical Latent Spaces for stable variational autoencoders](https://arxiv.org/pdf/1808.10805.pdf)**. *Jiacheng Xu, Greg Durrett*. (EMNLP 2018). [[Code]](https://github.com/jiacheng-xu/vmf_vae_nlp)
- **[Disentanglement with hyperspherical latent spaces using diffusion variational autoencoders](https://openreview.net/pdf?id=SylFDSU6Sr)**. *Daniel Hain, Chris Williams, et al*. (NeurIPS 2019 Workshop).

---

## 3. General Manifold VAEs

*   **Core Idea**: Assumes the latent space is a general, curved **Riemannian manifold** whose structure is not known beforehand. The model's goal is to learn this manifold's intrinsic geometry (like local curvature and distances) directly from the data.
*   **Advantages**:
    *   **Maximum Flexibility**: Adapts to complex and unknown data geometries without being restricted to a fixed curvature.
    *   **Realistic Interpolation**: Traversing the learned manifold's geodesics (shortest paths) can generate smoother and more realistic transition samples.

### 3.1. Geometry-Aware & Structure-Preserving

*These models focus on learning the manifold structure implicitly from data or by preserving local relationships.*

- **[Variational autoencoders with Riemannian brownian motion priors](https://arxiv.org/pdf/2002.05227.pdf)**. *Dimitris Kalatzis, David Eklund, Georgios Arvanitidis, Søren Hauberg*. (ICML 2020).
- **[Geometrically enriched latent spaces](https://arxiv.org/pdf/2008.00565.pdf)**. *Georgios Arvanitidis, Søren Hauberg, Bernhard Schölkopf*. (ICML 2020 Workshop).
- **[Data Generation in Low Sample Size Setting Using Manifold Sampling and a Geometry-Aware VAE](https://arxiv.org/pdf/2103.13751.pdf)**. *Clément Chadebec, Stéphanie Allassonnière*. (MICCAI 2021).
- **[Neighborhood Geometric Structure-Preserving Variational Autoencoder for Smooth and Bounded Data Sources](https://pubmed.ncbi.nlm.nih.gov/33556022/)**. *Ruixuan Chen, et al*. (IEEE TNNLS 2021).
- **[NeRF-VAE: A Geometry Aware 3D Scene Generative Model](https://arxiv.org/pdf/2104.00587.pdf)**. *Adam Kosiorek, et al*. (ICML 2021).
- **[Geometric disentanglement for generative latent shape models](https://arxiv.org/pdf/1908.06386.pdf)**. *Tristan Aumentado-Armstrong, et al*. (ICCV 2019).
- **[Learning flat latent manifolds with VAEs](https://arxiv.org/pdf/2002.04881.pdf)**. *Yannik Checker, et al*. (ICLR 2020).
- **[Learning to disentangle factors of variation with manifold interaction](http://proceedings.mlr.press/v32/reed14.pdf)**. *Scott Reed, et al*. (ICML 2014).

### 3.2. Hamiltonian, Symplectic, and Lie Group VAEs

*These models incorporate priors from advanced mathematics and physics (like energy conservation or group theory) to learn structured latent dynamics.*

- **[Hamiltonian variational auto-encoder](https://arxiv.org/pdf/1805.11328.pdf)**. *Anthony Caterini, Arnaud Doucet, Dino Sejdinovic*. (NeurIPS 2018).
- **[Geometry-aware Hamiltonian variational autoe-encoder](https://arxiv.org/pdf/2010.11518.pdf)**. *Clément Chadebec, et al*. (AISTATS 2021).
- **[Quasi-symplectic Langevin variational autoencoder](https://arxiv.org/pdf/2009.01675.pdf)**. *Ya-Ping Wang, Nicholas Ayache, Hervé Delingette*. (2020).
- **[Reparameterizing distributions on Lie groups](https://arxiv.org/pdf/1903.02958.pdf)**. *Luca Falorsi, et al*. (AISTATS 2019).

---

## 4. Foundational Papers & Concepts

*Understanding GeoVAEs requires familiarity with the core concepts of VAEs, disentanglement, and flexible generative models.*

- **[Auto-encoding variational Bayes](https://arxiv.org/pdf/1312.6114.pdf)**. *Diederik P Kingma, Max Welling*. (ICLR 2014).
  - **Why it matters**: The original VAE paper that started it all.
- **[beta-VAE: learning basic visual concepts with a constrained variational framework](https://openreview.net/pdf?id=Sy2fzU9gl)**. *Irina Higgins, et al*. (ICLR 2017).
  - **Why it matters**: A key paper on disentanglement that highlighted the importance of a structured latent space, motivating the search for better geometric priors.
- **[Variational inference with normalizing flows](https://arxiv.org/pdf/1505.05770.pdf)**. *Danilo Jimenez Rezende, Shakir Mohamed*. (ICML 2015).
  - **Why it matters**: Introduces normalizing flows, a powerful technique for learning flexible probability distributions, often combined with geometric priors to define complex densities on manifolds.
- **[The information bottleneck method](https://arxiv.org/pdf/physics/0004057.pdf)**. *Naftali Tishby, Fernando C. Pereira, William Bialek*. (2000).
  - **Why it matters**: Provides the core theoretical principle behind many representation learning objectives, framing learning as a trade-off between compression and prediction.

---

## 5. Contributing

Contributions are always welcome! Please read the [contribution guidelines](CONTRIBUTING.md) first.

If you have any suggestions or find a paper that should be included, please feel free to open an issue or submit a pull request.
