---
layout: page
title: Training and Visualising Degeneration Apertus Probes
description: Token-level probes to detect and steer generation degeneration in a LoRA-adapted LLM.
importance: 2
category: research
related_publications: false
authors:
  - Lorenzo Baggi
  - Marco De Negri
  - Moritz Reihs
  - Luca Sartori
more_authors:
  - Eduard Durech
  - Anna Hedström
  - Valentina Pyatkin
group: ETH AI Center, Apertus Group
period: Spring 2026 – present
---

*This page is still a work in progress — for now it's just a quick summary of the project.*

**ETH AI Center, Apertus group** — Spring 2026 – present

Built a token-level degeneration probe on LoRA-adapted Apertus-8B-Instruct hidden states, trained on 83K labelled completions via a sliding-window repetition score, reaching 0.92 F1 (99.9% recall) at flagging degenerating tokens before generation visibly collapses; project carried out in collaboration with Anna Hedström, Valentina Pyatkin, and Eduard Durech (ETH AI Center / IVIA Lab).

Found via PCA that LoRA adaptation makes degenerate and healthy tokens more linearly separable, and used the probe to steer generations toward safe regions and trigger early stopping during training, cutting wasted RL/SFT compute. Built an interactive dashboard for diagnostics, with training and inference run on the Alps supercomputer (CSCS).
