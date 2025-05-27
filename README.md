# search-trends-vs-financial-markets

# Carrefour Stock Data and Google Trends Keywords Collection Scripts
This Python script is used for collecting historical stock price data for **Carrefour S.A. (CA.PA)**, a major FMCG retailer listed on **Euronext Paris**, and brand keywords on Google Trends to support the thesis titled:
> **Linking Google Search Trends to the Financial Performance of Major FMCG Players in France**


## Purpose
To collect reliable, publicly accessible stock data that aligns with Google Trends data to evaluate whether digital attention predicts short-term fluctuations in Carrefour’s stock price.


## Scripts
### 1. Yahoo Finance via `yfinance`
*This Python script collects daily and weekly stock data related to Carrefour S.A. `yfinance` offers a practical, peer-reviewed data source widely used in financial research.*
- Ticker: `CA.PA`
- Method: `yfinance` package
- Timeframe: 2022-01-01 to 2025-05-21
- Interval: `1wk`,  one week (to match Google Trends weekly SVI granularity)
- Fields: `Open`, `High`, `Low`, `Close`, `Adj Close`, `Volume`
- Geography: France
- Data Type: `TIMESERIES`
#### Save outputs:
- `carrefour_stock_data.csv` — Full daily data (if using daily mode)
- `carrefour_stock_weekly.csv` — Weekly data aligned with Google Trends
#### Output description:
Each row in the output file contains:
- `Date` (end of week)
- `Open`, `High`, `Low`, `Close`, `Adj Close` values
- `Volume`
This data is used to compute weekly returns and align temporally with Google Trends SVI data for statistical analysis.

### 2. Google Trends via SearchAPI.io
*This Python script collects weekly Google Trends data related to Carrefour and other FMCG-related keywords. Allows for the collection of reliable, time-aligned keyword search volume data.*
- API: [SearchAPI.io](https://www.searchapi.io/docs/google-trends)
- Endpoint: `https://www.searchapi.io/api/v1/search`
- Method: GET request via `requests` module
- Keywords: retrived from `Carrefour-related_keywords.xlsx`. Batching up to 5 keywords per request (as per API limit)
- Timeframe: 2022-01-01 to 2025-05-21
- Interval: Weekly (aligned with stock data granularity)
- Geography: France (`geo=FR`)
- Data Type: `TIMESERIES`
#### Save outputs:
   - `carrefour_search_trends_keywords.csv` (wide format keyword-level SVI data)
   - `carrefour_search_trends_aggregated.csv` (aggregated category-level SVI)
#### Output description:
Each row in the output file contains:
- `Date` (start of week)
- `Search Volume Index (SVI)` values for each keyword or category
- Data is reindexed to a common weekly timeline to ensure temporal alignment with Carrefour’s stock returns
