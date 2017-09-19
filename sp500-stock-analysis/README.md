# S&P500 Stock Analysis: Return-Risk Performance vs Index

## Abstract
With the Kaggle dataset S&P 500 stock data and the yahoo finance webservice the yearly performances (return vs risk) of all the stocks on the S&P500 stock index are analysed.

The stocks that performed better than the index last year are identified as well as the stocks that have beaten the index more than twice over the past 5 years.

Linear regression over a period of  one year is applied to define the return (slope) and risk (stdev).

Ony 30 stocks out of the 500 stocks from the index performed better than the SP500 index for more than 2 years in the past 5 years.


## Motivation
Warren Buffett, the world’s most successful investor states that for ordinary people the best investment is buying the index instead of trying to pick successful stocks.

This analysis shows that Buffett is right and that the S&P500 is very difficult to beat year after year. 


## Datasets
* **Kaggle S&P 500 stock data**
5 years (2012-08-13 to 2017-08-11) of daily price information for all 500 stocks of the current S&P500 index (open, high, low, close, volume). 
A total of 606,801 observations
https://www.kaggle.com/camnugent/sandp500 all_stocks_5yr.csv
* **Yahoo finance** 
5 years of daily price information for the current S&P500 index (open, high, low, close, volume). 
A total of 1258 observations
https://finance.yahoo.com/quote/%5EGSPC%2C/history?p=%5EGSPC%2C


## Data Preparation and Cleaning
* Divide the data set into 5 equal periods of approx. 1 year each
* Put a multi index on the dataframe [Name, Date]
* Get the Yahoo data using pandas_datareader.get_data_yahoo
* Align the date range of the Yahoo data with the data from Kaggle
* Use pandas.concat to combine the Yahoo data with the Kaggle data

## Research Questions
* Which stocks performed better last year than the index, with higher return and lower risk?
* Which stocks performed better than the index (more than twice in the past 5 years)?

## Methods
* define function to calculate return / risk ratio for a particular year
* calculate return / risk ratio for every year for all stocks, including S&P 500 index (yahoo finance symbol: ^GSPC)
* visualise the results
* calculate the relative performance for each stock vs the index
* rank stocks on return / risk ratio, show top 20
* filter stocks, select the ones with better performance than SP500 index
* find stocks that performed better than the SP500 index more than twice over the past 5 year

## Findings
* Best of last year:
['CCL', ‘'RE',  'RCL', 'ANTM',  'MSFT', 'ALL', 'XL',  'PGR',  'DE', 'UNH', 'MA', 'APH', 'MU', 'DGX', 'PCLN', 'FMC',  'LRCX',  'BA', 'ROK',  'ROP']
Better Return to Risk Ratio than S&P500 index

* Ony 30 stocks performed better than the S&P500 index more than twice over the 5 year period:
['ADBE', 'ALL', 'AON', 'AOS', 'APH', 'AVY', 'BDX', 'BSX', 'CAG', 'CVS', 'EFX', 'EXR', 'FISV', 'GIS', 'HD', 'HON', 'HSIC', 'LRCX', 'MA', 'MMC', 'NYSE:NWL', 'ORLY', 'SRE', 'TMO', 'VRSK', 'WAT', 'DPS', 'DGX', 'PGR', 'UNH']

* **With only 6% of the stocks outperforming the index it is very difficult to beat the index!**
* None of these stocks outperformed the index in all the 5 periods.
* There is a positive correlation between risk and return for the observed data
* On average 20% of the stocks perform better than the SP500 index in a single year
* Only in year 3 of the past 5 years there are stocks which performed better than the SP500 index and with less risks, other years all stocks with higher returns also had higher risks

## Limitations
* Survival bias: dataset only has historical data from the current S&P 500 index companies. The composition of the index changes. Over the past 5 years new companies entered the index and others were removed.
* Only S&P 500 index stocks, biased to big US companies
* We are using data of the past 5 year, a period with continuous rise of stock prices. This might influence stocks that are well typically well performing in a bullish market. These same stocks might not perform so well in a bearish market.


## Conclusions
* It is very hard to beat the market (S&P500 index)
* There is no assurance that past performance is an accurate predictor of the future

## Acknowledgements
Thanks to Kaggle and Yahoo for making historical stock prices data available for research

## References
Pandas_datareader library: https://pandas-datareader.readthedocs.io/en/latest/
