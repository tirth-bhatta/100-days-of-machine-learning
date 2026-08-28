# Bias-Variance Trade-off | Overfitting and Underfitting in Machine Learning

## Introduction

When we train a Machine Learning model, our main goal is not only to perform well on the training data. The model should also perform well on new, unseen data.

Sometimes a model is too simple and cannot learn the important patterns. This is called **Underfitting**.

Sometimes a model is too complex and learns the training data, including its noise. This is called **Overfitting**.

The **Bias-Variance Trade-off** helps us understand the balance between these two problems.

---

# 1. What is Bias?

**Bias** is the error caused by making overly simple assumptions about the data.

A model with **high bias** is too simple and cannot capture the important patterns in the data.

### Example

Suppose the actual data follows a curved pattern, but we use a straight-line model.

The model will not be able to properly follow the curve.

Therefore:

**High Bias → Model is too simple → Underfitting**

### Simple Example

Imagine a student only studies a few topics before an exam.

The student does not learn enough of the actual subject.

Similarly, a high-bias model does not learn enough from the data.

---

# 2. What is Variance?

**Variance** describes how much a model changes when it is trained on different training datasets.

A model with **high variance** is very sensitive to the training data.

It may learn not only the actual pattern but also random noise.

Therefore:

**High Variance → Model is too complex → Overfitting**

### Simple Example

Imagine a student memorizes every question from one practice paper instead of understanding the subject.

If the actual exam contains different questions, the student may perform badly.

Similarly, a high-variance model may perform very well on training data but poorly on new data.

---

# 3. What is Underfitting?

**Underfitting** occurs when a Machine Learning model is too simple to learn the important patterns in the training data.

### Characteristics of Underfitting

- Model is too simple
- High Bias
- Low Variance
- Poor performance on training data
- Poor performance on test data
- Does not learn enough from the data

### Example

Using a straight line to represent highly curved data can cause underfitting.

```text
Actual Data:

     *       *
   *   *   *
 *       *       *
----------------------  ← Too simple model