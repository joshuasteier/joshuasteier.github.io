---
layout: archive
title: "Research"
permalink: /research/
author_profile: true
---

My research asks when learned or inferred signals are trustworthy. The answer usually depends on structural assumptions — coverage, architecture, observation process, confounding — that are rarely stated explicitly. I work across several domains, but the underlying question is the same.

## Structure of Learned Representations

How do model architectures organize information, and what determines whether that information is recoverable for downstream tasks?

- **J. Steier.** [Information Routing in Atomistic Foundation Models via Composition Projection Decomposition.](https://arxiv.org/abs/2603.03155) arXiv:2603.03155, 2026.
  - Developed CPD, a decomposition method revealing architecture-specific information routing in atomistic neural networks (MACE, SchNet, DimeNet++, ANI-2x). Found that pooling operations can invert the sign of compositional accessibility.
  - Code: [MatScope](https://github.com/joshuasteier/matscope) ([PyPI](https://pypi.org/project/matscope/))

## Learning Guarantees and Robustness

When can you trust that a learned policy or model will work under distribution shift, and what structural conditions determine the strength of guarantees?

- **J. Steier.** [A Survey of PAC-Guaranteed Reinforcement Learning.](https://arxiv.org/abs/2501.17457) arXiv:2501.17457, 2026.
  - Introduces the Coverage–Structure–Objective (CSO) framework for organizing the PAC-RL literature. Maps how coverage assumptions, MDP structure, and optimization objectives jointly determine sample complexity and policy reliability.

- **J. Steier.** [Contrastive Forward-Forward with Margin Clamping.](https://arxiv.org/abs/2603.01966) arXiv:2603.01966, 2026.
  - Studies how margin clamping changes gradient variance in biologically plausible learning. The effect depends on the interaction of margin threshold, network width, and dataset difficulty — a training signal that stabilizes in one configuration destabilizes in another.

- **J. Steier**, Hedgewald, E.V., Jacques, A., Hartnett, G., Menthe, L. *Understanding the Limits of Artificial Intelligence for Warfighters: Vol. 2.* RAND Corporation, 2022.

## Inference Under Confounding and Observation Bias

When observation processes distort the signal — shared testing propensity, biased sampling, coupled dynamics — what can actually be inferred?

- **J. Steier.** [Disentangling Biological Interference from Shared Testing Propensity in Multi-Pathogen Surveillance.](https://www.medrxiv.org/content/10.1101/2025.12.23.25328608v1) medRxiv, 2025. Under review at *PLOS Computational Biology*.
  - Models whether apparent RSV–COVID–influenza interference is real biology or an artifact of shared testing. Introduces a hierarchical renewal framework with a test-negative design observation layer.

## Networked System Structure

How does the structure of networks — mathematical, infrastructure, or strategic — determine resilience, equilibrium, and vulnerability?

- **J. Steier.** Ergodic Deviation–Robust Equilibrium under Mirror-Descent Learning in Finite Games. Under review at *ACM Transactions on Economics and Computation*.

- **J. Steier.** Directed Arborescences and Sandpile Groups in Block-Constant Multigraphs. Under review at *Journal of Algebraic Combinatorics*.

- **J. Steier.** Fibers and Gaps in Trailing Zeros of Factorials in Arbitrary Bases. Under review at *Integers*.

- **J. Steier**, Sytsma, T., Marrone, J.V., et al. *Technological and Economic Threats to the U.S. Financial System.* RAND Corporation, 2024.

## Physics

- **J. Steier.** Spectral Deformations in Near-Extremal Kerr Black Holes. Under review at *Classical and Quantum Gravity*.

- Sahiner, M.A., Vander Valk, R.J., **Steier, J.**, et al. Identification of structural phases in ferroelectric HfZrO₂ by DFT-assisted EXAFS analysis. *Applied Physics Letters* 118, 092903, 2021.

## Open-Source Software

- **[MatScope](https://github.com/joshuasteier/matscope)** — Python library for probing and decomposing representations in atomistic foundation models. Implements CPD with PyTorch Geometric backends (SchNet, DimeNet++, PaiNN, ANI-2x). [PyPI](https://pypi.org/project/matscope/).

- **[PyHealth](https://github.com/sunlabuiuc/PyHealth)** — Maintainer. Contributed the graph-based modeling module (PR #853), VisionEmbeddingModel, TimeImageProcessor, and multiple model migrations to PyHealth 2.0.

## Additional RAND Publications (2022–2024)

- Calengor, S., Katragadda, S.P., **Steier, J.** Adversarial Threats in Climate AI. *Proceedings of the AAAI Symposium Series*, 2(1), 46–53, 2024.
- Reports on cybersecurity risk, AI limitations for defense, financial system threats, and energy security. [Full list on RAND author page.](https://www.rand.org/about/people/s/steier_joshua.html)
