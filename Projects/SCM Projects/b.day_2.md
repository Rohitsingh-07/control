**Day 1 – Features & baselines (2–3h)** Link - https://chatgpt.com/s/t_68b627aa586881919ec5f1fc4d87a44c
- I asked chatgpt on why is step required - https://chatgpt.com/s/t_68b62b1c9c4481918f01197cba96ef83

<img width="860" height="417" alt="image" src="https://github.com/user-attachments/assets/2d1a8be3-c847-40c1-bfb4-9cd14bb0bfc0" />

- Raw data → Feature Engineering (lags, rolling stats, events, fixed effects)
- Baselines (Naive, Seasonal Naive) → Benchmarks
- Features + Baselines feed into Machine Learning models
- Models are evaluated vs. baselines → best ones go into Inventory Optimization

---

- So the first thing that is required is we need to set a benchmark which would be the baseline. In this case, it is going to be
  - Naive: Forecast today = yesterday’s sales
  - Seasonal Naive: Forecast today = sales on the same weekday last week
 
- This will be the benchmark and then we will compare this benchmark with our ML model and see how is the performance and if the performance is good we are going to use the ML model
- Once baselines are in place, every future model (Ridge, XGBoost, LSTM) will be compared against Naive and Seasonal Naive. We need this step to convincingly show improvement
---

2. Feature creation = turning raw data into signal
- By creating lags, rolling averages, seasonality, calendar features, event/holiday indicators, you transform the dataset into something models can learn from.
- Example: Instead of just saying “yesterday’s sales = 50,” you also give the model:
  - Last week same day = 47
  - 7-day rolling mean = 52
  - Is today Christmas = Yes
  - Month = December
  - Store fixed effect = Store_A
- These features capture demand patterns, seasonality, and shocks (holidays, promotions).

--- 

#### Implementation

1) Step 1: Prepare Data (Aggregation + Split)
We'll forecast next-day demand per (store, item)
- Group sales_long by store_id, item_id, date.
- Sort by date
- Train/validation split based on time (not random)

---

##### Time Series Analysis

- Time Series Analysis is the process of studying data that is collected over time (e.g., daily sales, stock prices, temperature, website visits) to:
  1. Understand patterns in the past
  2. Explain relationships (e.g., how seasonality affects sales).
  3. Forecast the future (make predictions)
- Unlike normal data, a time series has a time order, which makes it special
---
- Components of a Time Series
  1. Trend : The long-term movement (upward or downward) | Example: E-commerce sales increasing every year
  2. Seasonality : Regular repeating patterns | Example: Ice Cream sales peak in summer every year
  3. Cyclic Patterns : Longer term ups and downs
  4. Noise (Irregular) : Random Fluctations that can't be explained
---
- Types of Time Series Analysis
  1. Descriptive Analysis: Summarize and visualize
  2. Stationarity Testing: Check if data has constant mean/variance (important for many models)
  3. Model Based Analysis: Fit models like ARIMA, Exponential Smoothing, Prophet, LSTMs
  4. Casual Analysis: Study how external events impact series
  5. Forecasting: Predicting future values using the above insights
---
- Common Tools in TSA
  1. Visualization
  2. Statistical tests
  3. Models: ARIMA, ETS, Prophet, ML/DL Models
 
- Time Series Analysis = the study of data over time to understand its patterns (trend, seasonality, cycles, noise) and use that knowledge for explanation and forecasting.

---


