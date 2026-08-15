# Simple Linear Regression
# Mathematical Formulation + Coding From Scratch

# --------------------------------------------------
# 1. Import Libraries
# --------------------------------------------------
import numpy as np
import matplotlib.pyplot as plt


# --------------------------------------------------
# 2. Dataset
# --------------------------------------------------
X = np.array([1, 2, 3, 4, 5])
y = np.array([2, 4, 5, 4, 5])


# --------------------------------------------------
# 3. Mathematical Formulation
# --------------------------------------------------
# Equation of Simple Linear Regression:
#
#       y = mx + b
#
# where:
#       m = slope
#       b = intercept
#
# Formula for slope (m):
#
#       m = Σ(x - x̄)(y - ȳ) / Σ(x - x̄)²
#
# Formula for intercept (b):
#
#       b = ȳ - m*x̄


# --------------------------------------------------
# 4. Calculate Mean
# --------------------------------------------------
x_mean = np.mean(X)
y_mean = np.mean(y)


# --------------------------------------------------
# 5. Calculate Slope (m)
# --------------------------------------------------
numerator = np.sum((X - x_mean) * (y - y_mean))
denominator = np.sum((X - x_mean) ** 2)

m = numerator / denominator


# --------------------------------------------------
# 6. Calculate Intercept (b)
# --------------------------------------------------
b = y_mean - (m * x_mean)


# --------------------------------------------------
# 7. Print Model Parameters
# --------------------------------------------------
print("Slope (m):", m)
print("Intercept (b):", b)


# --------------------------------------------------
# 8. Make Predictions
# --------------------------------------------------
y_pred = m * X + b

print("Predicted Values:", y_pred)


# --------------------------------------------------
# 9. Predict for a New Value
# --------------------------------------------------
new_x = 6
prediction = m * new_x + b

print("Prediction for X =", new_x, ":", prediction)


# --------------------------------------------------
# 10. Visualization
# --------------------------------------------------
plt.scatter(X, y, label="Actual Data")
plt.plot(X, y_pred, label="Regression Line")

plt.xlabel("X")
plt.ylabel("Y")
plt.title("Simple Linear Regression From Scratch")
plt.legend()
plt.show()