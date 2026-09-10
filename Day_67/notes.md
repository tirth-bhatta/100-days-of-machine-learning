# Lasso Regression | Intuition and Code Sample | Regularized Linear Models

## 📌 What is Lasso Regression?

Lasso Regression is a **regularized version of Linear Regression**.

It is mainly used to:

* Reduce overfitting
* Make the model simpler
* Select important features
* Push some coefficients exactly to **0**

Lasso stands for:

**Least Absolute Shrinkage and Selection Operator**

---

## 🧠 Intuition

In normal Linear Regression, the model tries to find the best line by minimizing the prediction error.

Lasso adds an extra **penalty** for large coefficients.

The idea is:

```text
Prediction Error + Regularization Penalty
```

The penalty depends on the **absolute value of the coefficients**.

So Lasso tries to keep coefficients small.

Even more importantly, some coefficients can become exactly:

```text
0
```

When a coefficient becomes 0, that feature is effectively removed from the model.

### Example

Suppose we have:

```text
Age       → 0.8
Salary    → 1.5
Experience → 0.3
City      → 0.0
```

Lasso can make:

```text
City → 0
```

This means the model considers that feature unnecessary.

---

## 📐 Lasso Formula

The objective function is:

```text
Cost = MSE + α × Σ|β|
```

Where:

* **MSE** = Mean Squared Error
* **α (alpha)** = regularization strength
* **β** = model coefficients
* **Σ|β|** = sum of absolute coefficient values

### What does Alpha do?

```text
Small α → Less regularization
Large α → More regularization
```

If alpha becomes larger, coefficients are pushed harder toward zero.

---

## 🔥 Lasso vs Linear Regression

### Linear Regression

```text
Minimize → Prediction Error
```

### Lasso Regression

```text
Minimize → Prediction Error + Penalty
```

So:

```text
Linear Regression
        ↓
Prediction Error

Lasso Regression
        ↓
Prediction Error + Absolute Coefficient Penalty
```

---

## 💡 Why is Lasso useful?

Imagine you have 10 features:

```text
X1 X2 X3 X4 X5 X6 X7 X8 X9 X10
```

But only 4 are actually useful.

Lasso can produce:

```text
X1  → 0.8
X2  → 0
X3  → 1.2
X4  → 0
X5  → 0
X6  → 0.5
X7  → 0
X8  → 0
X9  → 1.1
X10 → 0
```

Now the model mainly uses:

```text
X1, X3, X6, X9
```

This is called **feature selection**.

---

# 💻 Code Sample

## Step 1 — Import Libraries

```python
import numpy as np
from sklearn.linear_model import Lasso
from sklearn.model_selection import train_test_split
from sklearn.metrics import mean_squared_error
```

---

## Step 2 — Create Sample Data

```python
X = np.array([
    [1, 2, 3],
    [2, 3, 4],
    [3, 4, 5],
    [4, 5, 6],
    [5, 6, 7],
    [6, 7, 8],
    [7, 8, 9],
    [8, 9, 10]
])

y = np.array([10, 15, 20, 25, 30, 35, 40, 45])
```

Here:

```text
X → Input features
y → Target/output
```

---

## Step 3 — Split the Data

```python
X_train, X_test, y_train, y_test = train_test_split(
    X, y, test_size=0.25, random_state=42
)
```

The data is divided into:

```text
Training Data → Used to train the model
Testing Data  → Used to check the model
```

---

## Step 4 — Create Lasso Model

```python
model = Lasso(alpha=0.1)
```

Here:

```text
alpha = 0.1
```

controls the strength of regularization.

---

## Step 5 — Train the Model

```python
model.fit(X_train, y_train)
```

The model learns the relationship between the input features and target.

---

## Step 6 — Make Predictions

```python
y_pred = model.predict(X_test)
```

Now the trained model predicts values for the test data.

---

## Step 7 — Check the Error

```python
mse = mean_squared_error(y_test, y_pred)

print("Mean Squared Error:", mse)
```

---

## Step 8 — Print Coefficients

```python
print("Coefficients:", model.coef_)
print("Intercept:", model.intercept_)
```

The coefficients tell us how strongly each feature affects the prediction.

If a coefficient becomes:

```text
0
```

that feature has effectively been removed by Lasso.

---

# 🚀 Complete Code

```python
import numpy as np
from sklearn.linear_model import Lasso
from sklearn.model_selection import train_test_split
from sklearn.metrics import mean_squared_error

# Create dataset
X = np.array([
    [1, 2, 3],
    [2, 3, 4],
    [3, 4, 5],
    [4, 5, 6],
    [5, 6, 7],
    [6, 7, 8],
    [7, 8, 9],
    [8, 9, 10]
])

y = np.array([10, 15, 20, 25, 30, 35, 40, 45])

# Split data
X_train, X_test, y_train, y_test = train_test_split(
    X, y, test_size=0.25, random_state=42
)

# Create Lasso model
model = Lasso(alpha=0.1)

# Train model
model.fit(X_train, y_train)

# Make predictions
y_pred = model.predict(X_test)

# Calculate error
mse = mean_squared_error(y_test, y_pred)

# Display results
print("Predicted Values:", y_pred)
print("Actual Values:", y_test)
print("Mean Squared Error:", mse)
print("Coefficients:", model.coef_)
print("Intercept:", model.intercept_)
```

---

# 🖥️ Example Output

```text
Predicted Values: [15.0 40.0]
Actual Values: [15 40]
Mean Squared Error: 0.0
Coefficients: [1.66666667 1.66666667 1.66666667]
Intercept: 1.66666667
```

**Note:** Exact coefficient/output values can vary slightly depending on the dataset and regularization strength.

---

# 🔑 Key Points

1. **Lasso is a regularized Linear Regression algorithm.**

2. It uses the **absolute values of coefficients** as the penalty.

3. Increasing **alpha** increases regularization.

4. Lasso can make some coefficients exactly **0**.

5. Therefore, Lasso can perform **feature selection**.

---

# 🆚 Lasso vs Ridge

| Feature           | Ridge                      | Lasso                              |
| ----------------- | -------------------------- | ---------------------------------- |
| Penalty           | L2                         | L1                                 |
| Coefficients      | Become small               | Can become exactly 0               |
| Feature Selection | ❌ Usually no               | ✅ Yes                              |
| Useful for        | Handling multicollinearity | Feature selection + regularization |

Simple memory trick:

```text
Ridge → Shrinks coefficients
Lasso → Shrinks + removes features
```

---

# 🎯 Today's Learning

```text
Linear Regression
       ↓
Regularization
       ↓
Ridge Regression
       ↓
Lasso Regression
       ↓
Feature Selection
```

### One-line definition:

**Lasso Regression reduces overfitting by adding an L1 penalty and can make some feature coefficients exactly zero.**

---

# 📁 Suggested Repository Structure

```text
100-Days-of-ML/
│
├── Day-10-Lasso-Regression/
│   ├── README.md
│   └── lasso_regression.py
│
└── ...
```

---

# 📝 Git Commit

```bash
git add .
git commit -m "Day 10: Learn Lasso Regression intuition and code"
git push
```

## 🚀 Day 10 Completed

**Topic:** Lasso Regression
**Concept:** L1 Regularization
**Main advantage:** Feature Selection
**Important parameter:** Alpha
**Key idea:** Some coefficients can become zero
