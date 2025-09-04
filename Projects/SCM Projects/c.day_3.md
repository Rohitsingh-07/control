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

---
---
---

# 📌 Mean Absolute Error (MAE) Explained

Imagine again you’re a **weather forecaster** 🌦️.  
Every day, you predict tomorrow’s temperature, and then reality happens.  

- On Monday, you predicted **28°C**, but the actual temperature was **30°C**.  
- On Tuesday, you predicted **25°C**, but the actual was **27°C**.  
- On Wednesday, you predicted **29°C**, but the actual was **25°C**.  

You might wonder: **“How far off am I, on average?”**  

That’s exactly what **MAE (Mean Absolute Error)** tells you.  

---

## 🔹 Step 1: Understand "Error"

- **Error = Prediction – Actual**  
- Example (from above):  
  - Monday: `28 - 30 = -2`  
  - Tuesday: `25 - 27 = -2`  
  - Wednesday: `29 - 25 = +4`  

---

## 🔹 Step 2: Take the Absolute Value

Why absolute?  
- To ignore the direction of error (negative or positive).  
- You only care about **how big the mistake is**, not whether you were high or low.  

So:  
- Monday: `|-2| = 2`  
- Tuesday: `|-2| = 2`  
- Wednesday: `|+4| = 4`  

---

## 🔹 Step 3: Take the Mean

Now, average the absolute errors.  


---

# ✅ Interpretation

- MAE = **2.67°C** means:  
  - On average, your predictions are **about 2.7 degrees off**.  
  - Lower MAE = better model.  
  - Higher MAE = worse model.  

---

# 🔑 Key Things to Know About MAE

1. **Always Non-Negative**  
   - MAE ≥ 0.  
   - 0 means a perfect model.  

2. **Linear Penalty**  
   - All errors are penalized equally.  
   - Example: An error of 10 is exactly twice as bad as an error of 5.  

3. **Same Unit as Target Variable**  
   - Just like RMSE, MAE is in the same unit as the prediction (°C, dollars, etc.).  

4. **More Robust to Outliers**  
   - Unlike RMSE, which squares errors (amplifying big mistakes), MAE treats all errors proportionally.  
   - Example: If one prediction is way off, MAE won’t “blow up” as much as RMSE.  

---

# 📊 Example in Real Life

Suppose you build a **machine learning model** to predict **house prices** 🏡.  

- Actual prices (in $1000s): `[200, 220, 250, 270]`  
- Predicted prices: `[210, 230, 240, 260]`  

Steps:  

- Errors = `[10, 10, -10, -10]`  
- Absolute Errors = `[10, 10, 10, 10]`  
- MAE = `(40 / 4) = 10`  

📌 Meaning: Your model’s predictions are off by **about $10,000 on average**.  

---

# 🆚 MAE vs RMSE

- **MAE:**  
  - Simpler, more interpretable.  
  - Treats all errors equally.  
  - More robust to outliers.  

- **RMSE:**  
  - Penalizes large errors more strongly.  
  - Useful when big mistakes are especially costly (e.g., finance, healthcare).  

👉 Rule of Thumb:  
- Use **MAE** when you want a **straightforward average error**.  
- Use **RMSE** when **large errors are much worse** than small ones.  

---

# 🎯 In Short

- MAE = **Mean Absolute Error**  
- Measures the **average size of mistakes** (ignoring direction).  
- **Lower MAE = better model**  
- More **robust to outliers** than RMSE.  

---

👉 Think of MAE as your **“average distance from the truth”** in the same units as your predictions.  

---
---
---

# 📌 Mean Absolute Percentage Error (MAPE) Explained

Imagine you’re still a **weather forecaster** 🌦️.  

This time, instead of just asking **“How far off am I?”**, you want to ask:  
👉 **“How far off am I, relative to the actual value, in percentage terms?”**  

That’s what **MAPE** tells you.  

---

## 🔹 Step 1: Recall the Errors

Let’s take the same predictions:  

- Monday: Predicted **28°C**, Actual **30°C** → Error = -2  
- Tuesday: Predicted **25°C**, Actual **27°C** → Error = -2  
- Wednesday: Predicted **29°C**, Actual **25°C** → Error = +4  

---

## 🔹 Step 2: Take the Absolute Value

- Monday: `|-2| = 2`  
- Tuesday: `|-2| = 2`  
- Wednesday: `|+4| = 4`  

---

## 🔹 Step 3: Convert to Percentage Error

Now divide each absolute error by the **actual value**, then multiply by 100:  

- Monday: `(2 / 30) × 100 = 6.67%`  
- Tuesday: `(2 / 27) × 100 ≈ 7.41%`  
- Wednesday: `(4 / 25) × 100 = 16%`  

---

## 🔹 Step 4: Take the Mean

Now, average these percentage errors:  

MAPE = (6.67% + 7.41% + 16%) / 3
MAPE ≈ 10.7%


---

# ✅ Interpretation

- MAPE = **10.7%** means:  
  - On average, your forecasts are **about 10.7% off from the actual values**.  
- The **lower the MAPE, the better the model**.  

---

# 🔑 Key Things to Know About MAPE

1. **Expressed in %**  
   - Unlike MAE or RMSE (which are in original units), MAPE is in **percentages**.  
   - Makes it easy to interpret across different datasets.  

2. **Scale Independent**  
   - Works well when comparing models across datasets with different units.  

3. **Intuitive for Business**  
   - Saying “my forecasts are **10% off** on average” is more intuitive than “off by 2.8 units”.  

4. **Limitations**  
   - ⚠️ **Division by zero problem:** If any actual value = 0, MAPE breaks.  
   - ⚠️ **Bias towards small actual values:** A tiny denominator can cause a huge percentage error.  

---

# 📊 Example in Real Life

Suppose you predict **monthly sales revenue** 📈:  

- Actual values ($): `[1000, 1200, 1500, 2000]`  
- Predicted values ($): `[1100, 1150, 1400, 2100]`  

Steps:  

- Errors = `[100, -50, -100, 100]`  
- Absolute Errors = `[100, 50, 100, 100]`  
- Percentage Errors = `[100/1000=10%, 50/1200≈4.2%, 100/1500≈6.7%, 100/2000=5%]`  
- MAPE = `(10% + 4.2% + 6.7% + 5%) / 4 ≈ 6.5%`  

📌 Meaning: Your sales predictions are **about 6.5% off on average**.  

---

# 🆚 MAPE vs MAE vs RMSE

- **MAE:**  
  - Measures average absolute error (in original units).  

- **RMSE:**  
  - Penalizes large errors more strongly (in original units).  

- **MAPE:**  
  - Expresses average error as a **percentage of actuals** (unit-free).  

👉 Use **MAPE** when:  
- You want an **easily interpretable percentage**.  
- You’re comparing errors across different scales.  

⚠️ Avoid MAPE if your dataset has **zeros or very small actual values**.  

---

# 🎯 In Short

- MAPE = **Mean Absolute Percentage Error**  
- Measures the **average percentage difference** between predictions and actuals.  
- **Lower MAPE = better model**  
- Super intuitive, but has pitfalls (zero values, small denominators).  

---

👉 Think of MAPE as:  
**“On average, how far off am I, in percentage terms?”** ✅

---
---
---

# 📌 Weighted Absolute Percentage Error (WAPE) Explained

Imagine you’re still the **weather forecaster** 🌦️.  

You already learned about **MAPE**: it tells you *“On average, how far off am I in percentage terms?”*  

But there’s a problem ⚠️:  
- MAPE can **explode** when actual values are very small (because dividing by small numbers gives huge percentages).  
- Also, MAPE calculates the percentage error **individually for each prediction** and then averages — which can sometimes be misleading.  

👉 That’s where **WAPE** comes in. It’s like a **more stable cousin of MAPE**.  

---

## 🔹 Step 1: Recall the Errors

Take the same forecasts:  

- Monday: Predicted **28°C**, Actual **30°C** → Error = -2  
- Tuesday: Predicted **25°C**, Actual **27°C** → Error = -2  
- Wednesday: Predicted **29°C**, Actual **25°C** → Error = +4  

Absolute Errors = `[2, 2, 4]`  

---

## 🔹 Step 2: Sum the Absolute Errors

Add up all absolute mistakes:  

Total Absolute Error = 2 + 2 + 4 = 8


---

## 🔹 Step 3: Divide by Total Actuals

Instead of averaging per-point percentages like MAPE,  
👉 WAPE looks at **total error relative to total actual values**.  

Total Actual = 30 + 27 + 25 = 82


Now:  

WAPE = (Total Absolute Error / Total Actual) × 100 </n>
WAPE = (8 / 82) × 100 ≈ 9.76%


---

# ✅ Interpretation

- WAPE = **9.76%** means:  
  - Across all predictions, the total mistakes add up to **about 9.8% of the total actual values**.  
- It’s often called the **“overall percentage error”**.  

---

# 🔑 Key Things to Know About WAPE

1. **Also in %**  
   - Like MAPE, WAPE is expressed as a percentage.  

2. **More Stable than MAPE**  
   - By using the **sum of actuals** instead of per-point percentages, WAPE avoids blowing up on small values.  

3. **Used in Forecasting (Especially Retail / Supply Chain)**  
   - Businesses love WAPE because it tells them:  
     👉 “Overall, my forecast was off by X% of total demand.”  

4. **Sometimes Called “Forecast Accuracy”**  
   - In industry, people often report:  
     ```
     Forecast Accuracy = 100% – WAPE
     ```
   - Example: If WAPE = 9.76%, forecast accuracy ≈ 90.2%.  

---

# 📊 Example in Real Life

Suppose you forecast **monthly sales demand** 🛒:  

- Actual sales = `[100, 200, 300, 400]`  
- Predicted sales = `[110, 190, 310, 390]`  

Steps:  

- Errors = `[-10, +10, -10, +10]`  
- Absolute Errors = `[10, 10, 10, 10]`  
- Total Absolute Error = `40`  
- Total Actual = `100 + 200 + 300 + 400 = 1000`  

WAPE = (40 / 1000) × 100 = 4%


📌 Meaning: Your forecasts are **off by about 4% of the total demand**.  

---

# 🆚 WAPE vs MAPE vs MAE

- **MAE:** Average absolute error (in original units).  
- **MAPE:** Average percentage error (per observation).  
- **WAPE:** Total error compared to total actuals (aggregate percentage error).  

👉 WAPE is often preferred in business forecasting because it:  
- Avoids MAPE’s instability with small actuals.  
- Gives an **overall % error**, which is very interpretable.  

---

# 🎯 In Short

- WAPE = **Weighted Absolute Percentage Error**  
- Measures **total error relative to total actual values**.  
- More **stable** than MAPE.  
- Popular in **retail, supply chain, and demand forecasting**.  

---

👉 Think of WAPE as:  
**“Overall, my forecasts were off by X% of the total actuals.”** ✅

---
---
---

# 🔍 Model Evaluation: Naive vs Seasonal Naive

You have these metrics:

| Model          | RMSE | MAE  | MAPE (%)      | WAPE (%) |
| -------------- | ---- | ---- | ------------- | -------- |
| Naive          | 2.61 | 1.16 | 27,879,996.33 | 84.74    |
| Seasonal Naive | 2.73 | 1.20 | 29,812,652.05 | 87.22    |

---

## Step 1: Compare the metrics

1. **RMSE (Root Mean Squared Error)**  
   - Naive = 2.61, Seasonal Naive = 2.73  
   - Lower is better. ✅  
   - **Naive slightly better**.

2. **MAE (Mean Absolute Error)**  
   - Naive = 1.16, Seasonal Naive = 1.20  
   - Lower is better. ✅  
   - **Naive slightly better**.

3. **WAPE (Weighted Absolute Percentage Error)**  
   - Naive = 84.74%, Seasonal Naive = 87.22%  
   - Lower is better. ✅  
   - Again, **Naive slightly better**.

4. **MAPE (Mean Absolute Percentage Error)**  
   - Naive = 27,879,996%, Seasonal Naive = 29,812,652%  
   - Extremely huge! ⚠️  
   - This is **not meaningful** — almost certainly due to **very small or zero values in your actuals (`y_true`)**, since MAPE divides by `y_true`.

---

## Step 2: What you can conclude

- **MAE is the smallest in absolute terms**, yes — meaning **on average, the predictions are off by ~1.16 units**.  
- RMSE is slightly higher because it **penalizes larger errors** more than MAE.  
- WAPE is reasonable (~85%), showing that **overall errors are ~85% of total actuals**.  
- MAPE is **completely blown up** — ignore it in this case because some actual values are zero or very small.

✅ **Key takeaway:**  
- Between Naive and Seasonal Naive: **Naive performs slightly better** in terms of RMSE, MAE, and WAPE.  
- MAPE is unreliable here due to data scale issues.

---

## 💡 Rule of thumb when evaluating models

- Look at **MAE and RMSE** for numeric accuracy.  
- Look at **WAPE** for business/aggregate-level errors.  
- Ignore **MAPE** if your actuals contain zeros or tiny numbers.

---

If you want, I can help you **plot these errors visually** to see which model is actually performing better across your validation set — sometimes the numbers alone don’t tell the full story.

---
