# Awesome-GeoVAEs

<a href="https://github.com/sindresorhus/awesome"><img src="https://cdn.rawgit.com/sindresorhus/awesome/d7305f38d29fed78fa85652e3a63e154dd8e8829/media/badge.svg" alt="Awesome"></a>

A curated list of awesome research papers and resources on Variational Autoencoders with Geometric Priors (GeoVAEs).

**几何先验变分自编码器（GeoVAEs）** 是一类将潜在空间约束到非欧几里得流形（如超球面或双曲空间）的技术。这种归纳偏置帮助模型学习更有意义、更结构化的表示，与数据的内在几何结构更加一致。

此列表按照使用的几何先验类型进行组织。欢迎贡献！

## 目录

- [1. 双曲 VAE (Hyperbolic VAEs)](#1-双曲-vae-hyperbolic-vaes)
- [2. 超球面 VAE (Hyperspherical VAEs)](#2-超球面-vae-hyperspherical-vaes)
- [3. 通用流形 VAE (General Manifold VAEs)](#3-通用流形-vae-general-manifold-vaes)
- [4. 相关资源 (Related Resources)](#4-相关资源-related-resources)
- [5. 贡献 (Contributing)](#5-贡献-contributing)

---

## 1. 双曲 VAE (Hyperbolic VAEs)

- **核心思想**: 将潜在空间建模为具有负曲率的双曲空间。由于双曲空间的体积随半径呈指数增长，它能以极高的效率嵌入树状或层次化结构。
- **优势**: 高效嵌入层次结构，提供连续的层级表示，避免叶子节点在嵌入空间中"拥挤"。
- **适用场景**: **树状结构、层次化数据** (如文本分类、社交网络、生物信息学、代码结构分析等)。

### 相关论文 (Papers)

- **[Continuous hierarchical representations with poincare variational autoencoders](https://arxiv.org/pdf/1901.06033.pdf)**. *Emile Mathieu, Charline Le Lan, Chris Maddison, Ryota Tomioka*. (NeurIPS 2019). [[Code]](https://github.com/emilemathieu/pvae)
- **[Latent variable modelling with hyperbolic nomalizing flows](https://arxiv.org/pdf/2002.06336.pdf)**. *Avishek Joey Bose, Ariella Smofsky, Lingkai Kung, et al*. (ICML 2020).
- **[A wrapped normal distribution on hyperbolic space for gradient-based learning](https://arxiv.org/pdf/1902.02992.pdf)**. *Yuki Nagano, Ryo Yamaguchi, Yasuhiro Fujita, Kento Koyama*. (ICML 2019).

---

## 2. 超球面 VAE (Hyperspherical VAEs)

- **核心思想**: 将潜在空间约束在单位超球面上，强制所有潜在向量的L2范数为1。模型学习的是数据的"方向性"而非"大小"。这通常通过冯·米塞斯-费舍尔(vMF)分布实现。
- **优势**: 关注方向而非长度，有效缓解后验坍塌问题，天然适合处理方向性数据。
- **适用场景**: **方向性、角度关系重要的数据** (如文本（词嵌入）、基因表达谱、图像风格等)。

### 相关论文 (Papers)

- **[Hyperspherical variational auto-encoders](https://arxiv.org/pdf/1804.00891.pdf)**. *Tim R. Davidson, Luca Falorsi, Nicola De Cao, Thomas Kipf, Jakub M. Tomczak*. (NeurIPS 2018). [[Code]](https://github.com/nicola-decao/s-vae-pytorch)
- **[Spherical Latent Spaces for stable variational autoencoders](https://arxiv.org/pdf/1808.10805.pdf)**. *Jiacheng Xu, Greg Durrett*. (EMNLP 2018). [[Code]](https://github.com/jiacheng-xu/vmf_vae_nlp)
- **[Disentanglement with hyperspherical latent spaces using diffusion variational autoencoders](https://openreview.net/pdf?id=SylFDSU6Sr)**. *Daniel Hain, Chris Williams, et al*. (NeurIPS 2019 Workshop).

---

## 3. 通用流形 VAE (General Manifold VAEs)

- **核心思想**: 不预设特定的几何形状，而是假设潜在空间是一个通用的、弯曲的黎曼流形。模型的目标是从数据中直接学习这个流形的内在几何结构。
- **优势**: 灵活性高，能捕捉复杂的内在结构，沿着流形测地线的插值可以生成更平滑、更真实的过渡样本。
- **适用场景**: **具有连续、非线性变化的复杂数据** (如物理系统模拟、机器人运动、物体姿态变化、医学影像中的疾病演化)。

### 相关论文 (Papers)

- **[Variational autoencoders with Riemannian brownian motion priors](https://arxiv.org/pdf/2002.05227.pdf)**. *Dimitris Kalatzis, David Eklund, Georgios Arvanitidis, Søren Hauberg*. (ICML 2020).
- **[Geometrically enriched latent spaces](https://arxiv.org/pdf/2008.00565.pdf)**. *Georgios Arvanitidis, Søren Hauberg, Bernhard Schölkopf*. (ICML 2020 Workshop).
- **[Data Generation in Low Sample Size Setting Using Manifold Sampling and a Geometry-Aware VAE](https://arxiv.org/pdf/2103.13751.pdf)**. *Clément Chadebec, Stéphanie Allassonnière*. (MICCAI 2021).

---

## 4. 相关资源 (Related Resources)

- **[Blog] [Normalizing Flows Tutorial, Part 1: Distributions and Determinants](https://blog.evjang.com/2018/01/nf1.html)**: Eric Jang的出色介绍，涵盖了流模型背后的概念，这些概念经常与GeoVAEs一起使用。
- **[Tutorial] [An Introduction to Variational Autoencoders](https://arxiv.org/abs/1906.02691)**: Kingma和Welling的基础性文章。
- **[GitHub] [Awesome-VAEs](https://github.com/matthewvowels1/Awesome-VAEs)**: 涵盖所有类型VAE的父列表。

---

## 5. 贡献 (Contributing)

欢迎贡献！请先阅读[贡献指南](CONTRIBUTING.md)。

如果您有任何建议或发现应该包含的论文，请随时打开一个Issue或提交Pull Request。
