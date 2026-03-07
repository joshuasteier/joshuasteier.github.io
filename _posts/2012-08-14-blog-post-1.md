---
title: "When Is a Learned Signal Trustworthy?"
date: 2026-03-07
permalink: /posts/2026/03/learned-signal-trustworthy/
tags:
  - research
  - machine learning
  - representation learning
  - inference
---

Last month I put three papers on arXiv in the same week. One is about atomistic foundation models. One is about reinforcement learning theory. One is about training dynamics in Forward-Forward networks. On the surface, these have nothing to do with each other.

But they are all asking the same question: **when should you trust what a model has learned?**

This post is my attempt to make that connection explicit — not as a grand theory, but as a working observation about what keeps showing up across my research.

## The finding that made the pattern click

In [*Information Routing in Atomistic Foundation Models*](https://arxiv.org/abs/2603.03155), I developed a decomposition method called Composition Projection Decomposition (CPD) to figure out what atomistic neural networks actually encode in their internal representations. These are models like MACE, SchNet, DimeNet++, and ANI-2x that predict molecular energies and forces — they're becoming foundational tools in chemistry and materials science.

The headline result: **different architectures route compositional information in fundamentally different ways, and this determines what you can extract from them downstream.**

MACE, which uses higher-order equivariant message passing, initially *destroys* compositional information in its intermediate layers — then recovers it in the final descriptor layer. ANI-2x does something stranger: its representations are linearly *anti-correlated* with composition under mean pooling, but this flips to positive correlation under sum pooling. The pooling operation — a seemingly minor architectural choice — completely changes what the representation "means."

I built an open-source library, [MatScope](https://pypi.org/project/matscope/), to make this kind of analysis reproducible.

What struck me was not just the result itself but how familiar the underlying problem felt. The question "is this signal real or is it an artifact of how you're looking?" is exactly what I keep running into in completely different domains.

## The same question, wearing different clothes

**In reinforcement learning:** My [PAC-RL survey](https://arxiv.org/abs/2501.17457) introduces a framework called Coverage–Structure–Objective (CSO) for organizing the theoretical RL literature. The core issue is: when can you trust that an offline RL policy will actually work? The answer depends on coverage assumptions (did your data see enough of the state space?), structural assumptions (how complex is the MDP?), and the objective (what are you even optimizing?). Change any of these and a "reliable" policy guarantee can evaporate. The signal — this policy works — is contingent on assumptions that are rarely stated clearly.

**In epidemiology:** In my [TND-MultiRenewal preprint](https://www.medrxiv.org/content/10.1101/2025.12.23.25328608v1), I model whether apparent interference between RSV, influenza, and COVID-19 is real biological interaction or an artifact of shared testing propensity. When the same population gets tested for multiple pathogens simultaneously, you can observe apparent negative correlation that has nothing to do with the viruses actually interfering with each other. The observation process creates a phantom signal.

**In training dynamics:** My [CFF paper](https://arxiv.org/abs/2603.01966) studies what happens when you clamp logit margins during contrastive Forward-Forward training. Margin clamping changes gradient variance, and whether this helps or hurts depends on the interaction between dataset difficulty, network width, and the margin threshold. A training signal that looks stabilizing in one configuration becomes destabilizing in another.

## The pattern

Each of these projects discovers that **a signal which appears meaningful under one set of assumptions becomes unreliable or inverts under another.** The specific mechanism differs:

- In CPD, it's the pooling operation and message-passing architecture
- In PAC-RL, it's coverage and structural complexity
- In TND, it's shared observation propensity
- In CFF, it's the interaction of margin threshold with network capacity

But the abstract structure is the same. There's a true underlying quantity. There's a projection — an observation process, an architectural choice, a data collection mechanism — that transforms it. And the question is whether what comes out the other side still faithfully represents what went in.

## What I think is going on (and what I don't yet know)

I suspect there's a formal connection here through projection operators. Coarse-graining a physical system, pooling neural network activations, and filtering epidemiological observations through a biased testing process are all projections that can introduce memory, create spurious correlations, and destroy or rearrange information. The Nakajima-Zwanzig formalism from statistical mechanics describes exactly this phenomenon in the physical setting. Whether that formalism extends cleanly to the ML and inference settings is an open question I'm actively thinking about.

I'm not claiming a unified theory. I'm claiming a unified *question*: given a projection from a high-dimensional system to an observed quantity, what conditions determine whether the observed signal is trustworthy?

## What's next

The immediate priority is strengthening the CPD paper for NeurIPS 2026 — adding the MACE-on-QM9 ablation that isolates pretraining effects from architecture effects, and expanding the cross-domain transfer analysis. The companion library [MatScope](https://github.com/joshuasteier/matscope) is on PyPI and I'm actively developing it.

Beyond that, I'm working within the [PyHealth](https://github.com/sunlabuiuc/PyHealth) ecosystem as a maintainer, building graph-based clinical ML tools that face their own version of the same question: when can you trust a prediction made from messy, incomplete health records?

If the projection-operator connection turns out to be more than metaphorical — if there's a real theorem linking these settings — that becomes a longer paper. But first, branches. Then trunk.

## Papers referenced

- **CPD:** J. Steier, [*Information Routing in Atomistic Foundation Models via Composition Projection Decomposition*](https://arxiv.org/abs/2603.03155), arXiv 2026.
- **PAC-RL:** J. Steier, [*A Survey of PAC-Guaranteed Reinforcement Learning*](https://arxiv.org/abs/2501.17457), arXiv 2026.
- **CFF:** J. Steier, [*Contrastive Forward-Forward with Margin Clamping*](https://arxiv.org/abs/2603.01966), arXiv 2026.
- **TND:** J. Steier, [*Disentangling Biological Interference from Shared Testing Propensity*](https://www.medrxiv.org/content/10.1101/2025.12.23.25328608v1), medRxiv 2025.
- **MatScope:** [pypi.org/project/matscope](https://pypi.org/project/matscope/) | [github.com/joshuasteier/matscope](https://github.com/joshuasteier/matscope)
