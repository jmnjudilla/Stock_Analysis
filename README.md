📊 Stock Analysis SQL KPIs

This project showcases essential stock market Key Performance Indicators (KPIs) using SQL. It is designed as part of a Data Analyst portfolio to demonstrate practical SQL skills applied to financial data analysis.

📁 Dataset Description

The dataset contains historical data for a single stock with the following columns:

Column(Description)

date (Trading date)
year(Year (integer))
month(Month (integer))
open(Opening price)
high(Highest price of the day)
low(Lowest price of the day)
close(Closing price)
volume(Trading volume (integer))

📌 Key Performance Indicators (KPIs)

1. Average Closing Price

Purpose: Measures the average closing price, grouped by month and year.

Insight: Helps understand price trends over time.

SELECT year, month, AVG(close) as avg_close
FROM tutorial.aapl_historical_stock_price
GROUP BY 1,2
ORDER BY 1,2;


2. All-Time High and Low

Purpose: Identifies the maximum and minimum price levels.

Insight: Indicates the overall price range and volatility.

SELECT MAX(high) as all_time_high,
MIN(low) as all_time_low
FROM tutorial.aapl_historical_stock_price;

3. Daily Percentage Change

Purpose: Calculates the percentage change from open to close.

Insight: Shows daily volatility and movement.

SELECT date,
close - open / open * 100 as daily_pct_change
FROM tutorial.aapl_historical_stock_price
WHERE open != 0;

4. Total Volume Traded

Purpose: Sums the total volume traded.

Insight: Indicates market liquidity.

SELECT SUM(volume) total_volume
FROM tutorial.aapl_historical_stock_price;

5. Average Daily Volume

Purpose: Computes the average volume per trading day.

Insight: Helps assess typical trading activity.

SELECT date,
AVG(volume) as avg_volume
FROM tutorial.aapl_historical_stock_price
GROUP BY 1
ORDER BY 1;

6. Volume-Weighted Average Price (VWAP)

Purpose: Weighted average of closing price based on volume.

Insight: Reflects price consensus weighted by trades.

SELECT 
SUM((close*volume)/volume) as vwap
FROM tutorial.aapl_historical_stock_price
WHERE volume != 0;

7. Monthly Returns

Purpose: Calculates monthly return as percentage gain/loss.

Insight: Measures performance of the stock month-to-month.



8. Best and Worst Trading Days

Purpose: Finds the highest and lowest single-day returns.

Insight: Highlights the most volatile trading sessions.



9. 7-Day Moving Average

Purpose: Smooths price trends over a weekly period.

Insight: Helps identify short-term trends.

SELECT date,
close - open / open * 100 as daily_pct_change
FROM tutorial.aapl_historical_stock_price
WHERE open != 0
ORDER BY daily_pct_change DESC
LIMIT 1;

10. Bullish Days Count

Purpose: Counts days when closing price was higher than opening.

Insight: Measures positive sentiment.

SELECT COUNT(*) as bullish_days 
FROM tutorial.aapl_historical_stock_price
WHERE close > open;

11. Average Daily Price Range

Purpose: Average difference between daily high and low.

Insight: Indicates average daily volatility.

SELECT 
AVG(high - low) as avg_daily_price_range
FROM tutorial.aapl_historical_stock_price;

12. Standard Deviation of Daily Returns

Purpose: Measures variability of daily returns.

Insight: Assesses risk and volatility.

SELECT date, close,  
AVG(close) OVER (ORDER BY date ROWS BETWEEN 6 PRECEDING AND CURRENT ROW) as ma_7
FROM tutorial.aapl_historical_stock_price;

✅ Summary

These KPIs were chosen to cover a wide range of financial and analytical dimensions:

Price performance
Trend analysis
Market volume
Volatility and risk
They demonstrate SQL proficiency in:
Aggregations
Window functions
CTEs
Financial computations

📌 How to Use

Clone the repository.
Load your own stock_data table with the specified schema.
Run queries using any SQL engine (e.g., PostgreSQL, MySQL, SQLite).

📬 Contact

For questions or collaboration, feel free to connect via GitHub or LinkedIn.

Built with ❤️ for data analysis and SQL mastery.
