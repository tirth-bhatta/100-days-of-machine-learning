# Ridge Regression Part 1

## What is Ridge Regression?

Ridge Regression is a **regularized version of Linear Regression**. It is used mainly to reduce **overfitting** and control large model coefficients.

### Simple Idea

Normal Linear Regression tries to find the best line by minimizing the prediction error.

Ridge Regression does the same thing, but it also **penalizes large coefficients**.

> **Ridge Regression = Linear Regression + L2 Regularization**

---

## Why Ridge Regression?

In Linear Regression, coefficients can become very large, especially when features are highly correlated.

Large coefficients can make the model:

- More sensitive to small changes
- Unstable
- More likely to overfit

Ridge solves this by adding a penalty to large coefficients.

---

## Ridge Regression Formula

Normal Linear Regression minimizes:

$$
RSS = \sum_{i=1}^{n}(y_i-\hat{y_i})^2
$$

Ridge Regression adds an L2 penalty:

$$
J = RSS + \lambda\sum_{j=1}^{m}\beta_j^2
$$

Where:

- $y_i$ = Actual value
- $\hat{y_i}$ = Predicted value
- $\beta_j$ = Model coefficient
- $\lambda$ = Regularization strength

The important part is:

$$
\lambda\sum\beta_j^2
$$

This is called **L2 Regularization**.

---

## What is Lambda (λ)?

Lambda controls how strongly the coefficients are penalized.

| Lambda | Effect |
|---|---|
| `0` | Same as Linear Regression |
| Small | Small regularization |
| Large | Strong regularization |
| Very large | Can cause underfitting |

As $\lambda$ increases, the coefficients generally become smaller.

---

## Geometric Intuition

Ridge Regression tries to find a good model while keeping the coefficients small.

Think of it as:

```text
Good Prediction
      +
Small Coefficients
      ↓
Ridge Regression