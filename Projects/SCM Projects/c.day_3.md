## 🔹 Why Are We Doing This?

When we build a **forecasting model**, we need to answer:

1. **How good is the model?**  
   → That means we need **metrics** (numbers that quantify prediction error).  

2. **Is our model actually better than something simple?**  
   → That’s why we compare against **baseline forecasts** (like Naive, Seasonal Naive).  

Without metrics + baselines:
- You might build a “fancy” model that isn’t any better than just guessing yesterday’s sales.
- You won’t know if your improvements are meaningful.

So:  
- **Metrics** = scorecard.  
- **Baselines** = benchmark to beat.  

---

## 🔹 The Metrics (Theory)

We use **4 metrics**, each highlighting a different perspective:

### 1. RMSE (Root Mean Squared Error)
\[
RMSE = \sqrt{\frac{1}{n}\sum (y_t - \hat{y}_t)^2}
\]  
- Penalizes **big mistakes more heavily** (squaring).  
- Good when large errors are very costly (e.g., stockouts).

# 📌 Root Mean Squared Error (RMSE) Explained

Imagine you’re a **weather forecaster** 🌦️.  
Every day, you predict tomorrow’s temperature, and then reality happens.

- On Monday, you predicted **28°C**, but the actual temperature was **30°C**.  
- On Tuesday, you predicted **25°C**, but the actual was **27°C**.  
- On Wednesday, you predicted **29°C**, but the actual was **25°C**.  

You might wonder: **“How good (or bad) are my predictions overall?”**

That’s where **RMSE (Root Mean Squared Error)** comes in. It’s a way to measure the difference between what you *predicted* and what actually *happened*.  

---

## 🔹 Step 1: Understand "Error"

- **Error = Prediction – Actual**  
- Example (from above):  
  - Monday: `28 - 30 = -2`  
  - Tuesday: `25 - 27 = -2`  
  - Wednesday: `29 - 25 = +4`  

Errors can be **negative** (you under-predicted) or **positive** (you over-predicted).  

---

## 🔹 Step 2: Square the Errors

Why square them?

- To **remove negatives** (otherwise they cancel out).  
- To **penalize larger mistakes more strongly** (a big error hurts more than a small one).  

So:

- Monday: `(-2)^2 = 4`  
- Tuesday: `(-2)^2 = 4`  
- Wednesday: `(4)^2 = 16`  

---

## 🔹 Step 3: Take the Mean

Average the squared errors (this gives us **MSE = Mean Squared Error**).  


---

## 🔹 Step 4: Take the Square Root

Finally, take the square root of MSE to bring it back to the **original units** (temperature, dollars, etc.).  



---

# ✅ Interpretation

- RMSE = **2.83°C** means:  
  - On average, your predictions are **about 2.8 degrees off**.  
  - Lower RMSE = better model.  
  - Higher RMSE = worse model.  

---

# 🔑 Key Things to Know About RMSE

1. **Always Non-Negative**  
   - RMSE ≥ 0.  
   - 0 means a *perfect model* (predictions = actual values).  

2. **Sensitive to Large Errors**  
   - Because of squaring, one big error can dominate RMSE.  
   - Example: If all your predictions are close except for one huge mistake, RMSE shoots up.  

3. **Same Unit as Target Variable**  
   - If you predict house prices in dollars, RMSE is also in dollars.  
   - This makes it easy to interpret.  

4. **Comparison Tool**  
   - RMSE is most useful when comparing models:  
     - Model A → RMSE = 50  
     - Model B → RMSE = 30  
     - ✅ Model B is better (on average, it’s closer to the truth).  

---

# 📊 Example in Real Life

Suppose you build a **machine learning model** to predict **house prices** 🏡.  

- Actual prices (in $1000s): `[200, 220, 250, 270]`  
- Predicted prices: `[210, 230, 240, 260]`  

Steps:  

- Errors = `[10, 10, -10, -10]`  
- Squared Errors = `[100, 100, 100, 100]`  
- MSE = `(400 / 4) = 100`  
- RMSE = `√100 = 10`  

📌 Meaning: Your model’s predictions are off by **about $10,000 on average**.  

---

# 🆚 RMSE vs Other Metrics

- **MAE (Mean Absolute Error):** Averages the absolute differences, less sensitive to big errors.  
- **MSE (Mean Squared Error):** Similar to RMSE, but without square root (harder to interpret since it’s in squared units).  
- **RMSE:** Popular because it balances interpretability (original units) and sensitivity to big errors.  

---

# 🎯 In Short

- RMSE = **Root Mean Squared Error**  
- Measures **how far off predictions are, on average**.  
- **Lower RMSE = better model**  
- Especially good when large errors are **extra bad** (finance, healthcare, weather).  

---

👉 Think of RMSE as your **“average mistake size”** in the same units as your predictions.

- We take the root to get the units back to normal such as MSE would have unit C^2 since it squares but taking a square root gets it back to C. So it is easier to interpret
