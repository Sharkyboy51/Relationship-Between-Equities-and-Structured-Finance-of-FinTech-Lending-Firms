
# Equities and Structured Finance of FinTech Lending Firms - A Quantitative Research and Trading Strategy

For the full research paper and more info, please email me: eyal.beneliyahu@gmail.com 

This quantitative finance research project measures the connection of two completely different financial assets, which are connected and sourcing their value from the same firm. The firms are FinTech lending firms, such as Upstart (NASDAQ:UPST) and SoFi (NASDAQ:SOFI), and the related assets are their publicly traded equities and the ABSs (Asset Backed Securities) they have issued.

The fundamental hypothesis for the existenca of such a connection, is grounded in the imporatnce of the underwriting quality for the success of the ABS and the firm's equity. The quality of underwriting  has a direct effect on the financial performance of the ABS and to the equity value, since these firms' main revenue source, and "claim to fame", is derived from the level of accuracy and scalablility in issuaning new consumer loans.

This paper outlines an innovative research approach to ABS issuers' stocks and their ABSs' performance. Since these FinTech stocks and their ABSs are relatively young, and due to budget limitations, the data and timeframe are limited, but the same methodology and code can be applied  to a far more extensive data set. Forming this comparable pool of firms, using their ABSs performance for trading strategies, and using the firms' combined average return as the benchmark is applicable for further research.



## Data
5 publicly traded FinTech consumer lending firms:

Equities:
2021-11-30 to 2023-01-20
Using Adjusted_Closed from Yahoo Finance

ABS:
16 different ABSs.

NYSE:LC, 3 ABS 
NASDAQ:UPST, 4 ABS
NASDAQ:SOFI, 3 ABS
NASDAQ:OPRT, 3 ABS
NASDAQ:AFRM, 3 ABS

Avg 22, (min 5, max 33) months of performance per ABS.
ABS data consists of 51, monthly updated features.
Example can be seen in "ABS Cohorts source data example/UPST/21-1" folder.








## Research for Trading Strategy

Goal and design:

The main goal of the research is to measure the relationship between ABS performace to stock performace. In order to achieve that I use ABS features and performance on day (t) to predict stock's performance on (t+1). 

Variables:

After several trials and errors and deeper understading of the economical meaning of each feature, I used four independant variables (X) - Annualized_Net_Loss_Rate + Life_CDR + Life_CPR + Gross_Coupon_Minus_Annualized_Net_Loss_Rate. Where the dependant variable (Y) is adj_1_change, which is the adjusted closed value one day after the X values.

Prediction model:

After trying several prediction models, I've found the RandomForestRegressor(random_state=42, n_estimators=100), showed the best predictive results (tested by MAE - Mean Absolute Error).

Trading Strategy:

1. E-EW-L/S-1 - Event based, Equally weighted, Long/Short top/bottom 1.
2. D-EW-L/S-1 - Daily, Equally weighted, Long/Short top/bottom 1
3. Benchmark - Long all 5 equities.

Performance: 
1. E-EW-L/S-1: Tot Return: 0.229 | Annualized Return: 0.354 | Annualized Return Efficient: 15.307 | Volatility: 0.032 | Sharpe: 7.07 | # trades: 27 | Best Day: 0.097 | Worst Day -0.072
2. D-EW-L/S-1: Tot Return: -0.001 | Annualized Return: -0.002 | Annualized Return Efficient: -0.002 | Volatility: 0.034 | Sharpe: -0.043 | # trades: 249 | Best Day: 0.16 | Worst Day -0.114
3. Benchmark: Tot Return: -0.769 | Annualized Return: -0.883 | Annualized Return Efficient: -0.883 | Volatility: 0.051 | Sharpe: -15.06 | # trades: 249 | Best Day: 0.178 | Worst Day -0.152



