# search-trends-vs-financial-markets - Carrefour Stock Data Collection Script
This Python script is used for collecting historical stock price data for **Carrefour S.A. (CA.PA)**, a major FMCG retailer listed on **Euronext Paris**, to support the thesis titled:
> **Linking Google Search Trends to the Financial Performance of Major FMCG Players in France**


## Purpose
To collect reliable, publicly accessible stock data that aligns with Google Trends data to evaluate whether digital attention predicts short-term fluctuations in Carrefour’s stock price.


## Scripts
### 1. Yahoo Finance via `yfinance`
*`yfinance` offers a practical, peer-reviewed data source widely used in financial research.*
- Ticker: `CA.PA`
- Method: `yfinance` package
- Timeframe: 2022-01-01 to 2025-05-21
- Interval: `1wk`,  one week (to match Google Trends weekly SVI granularity)
- Fields: `Open`, `High`, `Low`, `Close`, `Adj Close`, `Volume`
- Geography: France
#### Save outputs:
- `carrefour_stock_data.csv` — Full daily data (if using daily mode)
- `carrefour_stock_weekly.csv` — Weekly data aligned with Google Trends
#### Output description:
Each row in the output file contains:
- `Date` (end of week)
- `Open`, `High`, `Low`, `Close`, `Adj Close`
- `Volume`
This data is used to compute weekly returns and align temporally with Google Trends SVI data for statistical analysis.

### 2. Google Trends via SearchAPI.io
- Endpoint: [https://www.searchapi.io/api/v1/search](https://www.searchapi.io/api/v1/search)
- Method:
- Keywords: retrived from `Carrefour-related_keywords.xlsx`
- Timeframe: 2022-01-01 to 2025-05-21
- Interval: weekly
- Fields: `date`, `keyword`, `value`
- Geography: France
#### Save outputs:
   - `carrefour_search_trends_keywords.csv` (wide format)
   - `carrefour_search_trends_aggregated.csv` (by category)
#### Output description:

