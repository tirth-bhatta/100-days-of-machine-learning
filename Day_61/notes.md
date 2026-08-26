# 📈 Polynomial Regression | Machine Learning

> Polynomial Regression is used when the relationship between the input and output is not a straight line.

---

## 📚 What is Polynomial Regression?

Polynomial Regression is a type of regression used when the data follows a curved pattern.

In Linear Regression, we try to fit a straight line to the data.

But sometimes, the relationship between the input and output is curved. In that case, we use Polynomial Regression.

---

## 🤔 Why Do We Need Polynomial Regression?

Not all data follows a straight-line pattern.

For example, there can be a curved relationship between:

- Years of experience and salary
- Hours studied and exam marks
- Speed and fuel consumption

Polynomial Regression helps us understand and predict these curved patterns.

---

## ⚙️ How Does It Work?

Polynomial Regression adds extra features based on the original input.

For example, if:

X = 2

It can create:

- X = 2
- X² = 4
- X³ = 8

The model uses these values to understand the curved relationship in the data.

---

## 🔢 What is Degree?

The degree decides how much the line can curve.

- Degree 1 → Straight line
- Degree 2 → Simple curve
- Degree 3 → More complex curve

Using a very high degree can cause overfitting.

---

## 📊 Simple Example

Suppose we want to predict exam marks based on study hours.

| Study Hours | Marks |
|-------------|-------|
| 1 | 20 |
| 2 | 35 |
| 3 | 55 |
| 4 | 75 |
| 5 | 90 |

If the relationship between study hours and marks forms a curve, Polynomial Regression can be used to fit that curve.

---

## ✅ Advantages

- Can handle curved relationships
- More flexible than Linear Regression
- Can work well with non-linear data

---

## ❌ Disadvantages

- A high degree can cause overfitting
- Choosing the correct degree can be difficult
- The model can become more complex

---

## 🎯 Key Takeaway

Polynomial Regression is used when the relationship between variables is curved instead of a straight line.

It creates polynomial features such as X² and X³ to help the model learn more complex patterns.