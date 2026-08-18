# Multiple Linear Regression | Part 2 | Mathematical Formulation From Scratch

## 1. Introduction

Multiple Linear Regression is an extension of Simple Linear Regression where the dependent variable is predicted using two or more independent variables.

The general equation is:

[
\hat{y} = b_0 + b_1x_1 + b_2x_2 + \cdots + b_nx_n
]

Where:

* ( \hat{y} ) = predicted value
* ( b_0 ) = intercept
* ( b_1, b_2, \ldots, b_n ) = regression coefficients
* ( x_1, x_2, \ldots, x_n ) = independent variables

---

## 2. Example

Suppose we want to predict a student's salary based on:

* (x_1) = CGPA
* (x_2) = Years of Experience

The regression equation becomes:

[
\hat{y} = b_0 + b_1x_1 + b_2x_2
]

For every observation, the model produces a predicted value (\hat{y}).

---

## 3. Actual vs Predicted Value

Let the actual value be (y_i) and the predicted value be (\hat{y}_i).

The error or residual is:

[
e_i = y_i - \hat{y}_i
]

Therefore,

[
e_i = y_i - (b_0+b_1x_{i1}+b_2x_{i2}+\cdots+b_nx_{in})
]

The goal of Multiple Linear Regression is to find the best values of the coefficients that minimize these errors.

---

## 4. Cost Function

We use the **Sum of Squared Errors (SSE)**:

[
SSE = \sum_{i=1}^{m}(y_i-\hat{y}_i)^2
]

Substituting the regression equation:

[
SSE =
\sum_{i=1}^{m}
\left[
y_i-(b_0+b_1x_{i1}+b_2x_{i2}+\cdots+b_nx_{in})
\right]^2
]

Squaring the errors prevents positive and negative errors from cancelling each other.

The objective is:

[
\min SSE
]

---

## 5. Mathematical Formulation

For two independent variables:

[
\hat{y}*i=b_0+b_1x*{i1}+b_2x_{i2}
]

Therefore:

[
SSE =
\sum_{i=1}^{m}
(y_i-b_0-b_1x_{i1}-b_2x_{i2})^2
]

To minimize SSE, we differentiate it with respect to each parameter and set the derivatives equal to zero.

### With respect to (b_0):

[
\frac{\partial SSE}{\partial b_0}=0
]

### With respect to (b_1):

[
\frac{\partial SSE}{\partial b_1}=0
]

### With respect to (b_2):

[
\frac{\partial SSE}{\partial b_2}=0
]

This produces a system of **normal equations**.

---

## 6. Normal Equations

For two independent variables, the normal equations are:

[
\sum y =
mb_0+b_1\sum x_1+b_2\sum x_2
]

[
\sum x_1y =
b_0\sum x_1+b_1\sum x_1^2+b_2\sum x_1x_2
]

[
\sum x_2y =
b_0\sum x_2+b_1\sum x_1x_2+b_2\sum x_2^2
]

These equations can be solved simultaneously to obtain (b_0), (b_1), and (b_2).

---

## 7. Matrix Formulation

Multiple Linear Regression becomes much easier to represent using matrices.

The model can be written as:

[
\hat{y}=X\beta
]

Where:

[
X=
\begin{bmatrix}
1 & x_{11} & x_{12} & \cdots & x_{1n}\
1 & x_{21} & x_{22} & \cdots & x_{2n}\
\vdots & \vdots & \vdots & \ddots & \vdots\
1 & x_{m1} & x_{m2} & \cdots & x_{mn}
\end{bmatrix}
]

The first column contains 1s because it represents the intercept.

The coefficient vector is:

[
\beta=
\begin{bmatrix}
b_0\
b_1\
b_2\
\vdots\
b_n
\end{bmatrix}
]

And the target vector is:

[
y=
\begin{bmatrix}
y_1\
y_2\
\vdots\
y_m
\end{bmatrix}
]

Therefore:

[
\hat{y}=X\beta
]

---

## 8. Ordinary Least Squares Solution

The coefficients can be calculated using the **Ordinary Least Squares (OLS)** closed-form solution:

[
\boxed{\beta=(X^TX)^{-1}X^Ty}
]

Where:

* (X^T) = transpose of (X)
* (X^TX) = matrix multiplication of (X^T) and (X)
* ((X^TX)^{-1}) = inverse of (X^TX)
* (X^Ty) = matrix multiplication of (X^T) and (y)

This formula gives the coefficient values that minimize the sum of squared errors, provided (X^TX) is invertible.

---

## 9. Complete Flow

The mathematical process can be summarized as:

[
X,y
\rightarrow
X^TX
\rightarrow
(X^TX)^{-1}
\rightarrow
X^Ty
\rightarrow
\beta
\rightarrow
\hat{y}
]

So, Multiple Linear Regression mathematically finds the coefficients that produce the best-fitting hyperplane through the data.

## Key Takeaways

* Multiple Linear Regression uses two or more independent variables.
* The prediction equation is ( \hat{y}=b_0+b_1x_1+\cdots+b_nx_n ).
* Errors are measured using squared residuals.
* OLS minimizes the Sum of Squared Errors.
* Differentiation produces the normal equations.
* Matrix notation simplifies the mathematical formulation.
* The OLS coefficient formula is ( \beta=(X^TX)^{-1}X^Ty ).
