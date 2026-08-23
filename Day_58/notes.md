# Batch Gradient Descent with Code Demo

## Overview

Batch Gradient Descent is an optimization algorithm used to minimize a loss or cost function in Machine Learning. It is mainly used while training models such as **Linear Regression, Logistic Regression, and Neural Networks**.

The main idea is simple: calculate the error using the **entire training dataset**, calculate the gradient of the cost function, and then update the model parameters in the direction that reduces the error.

---

## What is Gradient Descent?

Gradient Descent is an iterative optimization algorithm that finds the minimum value of a cost function.

For a machine learning model, we start with some initial values for the parameters. The algorithm then repeatedly:

1. Makes predictions.
2. Calculates the error.
3. Calculates the gradient.
4. Updates the parameters.
5. Repeats the process until the cost becomes sufficiently small or the maximum number of iterations is reached.

The general parameter update rule is:

[
\theta = \theta - \alpha \frac{\partial J(\theta)}{\partial \theta}
]

Where:

* (\theta) = model parameter
* (\alpha) = learning rate
* (J(\theta)) = cost function
* (\frac{\partial J}{\partial \theta}) = gradient of the cost function

---

## What is Batch Gradient Descent?

In **Batch Gradient Descent**, the gradient is calculated using **all training examples before updating the model parameters**.

Suppose our dataset contains 1,000 training examples. In one iteration, Batch Gradient Descent uses all 1,000 examples to calculate the gradient and then performs one parameter update.

So:

**1 Iteration → Complete Dataset → Calculate Gradient → Update Parameters**

This makes Batch Gradient Descent different from other variants such as:

* Batch Gradient Descent → Uses the entire dataset
* Stochastic Gradient Descent → Uses one sample at a time
* Mini-Batch Gradient Descent → Uses a small batch of samples

---

## Cost Function

For Linear Regression, a commonly used cost function is Mean Squared Error:

[
J(m,b)=\frac{1}{n}\sum_{i=1}^{n}(y_i-(mx_i+b))^2
]

Where:

* (m) = slope
* (b) = intercept
* (x_i) = input value
* (y_i) = actual output
* (n) = number of training examples

The goal of Gradient Descent is to find values of (m) and (b) that minimize this cost.

---

## Batch Gradient Descent Process

For every iteration:

### Step 1: Make Predictions

Using the current values of (m) and (b):

[
\hat{y}=mx+b
]

### Step 2: Calculate the Error

[
error = \hat{y}-y
]

### Step 3: Calculate Gradients

For Linear Regression:

[
\frac{\partial J}{\partial m}
=============================

\frac{2}{n}\sum x_i(\hat{y_i}-y_i)
]

[
\frac{\partial J}{\partial b}
=============================

\frac{2}{n}\sum(\hat{y_i}-y_i)
]

### Step 4: Update Parameters

[
m = m-\alpha\frac{\partial J}{\partial m}
]

[
b = b-\alpha\frac{\partial J}{\partial b}
]

### Step 5: Repeat

The process continues until the cost function converges.

---

## Code Demo From Scratch

Below is a simple implementation of Batch Gradient Descent without using a machine learning library.

```python
import numpy as np
import matplotlib.pyplot as plt

# Dataset
X = np.array([1, 2, 3, 4, 5])
y = np.array([2, 4, 6, 8, 10])

# Initial parameters
m = 0
b = 0

# Hyperparameters
learning_rate = 0.01
epochs = 1000

n = len(X)

# Batch Gradient Descent
for i in range(epochs):

    # Prediction
    y_pred = m * X + b

    # Error
    error = y_pred - y

    # Gradients
    dm = (2 / n) * np.sum(X * error)
    db = (2 / n) * np.sum(error)

    # Update parameters
    m = m - learning_rate * dm
    b = b - learning_rate * db

print("Slope:", m)
print("Intercept:", b)

# Predictions
y_pred = m * X + b

print("Predictions:", y_pred)

# Visualization
plt.scatter(X, y)
plt.plot(X, y_pred)
plt.xlabel("X")
plt.ylabel("y")
plt.title("Batch Gradient Descent")
plt.show()
```

---

## Understanding the Code

### Initial Parameters

```python
m = 0
b = 0
```

We initially assume that both the slope and intercept are zero.

The algorithm will gradually find better values.

### Learning Rate

```python
learning_rate = 0.01
```

The learning rate controls the size of each update.

A very small learning rate can make training slow, while a very large learning rate can cause the algorithm to overshoot the minimum.

### Number of Epochs

```python
epochs = 1000
```

This determines how many times the complete dataset will be used to calculate the gradient and update the parameters.

### Prediction

```python
y_pred = m * X + b
```

The model calculates predictions using the current values of (m) and (b).

### Calculate Error

```python
error = y_pred - y
```

The difference between predicted and actual values gives the error.

### Calculate Gradient

```python
dm = (2 / n) * np.sum(X * error)
db = (2 / n) * np.sum(error)
```

These lines calculate the gradients for the slope and intercept.

Because Batch Gradient Descent uses the **whole dataset**, `np.sum()` processes all training examples before the parameters are updated.

### Update Parameters

```python
m = m - learning_rate * dm
b = b - learning_rate * db
```

The parameters move in the opposite direction of the gradient.

This is the key step of Gradient Descent.

---

## Why Do We Move Opposite to the Gradient?

The gradient points toward the direction of the **steepest increase** in the cost function.

We want to minimize the cost.

Therefore, we move in the opposite direction:

[
\text{New Parameter}
====================

## \text{Old Parameter}

\text{Learning Rate}\times\text{Gradient}
]

This gradually moves the model toward the minimum of the cost function.

---

## Batch vs Stochastic vs Mini-Batch

| Method        | Data Used Per Update | Speed          | Stability   |
| ------------- | -------------------- | -------------- | ----------- |
| Batch GD      | Entire dataset       | Slower         | Very stable |
| Stochastic GD | One sample           | Faster updates | Noisy       |
| Mini-Batch GD | Small batch          | Fast           | Balanced    |

Batch Gradient Descent gives a more accurate gradient because every training example is considered before each update.

However, for very large datasets, processing the entire dataset for every update can become computationally expensive.

---

## Advantages of Batch Gradient Descent

* Uses the complete dataset for every update.
* Produces a stable and consistent gradient.
* Works well for smaller datasets.
* Easy to understand and implement.
* Suitable for convex optimization problems such as Linear Regression.

## Disadvantages

* Can be slow for very large datasets.
* Requires more computation per iteration.
* Requires the complete dataset during each update.
* Can consume significant memory for large datasets.

---

## Important Hyperparameter: Learning Rate

The learning rate is one of the most important parameters in Gradient Descent.

### Learning Rate Too Small

The algorithm takes very small steps toward the minimum.

**Result:** Training becomes very slow.

### Learning Rate Too Large

The algorithm may jump over the minimum.

**Result:** The cost may increase or fail to converge.

### Suitable Learning Rate

The algorithm gradually moves toward the minimum.

**Result:** Faster and stable convergence.

---

## Batch Gradient Descent in One Line

The complete idea can be summarized as:

> **Use the entire dataset to calculate the gradient, then update the parameters once.**

For every iteration:

```text
Complete Dataset
       ↓
Make Predictions
       ↓
Calculate Error
       ↓
Calculate Gradient
       ↓
Update Parameters
       ↓
Repeat
```

---

## Key Takeaways

* Batch Gradient Descent is an optimization algorithm.
* It uses the **entire training dataset** for every parameter update.
* It minimizes a cost function by moving parameters opposite to the gradient.
* The learning rate controls the size of parameter updates.
* It is stable but can be computationally expensive for large datasets.
* It is commonly used for understanding how machine learning models learn their parameters.
* The same fundamental idea of calculating gradients and updating parameters is used in many more advanced machine learning algorithms.

---

## Conclusion

Batch Gradient Descent provides a clear foundation for understanding model training. Instead of directly calculating the best parameters, the algorithm starts with initial values and gradually improves them by repeatedly reducing the cost function.

The most important concept to remember is:

**Gradient tells us which direction increases the cost, so we move in the opposite direction to minimize it.**

In the next step, the same concept can be extended to **Mini-Batch Gradient Descent and Stochastic Gradient Descent**, which are more practical for large datasets.
