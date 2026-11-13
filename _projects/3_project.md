---
layout: page
title: Exchange Options Pricing Model
description: 
img: assets/img/cora_vol1_vol2.jpg
importance: 3
category: Econometrics
---

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/cora_vol1_vol2.jpg" title="Cora vs Volatility 1 vs Volatility 2" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/gamma_s2_vol1_vol2.jpg" title="Gamma S2 vs Volatility 1 and Volatility 2" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/opt_price_correlation_stock_price.jpg" title="Options Price vs Correlation vs Stock Price" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

This project implements an interactive exchange option pricing model within the Black–Scholes–Merton framework, allowing users to explore how underlying asset prices, volatilities, and correlation affect an option’s value and risk sensitivities.

An exchange option gives the holder the right, but not the obligation, to exchange one asset for another at expiration.

The application calculates the option’s theoretical value and displays sensitivities to changes in the underlying inputs:

Delta: the first derivative of the option value with respect to each underlying asset’s price.

Gamma: the second derivative of the option value with respect to each underlying asset’s price, measuring the sensitivity of Delta.

Vega: the sensitivity of the option value to each underlying asset’s volatility.

Cora: the sensitivity of the option value to the correlation between the two underlying assets.

Gora: the second derivative of the option value with respect to correlation, measuring how Cora changes.

Correlation is particularly relevant to exchange options because their value depends on the relative performance of two assets. Together with the individual asset volatilities, it determines the effective volatility used in the pricing model.

The interactive interface allows users to adjust model inputs and visualize a selected output across two input dimensions using 3D surface plots. Examples include option value across stock price and correlation, and Gamma or Cora across the two underlying volatilities. These visualizations reveal nonlinear relationships that are difficult to assess from individual numerical outputs.

This project combines derivatives valuation, sensitivity analysis, and interactive visualization to make the behavior of a two-asset option easier to investigate.

For questions about the model or my other projects, feel free to connect with me on LinkedIn.
