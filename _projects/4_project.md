---
layout: page
title: Value at Risk Dashboard
description: 
img: assets/img/VaR_Dashboard.jpg
importance: 1
category: Econometrics
---

<div class="row justify-content-sm-center">
    <div>
        {% include figure.liquid path="assets/img/VaR_Dashboard.jpg" title="Dashboard" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

This project investigates how probability distribution assumptions affect estimates of financial loss and tail risk. Built with **Python and Dash**, the interactive dashboard combines distribution fitting, goodness-of-fit testing, and risk measurement in a single analytical interface.

The model compares five candidate distributions: **normal, lognormal, Weibull, exponential, and generalized Pareto**. By fitting different distributions to loss data, the application explores how alternative assumptions change the estimated likelihood and severity of large losses.

The dashboard reports two key risk measures:

- **Value at Risk (VaR):** the loss quantile at a specified confidence level, representing a threshold exceeded with a corresponding small probability.
- **Expected Shortfall (ES):** the average loss in the tail beyond that threshold for a continuous loss distribution, providing insight into the severity of extreme outcomes.

To evaluate distributional fit, the project incorporates **Kolmogorov–Smirnov, Anderson–Darling, and Cramér–von Mises** diagnostics. These assess discrepancies between the empirical and modeled distributions, with Anderson–Darling placing greater emphasis on the tails—a particularly relevant consideration in risk analysis.

The interface displays a loss histogram alongside fitted probability density curves and risk thresholds. Supporting tables present goodness-of-fit statistics and risk estimates for each distribution, allowing users to compare model behavior visually and numerically.

The example analysis uses simulated losses constructed from normal and exponential components. This provides a controlled setting for exploring how candidate distributions represent a loss process with different underlying characteristics.

A central focus is **model risk**: applying different distributional assumptions to the same data can produce materially different VaR and Expected Shortfall estimates. The dashboard makes those differences visible and supports evaluating statistical fit alongside the behavior of the loss distribution’s tail.

**Technologies:** Python and Dash.
