# Ridge Regression Part 3 | Gradient Descent

## 📌 What is this?

In Part 2, we learned the mathematics behind Ridge Regression.

Today, we will understand **how the model actually learns its weights using Gradient Descent**.

---

## 🧠 What is Gradient Descent?

Gradient Descent is simply a method that helps the model find **better weights step by step**.

Imagine you are trying to find the lowest point of a hill.

You take a step down → check again → take another step → keep going.

The model does the same thing:

```text
Start with random/zero weights
        ↓
Make predictions
        ↓
Check how wrong they are
        ↓
Adjust the weights
        ↓
Repeat
        ↓
Better predictions
```

---

## 🎯 Why do we need it?

Suppose our data is:

```text
Hours Studied    Marks
      1            30
      2            40
      3            50
      4            60
```

The model needs to learn the relationship between:

```text
Hours Studied → Marks
```

At first, it doesn't know the correct weight.

It might start with:

```text
weight = 0
```

Then Gradient Descent slowly changes the weight until the predictions become better.

---

## 🧮 Simple Example

Suppose:

```text
x = 2
weight = 5
bias = 1
```

Prediction:

```text
prediction = (2 × 5) + 1

prediction = 11
```

If the actual answer is:

```text
actual = 15
```

then the model made a mistake.

Gradient Descent uses this mistake to decide:

> "I need to change my weight and bias."

It keeps doing this again and again.

---

## 🔐 Where does Ridge Regression come in?

Normal Linear Regression only cares about prediction error.

Ridge Regression also says:

> "Don't make the weights unnecessarily large."

So Ridge adds a small penalty to large weights.

This is called **L2 Regularization**.

```text
Linear Regression
        ↓
Reduce prediction error

Ridge Regression
        ↓
Reduce prediction error
        +
Keep weights smaller
```

---

## 🔢 What is Lambda?

Lambda (`λ`) controls how strong the penalty is.

```text
λ = 0
↓
No regularization

Small λ
↓
Small penalty

Large λ
↓
Strong penalty
```

So:

```text
Large λ → smaller weights
Small λ → larger freedom for weights
```

---

## 💡 Important Point

Ridge does **not** force the weights to become exactly zero.

It usually pushes them **closer to zero**.

This can help reduce overfitting.

---

## ⚙️ How Gradient Descent Works in Ridge

Every iteration follows these simple steps:

```text
1. Make prediction

2. Find the error

3. Calculate how the weights should change

4. Apply Ridge's penalty

5. Update the weights

6. Update the bias

7. Repeat
```

That's basically it.

---

## 🐍 Python Implementation From Scratch

We can implement a simple Ridge Regression model without using Scikit-learn.

```python
import numpy as np


class RidgeRegression:

    def __init__(self, learning_rate=0.01, lambda_=0.1, iterations=1000):

        self.learning_rate = learning_rate
        self.lambda_ = lambda_
        self.iterations = iterations

        self.weights = None
        self.bias = 0

    def fit(self, X, y):

        # Number of data points
        m = len(X)

        # Start weights with zero
        self.weights = np.zeros(X.shape[1])

        # Start bias with zero
        self.bias = 0

        for i in range(self.iterations):

            # Make predictions
            predictions = np.dot(X, self.weights) + self.bias

            # Find error
            error = predictions - y

            # Calculate weight gradient
            dw = (1 / m) * np.dot(X.T, error)

            # Add Ridge penalty
            dw += (self.lambda_ / m) * self.weights

            # Calculate bias gradient
            db = (1 / m) * np.sum(error)

            # Update weights
            self.weights -= self.learning_rate * dw

            # Update bias
            self.bias -= self.learning_rate * db

    def predict(self, X):

        return np.dot(X, self.weights) + self.bias


# -------------------------
# Example Data
# -------------------------

X = np.array([
    [1],
    [2],
    [3],
    [4],
    [5]
])

y = np.array([
    3,
    5,
    7,
    9,
    11
])


# -------------------------
# Create Model
# -------------------------

model = RidgeRegression(
    learning_rate=0.01,
    lambda_=0.1,
    iterations=1000
)


# -------------------------
# Train Model
# -------------------------

model.fit(X, y)


# -------------------------
# Make Predictions
# -------------------------

predictions = model.predict(X)


# -------------------------
# Display Results
# -------------------------

print("Ridge Regression")
print("----------------")

print("Weight:", model.weights)
print("Bias:", model.bias)

print("\nPredictions:")

for prediction in predictions:
    print(round(prediction, 2))
```

---

## 🧪 Example Output

Your exact values can be slightly different.

```text
Ridge Regression
----------------
Weight: [2.0...]
Bias: 0.9...

Predictions:
2.9
4.9
6.9
8.9
10.9
```

The predictions are close to:

```text
3
5
7
9
11
```

That means the model learned the relationship successfully.

---

## 🔍 The Most Important Part of the Code

This line calculates the normal gradient:

```python
dw = (1 / m) * np.dot(X.T, error)
```

Then we add Ridge regularization:

```python
dw += (self.lambda_ / m) * self.weights
```

That **second line is what makes this Ridge Regression**.

Without it, we would have normal Linear Regression using Gradient Descent.

---

## 📚 What We Learned Today

```text
Gradient Descent
      ↓
Helps the model learn better weights

Ridge Regression
      ↓
Adds a penalty for large weights

Lambda
      ↓
Controls the strength of the penalty
```

### In one sentence:

> **Gradient Descent repeatedly improves the model's weights, while Ridge Regularization prevents those weights from becoming unnecessarily large.**

---

## 📁 Project Structure

```text
ridge-regression-part-3/
│
├── README.md
└── ridge_gradient_descent.py
```

---

## 🚀 Run the Project

Install NumPy:

```bash
pip install numpy
```

Run:

```bash
python ridge_gradient_descent.py
```

---

## 📌 Git Commands

```bash
git add .
git commit -m "Add Ridge Regression Gradient Descent"
git push
```

---

## 🔥 Today's Topic

**Ridge Regression Part 3 | Gradient Descent | Regularized Linear Models**

Next:

**Ridge Regression Part 4 | Complete Implementation & Comparison**
