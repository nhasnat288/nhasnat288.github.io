---
layout: archive
title: "Gradient-Boosted and Symbolic Regression Modelling of Desiccation Cracking"
permalink: /research-projects/desiccation-ml/
author_profile: true
---

[← Back to Research Projects](/research-projects/)

---

## <i class="fas fa-book-open"></i> Research in Brief

My lab work on cracking showed how much a given additive helped in one soil under one set of drying conditions. It didn't show which factors matter most across many soils, climates and treatments. That's what an engineer needs to know before picking a fix.

So I collected several hundred desiccation test results from published studies into one dataset. Each result includes the soil (clay content and plasticity), the drying conditions (temperature and humidity), how many wetting and drying cycles it went through, the drying stage, and the treatment. The treatments range from raw soil to fiber and bio-mineralization. I predict three things separately: crack ratio, average crack width and the number of crack segments.

There are two steps. First, boosted tree models learn the patterns as well as the data allows. Then symbolic regression turns what the models learned into short equations that anyone can use by hand or in a spreadsheet.

**Research Period:** June 2026 – Present &nbsp;|&nbsp; **Status:** Ongoing

---

## <i class="fas fa-diagram-project"></i> Methodology

1. **Collecting the data.** I gathered test results from published studies into one dataset and removed duplicate and repeated inputs.

2. **Training models.** I trained LightGBM, XGBoost and CatBoost, tuned each one with grid search and 5-fold cross-validation, and used a random forest as the baseline. The models handle drying stage and treatment type directly instead of splitting them into dummy columns. I only removed outliers or transformed the outputs when it actually improved accuracy.

3. **Testing.** I scored each crack measure on a held-out test set and kept the best model for each one.

4. **Finding what matters.** I used permutation and gain importance to see which inputs each crack measure depends on.

5. **Turning categories into numbers.** The best model gives each drying stage and treatment type a number, so they can go into an equation.

6. **Writing the equations.** Symbolic regression fits one equation per crack measure using only the most important inputs. A penalty keeps the equations short.

---

## <i class="fas fa-lightbulb"></i> Key Findings

- The boosted models beat the random forest for all three crack measures. No single model was best for all three.
- **Each crack measure has a different main driver.** The things that decide how much of the surface cracks are not the same as the ones that decide crack width or crack count. So a single "cracking" number hides a lot.
- For crack ratio, the equation is almost as accurate as the best model and much better than linear regression.
- Crack width and crack count are harder to fit with a short equation. This suggests they depend on the inputs in more complex ways.
- Treatment matters, but for most measures it matters less than the soil and the climate.

---

## <i class="fas fa-chart-line"></i> Analysis

<div style="margin-bottom: 30px;">
<h3>Equation Versus Model Accuracy</h3>
<p>How the equation and a plain linear regression compare with the best boosted model on the test set. For crack ratio, the equation is almost as accurate as the full model.</p>
<img src="/images/research-projects/Desiccation_ML_Relative_Accuracy.png" alt="Relative accuracy of boosted model, closed-form equation and linear regression" style="max-width: 100%; border: 1px solid var(--global-border-color); border-radius: 4px; padding: 4px;">
<p style="text-align: center; font-style: italic; color: var(--global-text-color-light); font-size: 0.9em;">Figure: Accuracy relative to the best gradient-boosted model, per crack measure</p>
</div>

<div style="margin-bottom: 30px;">
<h3>What Drives Each Crack Measure</h3>
<p>Which groups of inputs matter most for each crack measure, based on permutation importance. The main factor is different for each one.</p>
<img src="/images/research-projects/Desiccation_ML_Drivers.png" alt="Dominant, secondary and minor drivers of each crack measure" style="max-width: 100%; border: 1px solid var(--global-border-color); border-radius: 4px; padding: 4px;">
<p style="text-align: center; font-style: italic; color: var(--global-text-color-light); font-size: 0.9em;">Figure: Relative importance of each group of inputs, per crack measure</p>
</div>

---

## <i class="fas fa-route"></i> Why this matters

This builds on my lab work on cracking. Those studies measured how much fiber, fly ash and lime reduced cracking in haor embankment soil. This one asks which of those factors matter most when soil, climate and treatment all change, and gives the answer as equations you can use without running a model.

Related: [Mitigating desiccation-induced cracking with fiber reinforcement and fly ash](/research-projects/desiccation-cracking/) and [remediation of desiccation-ridden embankment soil using waste plastic fiber, fly ash and lime](/research-projects/embankment-soil/).
