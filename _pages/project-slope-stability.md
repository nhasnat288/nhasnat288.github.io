---
layout: archive
title: "Physically Admissible Slope-Stability Prediction Using Bayesian Physics-Informed Neural Networks"
permalink: /research-projects/slope-stability/
author_profile: true
---

[← Back to Research Projects](/research-projects/)

---

## Research in Brief

I was teaching slope stability and foundations while reading data-driven papers in the same area, and a lot of those models gave confident answers that contradicted what I'd taught that same week. A network can fit a slope database well and still say that a slope gets safer as it gets taller. That is the problem this work is about.

I put together a database of 275 circular-failure slope cases from fourteen published sources, threw out the physically inconsistent and duplicate entries, and locked 55 cases away as a test set I don't touch. Then I automated 3,000 PLAXIS 2D strength-reduction runs through the Python remote-scripting API — fixing arc-length control and mode-dependency faults along the way — and used 2,000 of them to pretrain the network.

The model is a Bayesian physics-informed network with hard monotonicity constraints on six governing parameters. The constraint sits in the architecture, not in the loss function, so every posterior draw respects it and there is no weight to tune. Tuned classical baselines — random forest, SVM, ANN, BNN — score slightly higher on cross-validated accuracy. All of them violate monotonicity. This one cannot, including outside its training range. Pretraining on the FEM data improved cross-validated accuracy in all five folds.

**Status:** Manuscript in preparation. Joint first-author work with R. A. Nishat. [[CONFIRM: preferred name format for the co-author]]

---

## Key Findings

- The B-PINN achieves **zero monotonicity violations** across all parameter responses, while conventional baselines violate monotonicity in **19–31%** of out-of-range parameter sweeps
- McNemar's exact test separates **none of the 15 model pairs** at the 5% level — accuracy alone cannot discriminate among the models
- A König/min-cut bound reveals that label conflicts in the database cap any monotone classifier at **0.946 accuracy**
- SHAP analysis of the unconstrained BNN shows it assigns **lower failure probability to higher pore pressure** (Spearman ρ = −0.90), a physically inadmissible pattern
- In an 88,200-point design chart, the unconstrained network predicts decreasing failure probability with increasing slope height across **46% of the domain**; the B-PINN cannot produce such violations

---

## Experimental Analysis

<div style="margin-bottom: 30px;">
<h3>Parameter-Space Coverage</h3>
<p>Distribution comparison between the FEM-generated synthetic dataset (2,000 simulations) and the 275 field case histories across six input parameters: height, slope angle, unit weight, cohesion, friction angle, and pore-pressure ratio. The synthetic data provides broader coverage to support pre-training, while the field cases concentrate on ranges commonly encountered in practice.</p>
<img src="/images/research-projects/Slope%20Stability_FEM%20Data.png" alt="Parameter-space coverage: synthetic vs reference cases" style="max-width: 100%; border: 1px solid #ddd; border-radius: 4px; padding: 4px;">
<p style="text-align: center; font-style: italic; color: #666; font-size: 0.9em;">Figure: Parameter-space coverage — synthetic (FEM-generated) vs. reference field cases</p>
</div>

<div style="margin-bottom: 30px;">
<h3>Physical Consistency of Candidate Models</h3>
<p>(a) Heatmap of monotonicity violations broken down by input parameter and model — darker shading indicates more frequent violations. The B-PINN columns show dashes (no violations possible by construction). (b) Overall monotonicity violation measure on a relative scale, confirming that the B-PINN (both base and pre-trained variants) records zero violations while all conventional baselines exhibit worst-case violations.</p>
<img src="/images/research-projects/Slope%20Stability_Physical%20Consistancy.png" alt="Physical consistency of candidate models" style="max-width: 100%; border: 1px solid #ddd; border-radius: 4px; padding: 4px;">
