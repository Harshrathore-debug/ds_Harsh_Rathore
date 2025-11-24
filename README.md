Comprehensive Technical Report: Correlation Between Trader PnL and External Market Sentiment

1. Introduction and Project Mandate

1.1 Project Objective

The primary objective of this quantitative study is to investigate and quantify the relationship between a single algorithmic or high-frequency trader's realized daily Profit and Loss (PnL) and the contemporaneous state of the broader market, as measured by a quantitative Market Sentiment Index (specifically, the Fear & Greed Index).

1.2 Core Hypothesis

The analysis operates under the hypothesis that a trader's performance, risk-taking behavior, and overall trading efficiency are systematically influenced by the prevailing market sentiment. Specifically, we aim to answer:

Are periods of extreme market sentiment (Fear or Greed) correlated with statistically different PnL outcomes?

Does the trader become more or less risk-averse (by adjusting leverage or capital size) in response to high market euphoria (Greed)?

Can we identify a specific sentiment state where the trader’s risk-adjusted performance (efficiency) is maximized?

1.3 Scope and Limitations

This report documents the methodology and structure of the analysis pipeline. While the current merged dataset contains a limited number of daily observations ($N=4$), the methodology is designed to scale with a larger, continuous dataset. Conclusions regarding statistical significance and long-term correlations are currently limited by this small sample size. Reliance on a synthetic leverage value (5.0x) due to missing raw data also means conclusions regarding the trader’s active risk-taking behavior are preliminary.

2. Data Acquisition and Engineering

The analysis relies on two distinct datasets: high-frequency trading data and daily sentiment data. The process requires cleaning and standardization before merging.

2.1 Date Aggregation and Synchronization

Synchronization is achieved by converting the precise time of each trade to a common date key. The final merged dataset (df_merged) is created by an inner join on the common date key.

$$DF_{\text{Merged}} = DF_{\text{Trader Metrics}}^{\text{Daily}} \cap DF_{\text{Sentiment}}^{\text{Daily}}$$

3. Feature Engineering and Trading Metrics

The analysis moves beyond simple PnL to include metrics characterizing the quality and efficiency of the trader’s decisions.

3.2 Engineered Metrics for Performance Evaluation

3.2.1 Trading Quality: Win Rate (%)

Win Rate measures the percentage of profitable trades.

$$\text{Win Rate} = \frac{\text{Total Wins}}{\text{Total Trades}} \times 100$$

3.2.2 Trading Efficiency: Risk-Adjusted PnL Score

This metric measures the return achieved relative to the volatility of that return (risk).

$$\text{Risk-Adjusted PnL Score} = \frac{\text{Average Daily Closed PnL}}{\text{Standard Deviation of Daily PnL}}$$

4. Quantitative Results and Discussion (The 8-Step EDA)

The analysis pipeline generates eight visualizations and statistical outputs for exploratory data analysis (EDA). Key areas include:

Daily PnL Distribution by Market Sentiment (Boxplot)

Average Leverage Used by Sentiment (Bar Plot)

Statistical T-Test: Pessimism vs. Optimism PnL (Bar Chart)

Linear Relationship: Daily PnL vs. Numerical Sentiment Index (Regression Analysis)

5. Strategic Recommendations and Path Forward

5.1 Formalizing the Strategic Recommendation

The analysis is designed to yield clear, actionable strategic advice based on the observed correlation:

Observed Correlation

Strategic Recommendation

Risk Management Focus

Negative (Contrarian)

Maximize Exposure during Extreme Fear.

Monitor Panic Selling.

Positive (Pro-Cyclical)

Restrict Risk during Extreme Greed.

Drawdown Protection.

5.2 Next Steps for Analysis Improvement

Massively Increase Data Volume ($N > 30$ Days).

Integrate Real-Time Leverage Data.

Analyze Directional Bias (Long vs. Short).

6. Appendix: Methodology Summary

The technical analysis is underpinned by a modular Python script.

Script Section

Purpose

Key Output

Section 1

Setup & Data Loading

Standardized raw DataFrames

Section 2

Data Cleaning & Preprocessing

Daily & Trade-Level Aggregates

Section 3

Feature Engineering & Aggregation

df_merged dataset with engineered metrics

Section 4

Comparative Analysis (8 EDA Steps)

Visualizations and Statistical Results
