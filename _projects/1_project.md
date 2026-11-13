---
layout: page
title: Conditionally Independent Diffusion (CID) model
description:
img: assets/img/CID_streamlitapp_demo_image.png
importance: 1
category: Econometrics
---

This project explores conditional independence through an interactive simulation of a Gaussian factor model. Built with Python, Streamlit, and Plotly, the application demonstrates how a shared market factor and individual random components determine the behavior of two modeled variables.

The model takes the form:

$$
X_i = aM + \sqrt{1-a^2}\,Z_i
$$

Here, \(M\) represents the common market factor, \(a\) controls exposure to that factor, and \(Z_i\) represents an independent, standard normally distributed component specific to each variable.

The central concept is **conditional independence**: variables can share exposure to a common source of uncertainty while remaining independent once that common factor is held fixed. This distinction is relevant to financial risk modeling, where systematic factors affect multiple assets or borrowers alongside their individual sources of risk.

The interactive dashboard allows users to:

- Adjust the simulation sample size.
- Change the factor loading and market-factor scenario.
- Examine the simulated outcomes through an interactive scatter plot.
- Calculate the sample correlation between the two variables.
- Generate new samples to observe simulation variability.

In this implementation, the market factor is held fixed within each simulation. The resulting plot therefore represents a **conditional distribution**: changing the market scenario shifts the distribution’s center, while changing the factor loading affects its dispersion. The two variables remain conditionally independent, so their sample correlation generally fluctuates around zero when their variances are nonzero.

The project combines statistical modeling, numerical simulation, and interactive visualization to make the relationship between common factors and conditional independence easier to explore.

**Technologies:** Python, NumPy, SciPy, pandas, Streamlit, and Plotly.

[View the source code on GitHub](https://github.com/Davidworkstation/Conditionally_Independant_Correlation_CID)

<div class="row justify-content-sm-center">
    <div>
        {% include figure.liquid path="assets/img/CID_subplots.jpg" title="CID Subplots" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
