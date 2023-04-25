# ![](https://ga-dash.s3.amazonaws.com/production/assets/logo-9f88ae6c9c3871690e33280fcf557f33.png) 


# Capstone Project: Predicting Stock Market Returns

### Overview

The stock market is notoriously hard to forecast due to its reflexivity between the actions of market participants and their perceptions. Strategies such as active value investing which have outperformed in the past have struggled to maintain their performance for well over a decade now as passive investing takes the lead. Momentum and quantitative trading strategies which worked under certain market regimes can find themselves struggling with capacity constraints, timing issues, and subject to nasty volatility skews, fat kurtosis tails, and huge margin calls. What works in one stock market may not work in another and what works now may not work in the future. Consequently, it has been empirically found that more than 90% of traders lose money in the long run and more than 90% of active managers do not outperform their benchmarks (the S&P500 index being chief among all) once all costs have been factored in.



### Problem Statement

All market participants want to make money. Even those who are in the market for hedging risk want to be overall profitable. To be profitable, one needs to be holding the right position (long or short) for the future state of the market. The problem is that the stock market cannot be easily forecast. The further the horizon, the more inaccurate forecasts nearly always are. Short-term forecasts can however be made with a reasonable amount of accuracy if the right tools are used.  

This project seeks to answer the question: Is it more profitable for a trading/investing strategy to predict the current market regime (bear or bull market) or predict the forward price returns in advance?

---

### Datasets

#### Provided Data

There are three groups of datasets included in the [`datasets`](./datasets/) folder for this project.

1. **SPY.csv** - Contains daily price data for the ETF since inception 1993-2023/1

2. [`regime_results`](./datasets/regime_results) - Contains the timeseries of regime predictions made under several models for backtesting 
  
3. [`backtest_results`](./datasets/backtest_results) - Contains backtest results made under several models for the period 2018-2023/1
                
  
---  
     

### Conclusions and Recommendations  

For more detailed analysis: full report available at [`Capstone Report`](./Capstone_Report.pdf)

Hidden Markov models proved to be reasonably capable of predicting current market regimes but underperformed considerably when trying to predict forward price returns.  

For the best alpha strategy, it is recommended to employ HMM models to predict the current market regime and not trade unnecessarily.  