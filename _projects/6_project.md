---
layout: page
title: Regression Forecasting
description: Regression Forecasting on JP Morgan Cash Flow Data
img: assets/img/JPMorgan_Regression_Dashboard_Preview.png
importance: 2
category: Econometrics
---

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/assets/img/JPMorgan_Regression_Dashboard_Preview.png" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

This project explores trends in **JPMorgan Chase’s historical cash-flow data** through an interactive polynomial regression dashboard. Built with **Python and Streamlit**, it allows users to compare how different polynomial degrees represent the same financial time series.

The project combines data collection, preparation, modeling, and visualization. A web-scraping script uses Selenium and Beautiful Soup to extract quarterly cash-flow statement data from Macrotrends, which is organized into a CSV dataset for analysis.

Within the dashboard, users can select a cash-flow statement variable and compare **four independently adjustable polynomial fits** side by side. Each chart overlays the observed values with a fitted curve, making differences between model specifications easy to inspect.

Polynomial regression approximates the selected series as a function of time:

$$
y_t = \beta_0 + \beta_1t + \beta_2t^2 + \cdots + \beta_dt^d + \varepsilon_t
$$

The degree \(d\) determines the model’s flexibility. Lower-degree polynomials summarize broad movements, while higher-degree polynomials can follow more detailed fluctuations. The application uses NumPy’s least-squares polynomial fitting functions to estimate these curves.

A central focus is the **tradeoff between model complexity and overfitting**. A curve that closely follows historical observations may also capture noise or isolated movements, limiting its usefulness beyond the observed period. The dashboard supports exploratory, in-sample comparison; it does not establish forecasting accuracy.

This project demonstrates a workflow for turning financial statement data into an interactive analytical tool, connecting web scraping and data preparation with regression modeling and visual interpretation.

**Technologies:** Python, Streamlit, NumPy, pandas, Plotly, Selenium, and Beautiful Soup.

[View the source code on GitHub](https://github.com/Davidworkstation/JPMorgan_CashFlow_PolynomialRegression)
