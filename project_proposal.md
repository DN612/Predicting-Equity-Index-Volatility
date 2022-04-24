
# Project Proposal

## What is our aim?
Financial markets have very complex structures that are highly nonlinear (stochastic) with a low signal-to-noise ratio which makes predicting short term asset returns difficult. However, it is well established in literature that volatility is easier to predict than returns. Factors like slow decay of autocorrelation in absolute returns tend to suggest that volatility is inherently more forecastable - this might imply the long time memory of the financial time series. Volatility is forecastable because of a number of persistent statistical properties, which we will discuss and elaborate on in our analysis. 

The aim of our project is to predict/forecast both weekly and daily realized volatility of the S&P 500 Index — we included daily volatility prediction in order to capture important events which may get muted when averaging out over a larger time frame (weekly). We plan to use different machine learning based volatility forecasting methods and evaluate the forecast accuracy which can be used to make meaningful investment decisions.

## What data are we using?
- We will be using 1 minute tick data for S&P 500 from Kaggle (https://www.kaggle.com/gratefuldata/intraday-stock-data-1-min-sp-500-200821). The data is from 22 January 2008 to 06 May 2021. This dataset covers the financial crisis of 2008 to 2009, the European sovereign debt crisis, Greece brankruptcy, several rounds of dispute about the U.S. debt ceiling, and the flash crashes of 6 May 2010 and 24 August 2015 as well as the recent Covid crisis in 2020 and the market evolution after it.

- The explanatory variables/features that we plan to explore can be broadly classified as:
  - **Macroeconomic variables**: 
    - **CBOE volatility (VIX) index**: The VIX Index, also known as the "Fear Index" is a guage of the next month's volatility based on options market. This feature has       high predictive power for the actual S&P 500 volatility.
    - **One/two different country stock index log returns**: The specific country index (to be included in the model) will be based on highest economic exposure of stocks included in the S&P 500 index. The rationale behind this is that many of the stocks in S&P 500 have large portions of their businesses depending on their manufacturing sites in other countries like China/Taiwan (especially for technology stocks). 
    - **the ADS Business Conditions index** (https://www.philadelphiafed.org/surveys-and-data/real-time-data-research/ads): This is an index designed to track real business conditions in the US which has real implications on the stock market performance and volatility.
    - **US 1-month T-bill rate**: The US Treasury rates have a huge impact on the real interest rates (lending/borrowing) and changes in the T-bill rates also have a large impact on the stock returns, which in turn affects the volatility of the S&P 500 returns.
    - **Economic Policy Uncertainty (EPU) index** (https://www.policyuncertainty.com/us_monthly.html): EPU denotes the contribution of government policy makers to the uncertainty regarding fiscal, regulatory, or monetary policy. We know that higher economic policy uncertainty leads to increases in stock volatility, which makes this a good predictor of future volatility.
    - **NBER based Recession Indicator** (https://fred.stlouisfed.org/series/USRECDM): Technically, recession is defined as a decline in GDP over two successive quarters. This boolean indicator helps us identify business cycles over time which in turn affects the stock market volatility.
  - **Volatility lag variables**: Past volatility might be a good indicator of future volatiliy. We plan to study the effects of using lagged variables for volatility since there are periods when we observe volatility clusers - which mean that past volatile periods may help predict next period volatility. For this, we will use the daily, weekly, and monthly lag of realized variance. 
  - **Index level variables**: 
    - **1-week index momentum**: Stock index momentum is also a good predictor of volatility - we will explore the effect on momentum on volatility when we perform exploratory data analysis.
    - **Dollar trading volume**: Daily traded volume of an ETF may also help us predict volatility of the stock market index. 
    - **Ex-dividend dates feature**: This would be a boolean indicator which represents 1 for dates on which dividends are announced for the S&P 500 ETFs.

We may also choose to include news sentiment data for the S&P 500 Index/ETF as an alternative dataset. This is a preliminary feature list based on our economic intuition and the variables are subject to change on further data analysis.
 
## Why is this important?
Market volatility is a crucial input in asset pricing, portfolio allocation, and risk management. Inaccurate volatility estimates can be damaging to financial institutions as it deprives them of funds for investing. In addition, market volatility and its impact on public confidence can have a significant effect on the
broader global economy, which makes it even more important to predict volatility in order to make sound investment decisions.

This has been especially important during recent times when volatility wrecked havoc in the stock market in March 2020 — thus, it makes sense to forecast the volatitlity so that we are able to predict future volatility indications and avoid drawdowns (large losses) to preserve capital. We believe that covering the multiple crisis periods (in the 2008-2020 period) will help us uncover trends in the volatility during turbulent times as well as normal times.

## How will Machine Learning help?
Conventional linear regression models fail to predict accurately when the input variables are strongly correlated or have a low signal-to-noise ratio, or when the underlying relationships are non-linear in nature. Machine Learning methods can deal with highly nonlinear structured data that often appear in financial markets. They can also extract valuable information from a large amount of data by looking at a broad feature space where linear regression models often fail to do so. Additionally, they are significantly resistant to a substantial amount of noise added to distort the original dataset, in contrast to the linear regression, which makes ML very useful in predicting patterns in volatiltiy. 

Therefore, we believe that machine learning models of varying complexities would give some meaningful insights on market index volatility prediction.

### References:
- https://econpapers.repec.org/paper/aahcreate/2021-03.htm
- https://www.bis.org/publ/confp01m.pdf
- http://wp.lancs.ac.uk/fofi2020/files/2020/04/FoFI-2020-055-Jiadong-Liu.pdf
- https://www.jstor.org/stable/2962246
- https://www.lazardassetmanagement.com/docs/-m0-/22430/predictingvolatility_lazardresearch_en.pdf
- https://arxiv.org/pdf/1002.0284.pdf
- https://www.uibk.ac.at/ibf/team/huberj/kirchlerhuber_jedc_final.pdf
- https://www.sciencedirect.com/science/article/pii/S1544612315000835
