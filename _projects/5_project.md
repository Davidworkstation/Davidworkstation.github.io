---
layout: page
title: One-Factor Gaussian Copula
description: 
img: assets/img/OFGC_Dashboard_Preview.png
importance: 1
category: Econometrics
---

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/OFGC_Dashboard_Preview.png" title="Dashboard" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

This project explores credit risk through an interactive **one-factor Gaussian copula simulation**, built with **Python and Streamlit**. The dashboard illustrates how a common market factor, borrower-specific randomness, and hazard rates contribute to modeled default times.

The one-factor framework separates credit risk into two components:

- **Systematic risk:** exposure to a common factor affecting multiple borrowers.
- **Idiosyncratic risk:** uncertainty specific to each borrower.

In a Gaussian factor model, shared exposure creates dependence across borrowers when the market factor varies. Conditional on a fixed market-factor realization, the borrower-specific random components remain independent. This structure provides a tractable foundation for investigating default dependence.

The dashboard presents the simulation’s intermediate calculations, including individual stochastic draws, transformed factor values, probability-scale values, survival thresholds, and estimated times to default. Hazard rates govern the default-time distribution, with higher rates corresponding to shorter expected survival under a constant-hazard assumption.

Users can adjust the simulation size, market-factor scenario, and hazard-rate configuration. Histograms summarize the generated stochastic values, survival thresholds, and default times, while a detailed table makes the calculation sequence easier to inspect.

By pairing numerical outputs with interactive visualizations, the application makes the mechanics of credit-risk simulation more accessible. It demonstrates how probabilistic assumptions translate into default-time scenarios and provides a foundation for further exploration of portfolio credit risk.

**Technologies:** Python and Streamlit.
