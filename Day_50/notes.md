# Simple Linear Regression | Code + Intuition

## Introduction

Simple Linear Regression is a supervised machine learning algorithm used to predict a continuous numerical value using a single independent variable.

It tries to find the best-fit straight line between the input variable (X) and output variable (Y).

The equation of a simple linear regression line is:

**Y = mX + c**

Where:
- Y = Predicted output
- X = Input feature
- m = Slope/Coefficient
- c = Intercept

---

## Intuition

Suppose we have data containing the years of experience and salary of employees:

| Experience | Salary |
|------------|--------|
| 1 | 30000 |
| 2 | 35000 |
| 3 | 42000 |
| 4 | 48000 |
| 5 | 55000 |

If we plot these values, the points will not fall exactly on a straight line.

Linear Regression finds a line that best represents the relationship between experience and salary.

The model can then use this line to predict the salary of a person with a new number of years of experience.

For example:

**Input:** 6 years of experience  
**Output:** Predicted salary

The main idea is:

**Data → Find Relationship → Best-Fit Line → Prediction**

---

## Best-Fit Line

The best-fit line is the line that minimizes the difference between the actual values and the predicted values.

The error for an individual observation is:

**Error = Actual Value - Predicted Value**

Linear Regression tries to minimize the overall squared error:

**SSE = Σ(y - ŷ)²**

where:
- y = Actual value
- ŷ = Predicted value

---

## Python Code

```python
import numpy as np
import matplotlib.pyplot as plt
from sklearn.linear_model import LinearRegression

# Input data
X = np.array([1, 2, 3, 4, 5]).reshape(-1, 1)

# Output data
y = np.array([30000, 35000, 42000, 48000, 55000])

# Create Linear Regression model
model = LinearRegression()

# Train the model
model.fit(X, y)

# Get slope and intercept
print("Slope:", model.coef_[0])
print("Intercept:", model.intercept_)

# Predict salary for 6 years of experience
prediction = model.predict([[6]])

print("Predicted Salary:", prediction[0])

# Predictions for existing data
y_pred = model.predict(X)

# Visualization
plt.scatter(X, y, label="Actual Data")
plt.plot(X, y_pred, label="Regression Line")

plt.xlabel("Years of Experience")
plt.ylabel("Salary")
plt.title("Simple Linear Regression")
plt.legend()
plt.show()