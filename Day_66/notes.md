# Ridge Regression Part 4 — 5 Key Points

Today I learned the **5 most important points about Ridge Regression** and why regularization is useful in Machine Learning.

### 1. Ridge Regression reduces overfitting

Ridge Regression adds a **penalty** to the model when the coefficients become too large.

Instead of only minimizing the prediction error, it also tries to keep the coefficients small.

So:

**Large coefficients → Higher penalty → Simpler model → Less overfitting**

---

### 2. It uses L2 Regularization

Ridge Regression uses **L2 regularization**.

The cost function becomes:

**Cost = MSE + α × Σ(coefficient²)**

Here:

* **MSE** → Prediction error
* **α (alpha)** → Controls the strength of regularization
* **coefficient²** → Penalty for large coefficients

The larger the coefficient, the larger the penalty.

---

### 3. Alpha controls regularization

The **α (alpha)** value decides how strongly Ridge Regression penalizes large coefficients.

* **α = 0** → Same as Linear Regression
* **Small α** → Weak regularization
* **Large α** → Strong regularization

If alpha becomes too large, the model can become **too simple and underfit**.

So we need to choose a suitable alpha.

---

### 4. Ridge does NOT usually make coefficients exactly zero

This is an important difference between **Ridge and Lasso Regression**.

**Ridge:**
Reduces coefficients but usually keeps them non-zero.

**Lasso:**
Can reduce some coefficients exactly to **0**, which can help with feature selection.

So remember:

**Ridge → Shrinks coefficients**

**Lasso → Shrinks + can eliminate features**

---

### 5. Ridge is useful when features are correlated

When multiple features are highly related to each other, normal Linear Regression can produce unstable or very large coefficients.

Ridge Regression controls these coefficients and makes the model more stable.

This makes Ridge especially useful when:

* There are many features
* Features are correlated
* The model is overfitting
* Coefficients are becoming very large

---

## 🧠 Easy Way to Remember

**Ridge = Reduce coefficient size**

Think:

> **Ridge puts a "limit" on how big the coefficients want to become.**

### Today's takeaway:

**Ridge Regression = Linear Regression + L2 Regularization**

It helps create a **simpler, more stable model that is less likely to overfit.**
