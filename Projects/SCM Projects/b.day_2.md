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

### Features & Baselines

###### Step 1: Prepare Data (aggregation + split)
- We'll forecast next-day demand per (store, item)
- Group sales_long by store_id, item_id, date.
- Sort by date
- Train/validation split based on time (not random)

###### Step 2: Feature Engineering

- Why Feature Engineering is important in Time Series
  - Raw time series data (date, store_id, item_id, sales) by itself doesn’t contain enough information for a machine learning model to learn patterns.
  - Unlike statistical models (like ARIMA), ML models (like XGBoost, LightGBM, Random Forests, Neural Nets) don’t “know” about:
    - Time order
    - Seasonality (weekly, monthly patterns)
    - Past demand influencing future demand
    - Special events/holidays affecting sales
- So, we must create features that encode these time dependencies.

1. Lag features (1, 7, 14, 28 days):
   - Capture short-term and long-term demand memory.
   - Example: If sales always spike 7 days later (weekly cycle), the lag helps the model see that.
2. Rolling mean/std (7, 28 days):
   - Capture trend (average demand) and volatility (how much it fluctuates).
   - Example: If an item is steadily trending upward, the rolling mean captures that slope.
3. Calendar features (day-of-week, month):
   - Encode seasonality.
   - Example: More snacks may sell on weekends, more clothes in December.
4. Event proxy (holiday/event flag):
   - Capture external shocks.
   - Example: Sales spike on “Christmas” or during “Black Friday.”

- How this helps later:
  - When you train your ML model:
    1. These features act as predictors (X) while sales is the target (y).
    2. The model learns relationships like:
       - If it’s Friday, sales are higher.
       - If lag_7 = 50, today’s sales may be close to that.
       - If is_event = 1, expect a spike.
       - If rmean_28 is rising, trend is upward.
- This way, the model can forecast future sales by looking at historical demand, seasonality, and special events.

- This step is about transforming raw time-series data into machine-readable features. Without it, your model would have no clue about temporal patterns, and forecasting accuracy would be very poor.

- lag_1: Sales yesterday
- lag_7: Sales last week, same day
- lag_14: Sales two weeks ago, same day
- lag_28: Sales four weeks ago (monthly cycle)

- Lags are like giving the model a memory of the past so it can predict the future. Without lags, the model would only see today’s date and have no idea what happened before.
- We don’t stop at just lag_1 (yesterday). We add lag_7, lag_14, lag_28 because sales are not only influenced by yesterday but also by recurring weekly and monthly patterns.

---

####### Step 3: Define Baselines

- Naive Forecast: tomorrow = today’s sales (lag_1).
  - lag_1 = yesterday’s sales.
  - So the forecast for today = sales of yesterday.
  - This is the simplest baseline in time series forecasting.
  - If sales were 100 yesterday → predict 100 today.

- Seasonal Naive: tomorrow = same day last week (lag_7).
  - lag_7 = sales from 7 days ago (same weekday last week).
  - Why? Because many products have weekly seasonality (think groceries, weekend shopping, etc.).
  - So the forecast for today = sales from the same day last week.
  - If last Monday’s sales = 120 → predict 120 for this Monday.

