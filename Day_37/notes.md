# Handling Missing Categorical Data | Simple Imputer | Most Frequent Imputation | Missing Category Imputation

![My Image](./image.png)

## 📌 Overview
Categorical features often contain missing values due to incomplete data collection or user input. Since machine learning models cannot work with missing values directly, we need to replace them using suitable imputation techniques.

---

# 1️⃣ Most Frequent Imputation

## What is Most Frequent Imputation?

Most Frequent Imputation replaces missing values with the category that appears most frequently (Mode) in the dataset.

It is one of the simplest and most commonly used methods for handling missing categorical data.

### Example

| Color |
|--------|
| Red |
| Blue |
| Red |
| NaN |
| Red |

Most frequent value = **Red**

After imputation:

| Color |
|--------|
| Red |
| Blue |
| Red |
| Red |
| Red |

---

## Advantages
- Simple and fast
- Easy to implement
- Works well when missing values are few
- Preserves dataset size

---

## Disadvantages
- Can increase the frequency of the dominant category
- May introduce bias
- Reduces data variability if many values are missing

---

# 2️⃣ Simple Imputer (Most Frequent Strategy)

Scikit-Learn provides the **SimpleImputer** class to automatically replace missing categorical values.

### Syntax

```python
from sklearn.impute import SimpleImputer

imputer = SimpleImputer(strategy="most_frequent")
```

### Example

```python
import pandas as pd
from sklearn.impute import SimpleImputer

df = pd.DataFrame({
    "Gender": ["Male", "Female", None, "Male", None]
})

imputer = SimpleImputer(strategy="most_frequent")

df["Gender"] = imputer.fit_transform(df[["Gender"]]).ravel()

print(df)
```

### Output

```
   Gender
0    Male
1  Female
2    Male
3    Male
4    Male
```

---

# 3️⃣ Missing Category Imputation

Instead of replacing missing values with the most common category, we create a **new category** such as:

- Missing
- Unknown
- Not Available

This allows the model to learn that the value was originally missing.

### Example

Before

| City |
|------|
| Delhi |
| Mumbai |
| NaN |
| Chennai |

After

| City |
|------|
| Delhi |
| Mumbai |
| Missing |
| Chennai |

---

## Using Pandas

```python
df["City"] = df["City"].fillna("Missing")
```

---

## Advantages
- Preserves information about missing values
- Prevents overusing the most frequent category
- Useful when missing values have meaning

---

## Disadvantages
- Adds a new category to the dataset
- May slightly increase feature dimensionality after encoding

---

# 📊 Comparison

| Method | Replaces Missing With | Best Use Case |
|---------|-----------------------|---------------|
| Most Frequent Imputation | Mode of the column | Few missing values |
| Missing Category Imputation | New category (Missing/Unknown) | Missing values may carry useful information |

---

# 🎯 Key Points

- Missing categorical data must be handled before training a model.
- **Most Frequent Imputation** replaces missing values with the mode.
- **SimpleImputer(strategy="most_frequent")** automates this process in Scikit-Learn.
- **Missing Category Imputation** creates a separate category like `"Missing"` or `"Unknown"`.
- Choose the method based on the nature of your data and the percentage of missing values.