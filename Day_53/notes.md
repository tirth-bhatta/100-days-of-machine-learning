# Multiple Linear Regression | Geometric Intuition & Code

## What is Multiple Linear Regression?

Multiple Linear Regression is an extension of Simple Linear Regression where we use **two or more independent variables** to predict one dependent variable.

In Simple Linear Regression:

y = b0 + b1x

In Multiple Linear Regression:

y = b0 + b1x1 + b2x2 + ... + bnxn

Where:
- y = Predicted output
- b0 = Intercept
- b1, b2, ..., bn = Coefficients
- x1, x2, ..., xn = Input features

For example, house price can be predicted using multiple features such as area, number of bedrooms, and age of the house.

Price = b0 + b1(Area) + b2(Bedrooms) + b3(Age)

---

## Geometric Intuition

In Simple Linear Regression, we have one independent variable, so the model finds the best-fitting **straight line**.

When we have two independent variables:

y = b0 + b1x1 + b2x2

the model finds the best-fitting **plane** in 3-dimensional space.

When we have more than two features, it becomes difficult to visualize, so mathematically it is called a **hyperplane**.

The basic idea remains the same:

**Find the best-fitting line/plane/hyperplane that minimizes the difference between actual and predicted values.**

The model tries to minimize the **Sum of Squared Errors (SSE)**:

SSE = Σ(yi - ŷi)²

where:

yi = Actual value  
ŷi = Predicted value

---

## Example

Suppose we want to predict house prices using:

- Area
- Number of Bedrooms
- House Age

The model can be:

Price = b0 + b1(Area) + b2(Bedrooms) + b3(Age)

Each coefficient represents the effect of that feature on the predicted output while keeping the other features constant.

---

## Implementation Using Scikit-Learn

```python
import pandas as pd
from sklearn.model_selection import train_test_split
from sklearn.linear_model import LinearRegression
from sklearn.metrics import mean_absolute_error, mean_squared_error, r2_score
import numpy as np

# Dataset
data = {
    'Area': [1000, 1500, 1800, 2000, 2500, 3000, 3500, 4000],
    'Bedrooms': [2, 3, 3, 4, 4, 5, 5, 6],
    'Age': [10, 8, 7, 6, 5, 4, 3, 2],
    'Price': [200, 300, 350, 400, 500, 600, 700, 800]
}

df = pd.DataFrame(data)

# Independent variables
X = df[['Area', 'Bedrooms', 'Age']]

# Dependent variable
y = df['Price']

# Train-test split
X_train, X_test, y_train, y_test = train_test_split(
    X, y, test_size=0.2, random_state=42
)

# Create model
model = LinearRegression()

# Train model
model.fit(X_train, y_train)

# Make predictions
y_pred = model.predict(X_test)

# Model parameters
print("Intercept:", model.intercept_)
print("Coefficients:", model.coef_)

# Predictions
print("Predicted Values:", y_pred)
print("Actual Values:", y_test.values)

# Evaluation
print("MAE:", mean_absolute_error(y_test, y_pred))
print("MSE:", mean_squared_error(y_test, y_pred))
print("RMSE:", np.sqrt(mean_squared_error(y_test, y_pred)))
print("R2 Score:", r2_score(y_test, y_pred))