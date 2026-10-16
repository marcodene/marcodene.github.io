---
layout: page
title: Degeneration Detection Is Not Early Warning
description: Linear probes on LLM hidden states that warn, token by token, before a model falls into a repetitive loop. Accepted at the NeurIPS 2026 Workshop on Interpretability as a Science.
importance: 1
category: research
related_publications: false
authors:
  - Marco De Negri
  - Luca Sartori
  - Lorenzo Baggi
  - Moritz Reihs
more_authors:
  - Eduard F. Ďurech
  - Mennatallah El-Assady
  - Valentina Pyatkin
  - Anna Hedström
group: ETH AI Center, Apertus Group
period: Spring 2026
# pdf: https://arxiv.org/abs/XXXX.XXXXX  # TODO: add once the arXiv preprint is out
---

_This page is still a work in progress — for now it's just a quick summary of the project._

**ETH AI Center, Apertus group** — Spring 2026 · Accepted at the NeurIPS 2026 Workshop: Interpretability as a Science

Trained linear probes on the hidden states of Apertus-8B, Llama-3.1-8B and Mistral-7B to warn, token by token, that a model is about to fall into a repetitive loop, before it shows in the text.

Proposed ONWARD, an evaluation that fixes the false-alarm rate on healthy responses and scores alarms against a human-verified failure onset. Showed that AUROC saturates on this task and cannot tell an early warning from a late detection, and that LoRA adaptation below the probe more than doubles warning coverage on all three models. All experiments run on the Alps supercomputer (CSCS).
