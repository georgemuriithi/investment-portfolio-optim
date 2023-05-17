# Investment Portfolio Optimization

<a href="https://github.com/georgemuriithi/investment-portfolio-optim/blob/main/LICENSE">
    <img alt="License" src="https://img.shields.io/github/license/georgemuriithi/investment-portfolio-optim.svg?color=blue&cachedrop">
</a>

An investment portfolio of stocks is created using Long Short-Term Memory (LSTM) stock price prediction and optimized weights. The performance of this portfolio is better compared to an equally weighted portfolio and a market capitalization-weighted portfolio.

<p align="center">
  <img src="https://user-images.githubusercontent.com/21691211/155658959-cfd8f6cf-2baa-4a6a-afa8-274e7eddb3fd.png">
</p>

***Disclaimer:** The LSTM model cannot be used to predict stock prices in real life, and this project cannot help an investor make investment decisions in the stock market. This is because the stock market is highly unpredictable. Prediction models do not work. In this project, the validation phase is used to test the model's performance. The purpose of the project is to implement Univariate Time-Series Prediction using LSTM.*

## Problem Description
The task is to create an investment portfolio from stocks that maximizes overall return.

### Data
**Top 30 U.S. companies by market capitalization** are used. The start time is **2009-12-31** and the end time is **2021-12-31.** AbbVie (ABBV), Meta (FB) and Tesla, Inc. (TSLA) are excluded because they were listed on the stock market after 2009-12-31.

The csv files and model states can be accessed from the *data* folder.

## <a href="https://github.com/georgemuriithi/investment-portfolio-optim/blob/main/Investment-Portfolio-Optimization.ipynb">Solution Approach</a>
<a href="https://colab.research.google.com/drive/1Rd7xhUgp3OQO5u-bGqIT4cb29zJvWeXG?usp=sharing">
    <img alt="Open In Colab" src="https://colab.research.google.com/assets/colab-badge.svg">
</a>

An investment portfolio of several stocks is created by making stock price predictions using an **LSTM Univariate Time-Series Prediction** model. Daily returns are then are computed from the predicted stock prices and used to get weights that maximize overall return. This is done using **SLSQP (Sequential Least SQuares Programming)** optimization.

To create the **features** of the LSTM model, a time step of **100 days** is used. This means that if we consider today's Adj Close price as the **response,** the features will be the Adj Close prices of the past 100 days.

LSTM model **parameters:**

- `input_size=1`
- `hidden_size=1`
- `num_layers=1`
- `batch_first=True`
- `num_classes=1`
- `learning_rate=0.001`
- `optimizer=Adam`
- `loss_function=MSELoss()`
- `num_epochs=10000`

***GPU** is leveraged.*
