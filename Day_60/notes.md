# 📦 Mini-Batch Gradient Descent

> Mini-Batch Gradient Descent is a variation of Gradient Descent that updates model parameters using a **small batch of training examples** at a time instead of using the entire dataset or only one example.

---

## 📚 Table of Contents

* ## 1. What is Mini-Batch Gradient Descent?
* ## 2. How It Works
* ## 3. Formula
* ## 4. Example
* ## 5. Batch GD vs SGD vs Mini-Batch GD
* ## 6. Advantages
* ## 7. Disadvantages
* ## 8. Key Takeaways

---

## 1. What is Mini-Batch Gradient Descent?

Mini-Batch Gradient Descent divides the training dataset into **small groups called mini-batches**.

For each update, the model calculates the gradient using one mini-batch and updates its parameters.

For example, if we have **10,000 training examples**, instead of using all 10,000 examples at once, we might use batches of **32, 64, or 128 examples**.

It provides a balance between:

* **Batch Gradient Descent** → uses the entire dataset
* **Stochastic Gradient Descent (SGD)** → uses one example
* **Mini-Batch Gradient Descent** → uses a small group of examples

---

## 2. How It Works

The basic process is:

1. Divide the training dataset into mini-batches.
2. Select one mini-batch.
3. Calculate the gradient using that mini-batch.
4. Update the model parameters.
5. Repeat for all mini-batches.
6. Repeat the process for multiple epochs.

### Simple Flow

```text
Training Dataset
       ↓
Split into Mini-Batches
       ↓
Mini-Batch 1 → Calculate Gradient → Update Parameters
       ↓
Mini-Batch 2 → Calculate Gradient → Update Parameters
       ↓
Mini-Batch 3 → Calculate Gradient → Update Parameters
       ↓
             ...
       ↓
      New Epoch
```

---

## 3. Formula

The parameter update is:

```text
θ = θ - η × ∇J_B(θ)
```

Where:

* `θ` = Model parameters
* `η` = Learning rate
* `∇J_B(θ)` = Gradient calculated using the current mini-batch
* `B` = Mini-batch

The gradient is calculated by averaging the gradients of the examples inside the mini-batch.

---

## 4. Example

Suppose we have:

```text
Dataset = 1,000 samples
Batch Size = 100
```

The dataset is divided into:

```text
Batch 1 → 100 samples
Batch 2 → 100 samples
Batch 3 → 100 samples
...
Batch 10 → 100 samples
```

The model updates its parameters after processing each batch.

Therefore, one complete pass through the dataset contains:

```text
10 updates = 1 epoch
```

---

## 5. Batch GD vs SGD vs Mini-Batch GD

| Method        | Data Used Per Update | Speed              | Stability            |
| ------------- | -------------------- | ------------------ | -------------------- |
| Batch GD      | Entire dataset       | Slower per update  | Very stable          |
| SGD           | 1 sample             | Fast updates       | Noisy                |
| Mini-Batch GD | Small batch          | Fast and efficient | More stable than SGD |

Mini-batch GD provides a practical compromise between the computational cost of full-batch training and the noisy updates of SGD.

---

## 6. Advantages

* ⚡ Faster parameter updates than Batch GD
* 💾 Requires less memory than full Batch GD
* 🎯 More stable than SGD
* 🖥️ Works well with parallel hardware such as GPUs
* 📈 Usually provides a good balance between speed and convergence
* 🔄 Suitable for large datasets

Mini-batches can also make better use of hardware acceleration because matrix operations can be processed efficiently in parallel.

---

## 7. Disadvantages

* Requires choosing a suitable **batch size**
* Training can still be somewhat noisy
* Too-small batches can behave similarly to SGD
* Too-large batches require more memory
* Learning rate may need adjustment when changing batch size

---

## 8. Key Takeaways

> 🔹 Mini-Batch Gradient Descent uses a **small subset of data** for each update.

> 🔹 It is a compromise between **Batch Gradient Descent and SGD**.

> 🔹 The **batch size** determines how many training examples are used for each update.

> 🔹 It is widely useful for training machine learning and deep learning models efficiently.

### 🧠 Remember

```text
Batch GD       → All samples
SGD            → 1 sample
Mini-Batch GD  → Small group of samples
```

**Mini-Batch GD = Balance between speed, stability, and memory usage.**
