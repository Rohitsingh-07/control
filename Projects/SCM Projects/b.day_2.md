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
