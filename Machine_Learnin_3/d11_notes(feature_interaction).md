# Non-Linear Model Using Only Interaction Term

## Concept Overview

A **non-linear model using only interaction terms** is a regression approach where, instead of including all possible polynomial features (like squares, cubes, etc.), you only add terms that represent the multiplication (interaction) of two or more features. This lets you model cases where the combined effect of variables is not just the sum of their individual effects.

---

## What is an Interaction Term?

An **interaction term** is a feature created by multiplying two (or more) existing features together. In regression, this term allows you to model the scenario where the effect of one variable on the target depends on the value of another variable.

**Example:**

Suppose you are studying the effect of `TV` and `radio` advertising budgets on `sales`:

- **Linear Model:**  
  `sales = b0 + b1*TV + b2*radio`
- **Model with Interaction Term:**  
  `sales = b0 + b1*TV + b2*radio + b3*(TV*radio)`

Here, the `TV*radio` term captures the possibility that the effectiveness of TV ads is influenced by the amount spent on radio ads, and vice versa.

---

## Why Use Only the Interaction Term?

- Sometimes, you may observe or hypothesize that the main effect of each variable is linear, but the real-world outcome also depends on their joint effect.
- Adding only the interaction term allows the model to remain simple and interpretable, while still capturing important non-linear relationships.
- It avoids the explosion of features and potential overfitting that can happen if all polynomial terms are included.

---

## How to Implement in Python (Example)

Suppose you have a DataFrame `df` with columns `TV`, `radio`, and `sales`:

```python
import pandas as pd
from sklearn.linear_model import LinearRegression

# Create interaction term
df['TV_radio'] = df['TV'] * df['radio']

# Define features and target
X = df[['TV', 'radio', 'TV_radio']]
y = df['sales']

# Fit linear model
model = LinearRegression()
model.fit(X, y)
```

**Interpretation:**  
If the coefficient for the interaction term (`TV_radio`) is significant, it means the effect of TV advertising on sales depends on the radio advertising budget (or vice versa).

---

## Visualization

You can visualize the interaction effect by plotting predicted sales for different combinations of TV and radio budgets, or by plotting actual vs. predicted sales.

---

## Key Takeaways

- **Interaction terms** allow you to capture relationships where the combined effect of variables is non-additive.
- **Non-linear model using only interaction term** is a targeted way to introduce non-linearity without a large number of polynomial features.
- This approach is especially useful when you suspect variables interact but don’t want to overcomplicate the model.

---

## References

- [Scikit-learn: Polynomial and Interaction Features](https://scikit-learn.org/stable/modules/preprocessing.html#polynomial-features)
- You can find more context and code in the notebook: [`ds_b1_ml_2.ipynb` on GitHub](https://github.com/aicouncil/B1/blob/7b354e59d1e37b9feac52922a351beec230387a5/Machine_Learnin_3/ds_b1_ml_2.ipynb)
