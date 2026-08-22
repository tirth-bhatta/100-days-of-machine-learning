# Gradient Descent From Scratch | End to End Gradient Descent | Gradient Descent Animation

## Overview

Gradient Descent is one of the most important optimization algorithms in Machine Learning. It is used to minimize a **loss or cost function** by continuously updating the model parameters in the direction that reduces the error.

In this topic, Gradient Descent is implemented **from scratch** to understand what happens internally instead of directly using a library function. The complete process is covered from the mathematical intuition to parameter updates and finally visualizing how the algorithm moves toward the minimum point.

## What is Gradient Descent?

Gradient Descent is an iterative optimization algorithm used to find the values of parameters that minimize a given cost function.

The basic idea is simple:

* Start with some initial parameter values.
* Calculate the cost produced by those parameters.
* Calculate the gradient of the cost function.
* Move the parameters in the opposite direction of the gradient.
* Repeat the process until the cost becomes minimum or stops changing significantly.

The algorithm can be understood as **walking downhill on a surface**. The gradient tells us the direction of the steepest increase, so moving in the opposite direction takes us toward the minimum.

## Why Do We Need Gradient Descent?

In Machine Learning, we usually want to find parameters that produce the smallest possible prediction error.

For example, in Linear Regression:

[
y = mx + b
]

Here:

* `m` = slope/weight
* `b` = intercept/bias

Different values of `m` and `b` produce different prediction errors. Our goal is to find the values of `m` and `b` that minimize the cost function.

Instead of trying every possible combination of parameters, Gradient Descent efficiently searches for better parameter values through repeated updates.

## Cost Function

For Linear Regression, a commonly used cost function is Mean Squared Error:

[
J(m,b)=\frac{1}{n}\sum_{i=1}^{n}(y_i-\hat{y_i})^2
]

where:

* `n` = number of training examples
* `y` = actual value
* `ŷ` = predicted value
* `J(m,b)` = cost function

The objective of Gradient Descent is:

[
\text{Minimize } J(m,b)
]

A lower cost means that the model's predictions are closer to the actual values.

## Gradient

The gradient tells us how much the cost function changes when a parameter changes.

For Linear Regression, we calculate the partial derivatives of the cost function with respect to `m` and `b`:

[
\frac{\partial J}{\partial m}
]

and

[
\frac{\partial J}{\partial b}
]

These derivatives tell us the direction in which the cost is increasing.

Therefore, we move in the **opposite direction** to reduce the cost.

## Parameter Update Rule

The general Gradient Descent update rule is:

[
\theta = \theta - \alpha \frac{\partial J}{\partial \theta}
]

where:

* `θ` = model parameter
* `α` = learning rate
* `∂J/∂θ` = gradient of the cost function

For Linear Regression:

[
m = m-\alpha\frac{\partial J}{\partial m}
]

[
b = b-\alpha\frac{\partial J}{\partial b}
]

This update is repeated for multiple iterations.

## Learning Rate

The **learning rate** controls how large each step is during optimization.

If the learning rate is too small:

* Training becomes very slow.
* The algorithm may require many iterations.

If the learning rate is too large:

* The algorithm may jump over the minimum.
* The cost can increase instead of decrease.
* The algorithm may fail to converge.

A suitable learning rate allows Gradient Descent to move toward the minimum efficiently.

## Gradient Descent From Scratch

The implementation follows this basic structure:

```python
m = 0
b = 0

learning_rate = 0.01
epochs = 1000

for i in range(epochs):

    y_pred = m * X + b

    dm = (-2 / len(X)) * np.sum(X * (y - y_pred))
    db = (-2 / len(X)) * np.sum(y - y_pred)

    m = m - learning_rate * dm
    b = b - learning_rate * db
```

Here, no ready-made optimization function is being used. The parameters are updated manually using the calculated gradients.

## Complete Flow

The complete Gradient Descent process can be summarized as:

```text
Initialize parameters
        ↓
Make predictions
        ↓
Calculate cost
        ↓
Calculate gradients
        ↓
Update parameters
        ↓
Check the cost
        ↓
Repeat
        ↓
Converged parameters
```

At every iteration, the model attempts to make the cost smaller.

## Gradient Descent Animation

The animation helps visualize what is happening during optimization.

Initially, the model parameters are far from their optimal values. As the iterations continue, Gradient Descent updates the parameters step by step.

The visualization shows:

```text
High Cost
   ↓
Parameter Update
   ↓
Lower Cost
   ↓
Parameter Update
   ↓
Even Lower Cost
   ↓
Minimum Cost
```

This makes it easier to understand that Gradient Descent does not immediately find the best parameters. It gradually approaches them through repeated updates.

## Convergence

When the algorithm reaches a point where further updates produce almost no improvement in the cost, it is said to have **converged**.

A typical cost curve looks like:

```text
Cost
 |
 |\
 | \
 |  \
 |   \
 |    \____
 |         \____
 |              \___
 |________________________ Iterations
```

The cost generally decreases as the number of iterations increases, assuming the learning rate and problem setup are appropriate.

## Important Parameters

The main components of Gradient Descent are:

| Parameter         | Purpose                        |
| ----------------- | ------------------------------ |
| Initial values    | Starting point of optimization |
| Learning Rate     | Controls step size             |
| Gradient          | Determines direction of update |
| Cost Function     | Measures model error           |
| Epochs/Iterations | Number of updates              |
| Model Parameters  | Values being optimized         |

## Advantages

* Simple and easy to implement.
* Works well with large datasets.
* Can optimize models with many parameters.
* Forms the foundation of many Machine Learning optimization techniques.
* Helps understand how model parameters are learned.

## Limitations

* Choosing the correct learning rate can be difficult.
* A very large learning rate can prevent convergence.
* A very small learning rate can make training slow.
* Feature scaling can be important for faster convergence.
* Gradient Descent can be affected by the shape of the cost function.

## Key Takeaway

Gradient Descent is the process of **iteratively adjusting model parameters to minimize a cost function**.

The most important idea is:

> **Calculate the gradient → move in the opposite direction → repeat until convergence.**

Understanding Gradient Descent from scratch provides the foundation for understanding how many Machine Learning algorithms actually learn their parameters. It also makes concepts such as optimization, loss functions, learning rates, epochs, convergence, and parameter updates much easier to understand.

This implementation covers the complete journey of Gradient Descent—from the mathematical formulation and parameter updates to the final animated visualization of the optimization process.
