---
title: "Uncertainty-Aware Bayesian Physics-Informed Neural Network for Probabilistic Slope Stability Classification"
collection: publications
category: in_preparation
permalink: /publication/2026-bpinn-slope-stability
excerpt: 'A Bayesian physics-informed network with hard monotonicity constraints on six governing parameters, pretrained on automated PLAXIS 2D strength-reduction runs and fine-tuned on audited field case histories.'
date: 2026-01-01
venue: 'Manuscript in preparation'
citation: 'Nishat, R. A.&dagger;, &amp; <b>Hasnat, N.</b>&dagger;* &quot;Uncertainty-Aware Bayesian Physics-Informed Neural Network for Probabilistic Slope Stability Classification.&quot; Manuscript in preparation. (&dagger; joint first authors; * corresponding author)'
status: 'In preparation'
project: '/research-projects/slope-stability/'
role: 'Joint first and corresponding author. Built the case database, automated the PLAXIS 2D campaign and developed the model.'
---

A slope-stability classifier that cannot contradict the mechanics it is meant to represent. Monotonicity with respect to six governing parameters is enforced in the architecture rather than through a training penalty, so every posterior draw respects it, including outside the training range. The network is pretrained on 2,000 of 3,000 automated PLAXIS 2D strength-reduction runs and fine-tuned on a screened database of 275 published circular-failure cases, with 55 held back as a locked test set. Pretraining improved cross-validated accuracy in all five folds.

Joint first-author work with R. A. Nishat. **Status:** manuscript in preparation.

More detail on the [project page](/research-projects/slope-stability/).
