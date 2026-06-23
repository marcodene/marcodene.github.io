---
layout: page
title: Generative Antibody Design with Protein Language Models
description: Fine-tuning ESM2 with Direct Preference Optimization to generate higher-affinity antibody variants.
importance: 1
category: research
related_publications: false
authors:
  - Marco De Negri
  - Giovanni Guidarini
more_authors:
  - Andreas Krause
  - Scott Sussex
group: Learning & Adaptive Systems Group, ETH Zürich
period: Spring 2026 – present
---

*This page is still a work in progress — for now it's just a quick summary of the project.*

**Learning & Adaptive Systems Group, ETH Zürich** (Prof. Andreas Krause, Scott Sussex) — Spring 2026 – present

Turning ESM2, a masked protein language model, into a generative model for antibody design, fine-tuning on yeast-display binding data via Direct Preference Optimization (DPO) to generate higher-affinity CDR-H3 variants of the C05 broadly neutralizing anti-flu antibody.

Showed that evotuning (unsupervised fine-tuning on antibody sequence databases) gives a better starting point for DPO than the vanilla model, especially in the low-data regime, reaching a Spearman correlation of 0.65 between model scores and experimental binding on held-out test sets.

Generated novel antibody variants via both Gibbs sampling and beam search decoding; all training and inference run on the ETH Euler HPC cluster.
