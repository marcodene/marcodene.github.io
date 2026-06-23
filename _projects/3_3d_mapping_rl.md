---
layout: page
title: Goal-driven 3D Map Generation with Reinforcement Learning
description: An RL agent that dynamically allocates resolution in a 3D map under a tight memory budget.
importance: 3
category: research
related_publications: false
authors:
  - Lorenzo Baggi
  - Marco De Negri
  - Vassili De Palma
  - Alessio Salvatore
more_authors:
  - Daniel Barath
  - Jelena Trisovic
group: Computer Vision and Geometry Lab, ETH Zürich
period: Spring 2026
website: https://marcodene.github.io/3dv.github.io/
---

*This page is still a work in progress — for now it's just a quick summary of the project.*

**Computer Vision and Geometry Lab, ETH Zürich** (Daniel Barath) — Spring 2026

Trained an RL agent using PPO to dynamically allocate resolution in a 3D map, learning to keep high detail in regions relevant to the task at hand while compressing the rest, under a tight memory budget.

Built a Python library for 3D maps with online adaptive resolution (incremental delta-buffer updates, raycasting-based false-obstacle pruning) and integrated it with the PEANUT navigation agent in the AI Habitat simulator, cutting memory usage by 88.6% in test episodes while maintaining task success.
