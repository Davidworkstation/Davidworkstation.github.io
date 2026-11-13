---
layout: page
title: Brownian Motions
description: 
img: assets/img/GBM_noylims.png
importance: 3
category: work
---

This project explores stock price dynamics through **Geometric Brownian Motion (GBM)**, a stochastic model widely used in financial mathematics. By generating and plotting multiple simulated price paths, it illustrates how drift and volatility combine to produce different outcomes from the same starting conditions.

GBM models the evolution of an asset’s price using the stochastic differential equation:

$$
dS_t = \mu S_t\,dt + \sigma S_t\,dW_t
$$

Here, \(S_t\) is the asset price, \(\mu\) is the drift parameter, \(\sigma\) is volatility, and \(W_t\) is a standard Wiener process. The drift governs the expected rate of price growth, while the stochastic component introduces random fluctuations.

Under constant drift and volatility, GBM produces normally distributed log returns and lognormally distributed prices. Starting from a positive price, its paths remain positive and continuous.

The visualization compares multiple simulated trajectories over time. Although each path follows the same underlying assumptions, accumulated random shocks can produce substantially different outcomes. Some paths remain relatively subdued, while others experience pronounced growth, illustrating the asymmetry of the lognormal price distribution and the effects of compounding.

GBM also provides the underlying stock-price dynamics in the classical Black–Scholes–Merton option pricing framework. Its tractability makes it a useful starting point for studying financial uncertainty, Monte Carlo simulation, and derivatives valuation.

These simulations represent possible outcomes under a specified model rather than forecasts of individual stock prices. Constant volatility and continuous paths are simplifying assumptions; real markets can exhibit changing volatility and sudden price jumps.

This project connects stochastic modeling with visual analysis, making the effects of randomness, compounding, and model assumptions easier to examine.
