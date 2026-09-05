# Ridge Regression Part 2 | Mathematical Formulation & Code from Scratch

Ridge Regression is a type of **Regularized Linear Regression**.

In Part 1, we learned how Linear Regression finds the best line for our data.

In Part 2, we will understand:

- What is Ridge Regression?
- Why do we need Ridge Regression?
- What is Regularization?
- What is L2 Regularization?
- What is Lambda (λ) / Alpha?
- Mathematical formulation
- Ridge Regression formula
- Implementation from scratch
- Complete Python code
- Example
- Output
- Effect of different alpha values
- Important points for beginners

---

# 1. What is Linear Regression?

Linear Regression tries to find a relationship between input features `X` and output `y`.

For one feature, the equation is:

y = b0 + b1x

Where:

- `y` = predicted output
- `b0` = intercept
- `b1` = coefficient
- `x` = input feature

For example:

If:

b0 = 2
b1 = 3

Then:

y = 2 + 3x

For x = 1:

y = 2 + 3(1)
y = 5

For x = 2:

y = 2 + 3(2)
y = 8

The model tries to find the best values of `b0` and `b1`.

---

# 2. Problem with Linear Regression

Sometimes Linear Regression can produce very large coefficients.

For example:

b1 = 500
b2 = -800
b3 = 1200

Large coefficients can make the model too sensitive to the training data.

This can cause:

**Overfitting**

Overfitting means:

> The model learns the training data too closely and performs poorly on new/unseen data.

To reduce this problem, we use:

# Regularization

---

# 3. What is Regularization?

Regularization is a technique used to prevent a machine learning model from becoming too complex.

The basic idea is:

```text
Normal Model
     |
     v
Minimize Prediction Error
     |
     v
Coefficients may become very large
     |
     v
Add Regularization
     |
     v
Penalize Large Coefficients