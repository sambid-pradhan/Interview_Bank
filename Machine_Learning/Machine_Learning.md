**Source:** ML Fundamentals · Conceptual Interview Question

## Question

1. What is **overfitting** in machine learning? How can you recognize it, and what techniques help prevent it?

## Answer

**Overfitting** occurs when a machine learning model learns not only the underlying patterns in the training data but also the noise and random fluctuations. As a result:

- **Training accuracy:** Very high
- **Test/Validation accuracy:** Low

The model performs well on data it has seen but fails to generalize to unseen data.

![Underfitting vs. good fit vs. overfitting — polynomial regression with degrees 1, 4, and 15](images/overfitting-underfitting.png)

*Source: [scikit-learn — Underfitting vs. Overfitting](https://scikit-learn.org/stable/auto_examples/model_selection/plot_underfitting_overfitting.html)*

The diagram shows the same noisy data fit with three polynomial models:

- **Degree 1 (left):** Too simple — underfitting (high bias).
- **Degree 4 (middle):** Tracks the true function well — good generalization.
- **Degree 15 (right):** Wiggles through every training point — overfitting (high variance).

### Example

Imagine predicting house prices.

- A good model learns that **larger houses generally cost more**.
- An overfit model also learns that **the third house in the dataset had a blue door and cost $500,000**, treating that coincidence as an important pattern.

This hurts performance on new houses.

### Signs of Overfitting

- Very low training error but high validation/test error.
- Large gap between training and validation accuracy.
- Model complexity is too high compared to the amount of data.

### How to Avoid Overfitting


| Technique                     | Description                                                                                  |
| ----------------------------- | -------------------------------------------------------------------------------------------- |
| **More training data**        | Gives the model more representative examples and reduces memorization.                       |
| **Cross-validation**          | Ensures the model generalizes well across different data splits.                             |
| **Regularization (L1/L2)**    | Penalizes large weights, encouraging simpler models.                                         |
| **Reduce model complexity**   | Use fewer features, shallower trees, or fewer neural network layers.                         |
| **Pruning (Decision Trees)**  | Remove branches that capture noise instead of useful patterns.                               |
| **Early stopping**            | Stop training when validation performance stops improving.                                   |
| **Dropout (Neural Networks)** | Randomly deactivate neurons during training to prevent co-adaptation.                        |
| **Feature selection**         | Remove irrelevant or redundant features.                                                     |
| **Data augmentation**         | Create additional training examples (common for images, audio, text).                        |
| **Ensemble methods**          | Methods like Random Forest or Gradient Boosting often generalize better than a single model. |


### Bias-Variance Perspective

Overfitting is a **high variance** problem:

- The model is overly sensitive to the training data.
- Small changes in the training set can lead to very different predictions.

### Interview Answer (30–45 seconds)

> "Overfitting occurs when a model learns the training data too well, including noise and outliers, instead of the underlying patterns. It results in high training accuracy but poor performance on unseen data. We can prevent overfitting by using more training data, cross-validation, regularization techniques like L1/L2, reducing model complexity, early stopping, dropout in neural networks, pruning decision trees, feature selection, and data augmentation. The goal is to build a model that generalizes well rather than memorizing the training data."

---

**Source:** ML Fundamentals · Conceptual Interview Question

## Question

2. What is **underfitting** in machine learning? How can you recognize it, and what techniques help prevent it?

## Answer

**Underfitting** occurs when a machine learning model is **too simple** to capture the underlying patterns in the data. As a result, it performs poorly on both the training data and unseen test data.

- **Training accuracy:** Low
- **Test/Validation accuracy:** Low

The model fails to learn the relationships in the data.

![Underfitting vs. good fit vs. overfitting — polynomial regression with degrees 1, 4, and 15](images/overfitting-underfitting.png)

*Source: [scikit-learn — Underfitting vs. Overfitting](https://scikit-learn.org/stable/auto_examples/model_selection/plot_underfitting_overfitting.html)*

The left panel (degree 1) is a straight line that cannot follow the curve — classic underfitting.

### Example

Imagine predicting house prices.

- A good model learns that factors like **size, location, and number of bedrooms** influence price.
- An underfit model might simply predict the **average house price for every house**, ignoring all the features.

This leads to poor predictions for both training and new data.

### Signs of Underfitting

- High training error.
- High validation/test error.
- Training and validation performance are both poor and close to each other.
- The model has high bias.

### How to Avoid Underfitting


| Technique                      | Description                                                                                                                              |
| ------------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------- |
| **Increase model complexity**  | Use a more powerful model (e.g., deeper neural network, deeper decision tree).                                                           |
| **Add more relevant features** | Provide the model with more useful information.                                                                                          |
| **Reduce regularization**      | Lower L1/L2 penalties if they are preventing learning.                                                                                   |
| **Train for more epochs**      | Neural networks may need more training time to converge.                                                                                 |
| **Feature engineering**        | Create meaningful features or polynomial features to capture complex relationships.                                                      |
| **Use a better algorithm**     | Switch from a simple model (e.g., Linear Regression) to a more expressive one (e.g., Random Forest or Gradient Boosting) if appropriate. |
| **Hyperparameter tuning**      | Optimize parameters such as tree depth, learning rate, or number of estimators.                                                          |


### Bias-Variance Perspective

Underfitting is a **high bias** problem:

- The model makes overly simplistic assumptions.
- It cannot capture the true relationship between inputs and outputs.

### Overfitting vs. Underfitting


| Aspect            | Underfitting | Overfitting |
| ----------------- | ------------ | ----------- |
| Model complexity  | Too simple   | Too complex |
| Training accuracy | Low          | Very high   |
| Test accuracy     | Low          | Low         |
| Training error    | High         | Very low    |
| Test error        | High         | High        |
| Bias              | High         | Low         |
| Variance          | Low          | High        |


### Interview Answer (30–45 seconds)

> "Underfitting occurs when a model is too simple to learn the underlying patterns in the data, resulting in poor performance on both training and test datasets. It is a high-bias problem. We can reduce underfitting by increasing model complexity, adding relevant features, reducing excessive regularization, training for more epochs, performing feature engineering, tuning hyperparameters, or using a more expressive algorithm. The goal is to make the model flexible enough to capture the true patterns without becoming so complex that it overfits."

---

**Source:** ML Fundamentals · Conceptual Interview Question

## Question

3. What is **regularization** in machine learning? Why is it needed, and what are the main types?

## Answer

**Regularization** is a technique used to **prevent overfitting** by adding a penalty to the model's loss function. This discourages the model from learning overly complex patterns and helps it generalize better to unseen data.

### Why is it Needed?

Without regularization:

- The model may assign very large weights to some features.
- It starts fitting noise in the training data.
- Training accuracy becomes very high, but test accuracy drops.

Regularization keeps the model simpler by penalizing large weights.

### Mathematical Form

Original loss function:

$$
\mathcal{L}(\mathbf{w}) = \text{Prediction Error}
$$

With regularization:

$$
\mathcal{L}(\mathbf{w}) = \text{Prediction Error} + \lambda \cdot \text{Penalty}(\mathbf{w})
$$

where:

- **$\lambda$ (lambda)** controls the strength of regularization.
- Larger $\lambda$ → simpler model (higher bias, lower variance).
- Smaller $\lambda$ → model focuses more on fitting the training data.

### Types of Regularization

![L1 (diamond), L2 (circle), and Elastic Net (rounded diamond) penalty contours where penalty = 1](images/l1-l2-elastic-net-penalties.png)

*Source: [scikit-learn — SGD: Penalties](https://scikit-learn.org/stable/auto_examples/linear_model/plot_sgd_penalties.html)*

#### 1. L1 Regularization (Lasso)

Penalty:

$$
\text{Penalty}_{\text{L1}} = \lambda \sum_{i=1}^{p} \lvert w_i \rvert
$$

**Characteristics:**

- Uses the absolute value of weights.
- Can shrink some weights exactly to **0**.
- Performs **feature selection** automatically.
- Useful when many features are irrelevant.

**Example:**

```
Before:
Age = 2.1
Salary = 0.8
ZipCode = 0.5

After L1:
Age = 2.0
Salary = 0.6
ZipCode = 0
```

#### 2. L2 Regularization (Ridge)

Penalty:

$$
\text{Penalty}_{\text{L2}} = \lambda \sum_{i=1}^{p} w_i^2
$$

**Characteristics:**

- Uses squared weights.
- Reduces weights but rarely makes them exactly zero.
- Keeps all features while preventing any single feature from dominating.
- Most commonly used regularization technique.

#### 3. Elastic Net

Combines both L1 and L2:

$$
\mathcal{L}(\mathbf{w}) = \text{Error} + \lambda_1 \sum_{i=1}^{p} \lvert w_i \rvert + \lambda_2 \sum_{i=1}^{p} w_i^2
$$

Used when:

- There are many correlated features.
- You want both feature selection (L1) and stable coefficients (L2).

### Effect of $\lambda$ (Lambda)


| $\lambda$ | Effect                                        |
| --------- | --------------------------------------------- |
| $\lambda = 0$ | No regularization; higher risk of overfitting |
| Small $\lambda$ | Slight penalty; good balance                  |
| Large $\lambda$ | Simpler model; may underfit if too large      |


### Intuition

Imagine you're drawing a curve through data points.

- **Without regularization:** The curve twists and bends to pass through nearly every point (overfitting).
- **With regularization:** The curve is smoother and captures the overall trend rather than the noise.

Geometrically, regularization restricts coefficients to a constraint region. The optimal solution is where the loss contours first touch that region:

![Lasso (L1 diamond) vs. Ridge (L2 circle) — loss contours intersect the constraint region](images/lasso-ridge-coefficient-paths.png)

*Source: [ethen8181 — Regularization](http://ethen8181.github.io/machine-learning/regularization/regularization.html)*

- **Lasso (diamond):** Sharp corners on the axes → intersection often sets a coefficient to **exactly zero** (feature selection).
- **Ridge (circle):** Smooth boundary → coefficients shrink but **rarely become zero**.

### Interview Answer (30–45 seconds)

> "Regularization is a technique used to prevent overfitting by adding a penalty term to the loss function. This penalty discourages the model from assigning very large weights to features, resulting in a simpler model that generalizes better. The two main types are **L1 (Lasso)**, which can shrink some feature weights to zero and perform feature selection, and **L2 (Ridge)**, which reduces weights without eliminating features. The regularization strength is controlled by the lambda parameter—higher lambda means stronger regularization."

---

**Source:** ML Fundamentals · Conceptual Interview Question

## Question

4. Explain **Lasso** and **Ridge** regularization. How do they help in **Elastic Net** regularization?

## Answer

### 1. Lasso Regularization (L1)

Lasso adds the **absolute value of the coefficients** as a penalty to the loss function.

**Formula:**

$$
\mathcal{L}(\mathbf{w}) = \text{MSE} + \lambda \sum_{i=1}^{p} \lvert w_i \rvert
$$

#### What does Lasso do?

- Shrinks coefficient values.
- Can make some coefficients **exactly zero**.
- Automatically performs **feature selection**.
- Produces a simpler, more interpretable model.

**Example:**


| Feature  | Before | After Lasso |
| -------- | ------ | ----------- |
| Age      | 2.4    | 2.1         |
| Salary   | 1.8    | 1.2         |
| Zip Code | 0.6    | **0**       |


Here, **Zip Code** is removed from the model.

**Best when:**

- Many features are irrelevant.
- You want automatic feature selection.

### 2. Ridge Regularization (L2)

Ridge adds the **square of the coefficients** as a penalty.

**Formula:**

$$
\mathcal{L}(\mathbf{w}) = \text{MSE} + \lambda \sum_{i=1}^{p} w_i^2
$$

#### What does Ridge do?

- Shrinks coefficients toward zero.
- Rarely makes coefficients exactly zero.
- Keeps all features in the model.
- Reduces variance and improves generalization.

**Example:**


| Feature  | Before | After Ridge |
| -------- | ------ | ----------- |
| Age      | 2.4    | 2.1         |
| Salary   | 1.8    | 1.5         |
| Zip Code | 0.6    | 0.3         |


All features remain, but their influence is reduced.

**Best when:**

- Most features are useful.
- Features are highly correlated (multicollinearity).

### Key Differences

![Lasso (L1 diamond) vs. Ridge (L2 circle) — why L1 zeros coefficients and L2 does not](images/lasso-ridge-coefficient-paths.png)

*Source: [ethen8181 — Regularization](http://ethen8181.github.io/machine-learning/regularization/regularization.html)*


| Aspect                    | Lasso (L1)             | Ridge (L2)            |
| ------------------------- | ---------------------- | --------------------- |
| Penalty                   | $\sum_{i=1}^{p} \lvert w_i \rvert$ | $\sum_{i=1}^{p} w_i^2$ |
| Feature selection         | ✅ Yes                  | ❌ No                  |
| Coefficients become zero  | ✅ Yes                  | ❌ Rarely              |
| Handles multicollinearity | Good                   | Excellent             |
| Model complexity          | Simpler                | Keeps all features    |


### Elastic Net Regularization

Elastic Net combines **both Lasso and Ridge** penalties.

![L1, L2, and Elastic Net penalty contours — Elastic Net is a rounded diamond between Lasso and Ridge](images/l1-l2-elastic-net-penalties.png)

*Source: [scikit-learn — SGD: Penalties](https://scikit-learn.org/stable/auto_examples/linear_model/plot_sgd_penalties.html)*

#### Formula

$$
\mathcal{L}(\mathbf{w}) = \text{MSE} + \lambda_1 \sum_{i=1}^{p} \lvert w_i \rvert + \lambda_2 \sum_{i=1}^{p} w_i^2
$$

or equivalently,

$$
\mathcal{L}(\mathbf{w}) = \text{MSE} + \lambda \left( \alpha \sum_{i=1}^{p} \lvert w_i \rvert + (1 - \alpha) \sum_{i=1}^{p} w_i^2 \right)
$$

where:

- **$\lambda$** controls the overall regularization strength.
- **$\alpha$** controls the mix:
  - $\alpha = 1$ → Lasso
  - $\alpha = 0$ → Ridge
  - $0 < \alpha < 1$ → Elastic Net

### Why Combine Lasso and Ridge?

Lasso has a limitation:

- If several features are highly correlated, it may keep only one and discard the others.

Ridge has a limitation:

- It keeps all features, including irrelevant ones.

Elastic Net combines their strengths:

- Performs feature selection (Lasso).
- Handles correlated features better (Ridge).
- Produces more stable models than Lasso alone.

### Example

Suppose you're predicting house prices with features:

- Size
- Number of rooms
- Living area
- Total built-up area
- Garage

Here, **Size**, **Living area**, and **Built-up area** are highly correlated.

- **Lasso:** Might keep only **Size** and remove the other two.
- **Ridge:** Keeps all three but shrinks their coefficients.
- **Elastic Net:** Keeps the important correlated features while shrinking them appropriately and removing only truly irrelevant ones (e.g., Garage if it adds little value).

### When to Use


| Situation                         | Recommended Method |
| --------------------------------- | ------------------ |
| Many irrelevant features          | Lasso              |
| Highly correlated features        | Ridge              |
| Many features + multicollinearity | Elastic Net        |


### Interview Answer (45–60 seconds)

> "Lasso, or L1 regularization, adds the absolute value of coefficients as a penalty, which can shrink some coefficients to exactly zero. This makes it useful for automatic feature selection. Ridge, or L2 regularization, adds the squared value of coefficients, reducing their magnitude without eliminating features. It's particularly effective when features are highly correlated. Elastic Net combines both L1 and L2 penalties, giving us the benefits of feature selection from Lasso and the stability of Ridge. It's commonly used for high-dimensional datasets where there are many correlated features."

---

**Source:** ML Fundamentals · Conceptual Interview Question

## Question

5. What are different **model evaluation techniques** in machine learning? When should you use each one?

## Answer

Model evaluation techniques help determine **how well a machine learning model generalizes to unseen data**. The choice depends on the dataset size, model type, and problem (classification or regression).

### 1. Train-Test Split

The dataset is divided into:

- **Training set** (e.g., 80%) to train the model.
- **Test set** (e.g., 20%) to evaluate performance.

**Example:**

- 10,000 samples
- 8,000 for training
- 2,000 for testing

![Train-test split — 80% training set and 20% test set](images/train-test-split.png)

#### Advantages

- Simple and fast.
- Suitable for large datasets.

#### Disadvantages

- Performance depends on one random split.
- Can be misleading if the split is not representative.

### 2. K-Fold Cross-Validation

The dataset is divided into **K equal parts (folds)**.

For each iteration:

- Train on **K−1 folds**.
- Test on the remaining fold.
- Repeat until every fold has been used as the test set.
- Average the performance across all folds.

Example with **5-fold CV**:

```
Fold 1 → Test
Fold 2-5 → Train

Fold 2 → Test
Fold 1,3,4,5 → Train

...

Average all 5 scores
```

![5-fold cross-validation — each fold used once as the test set](images/k-fold-cross-validation.png)

*Source: [scikit-learn — Visualizing cross-validation behavior](https://scikit-learn.org/stable/auto_examples/model_selection/plot_cv_indices.html)*

#### Advantages

- More reliable than a single train-test split.
- Uses all data for both training and testing.
- Reduces variance in performance estimates.

#### Disadvantages

- Computationally expensive.

### 3. Stratified K-Fold Cross-Validation

Used mainly for **classification** problems.

Each fold preserves the **same class distribution** as the original dataset.

Example:

Original dataset:

```
90% Negative
10% Positive
```

Each fold will also contain approximately:

```
90% Negative
10% Positive
```

![Stratified 5-fold — each fold preserves the 90/10 class ratio](images/stratified-k-fold.png)

*Source: [scikit-learn — Visualizing cross-validation behavior](https://scikit-learn.org/stable/auto_examples/model_selection/plot_cv_indices.html)*

#### Why use it?

Without stratification, some folds may contain very few or no minority-class samples, leading to unreliable evaluation.

### 4. Leave-One-Out Cross-Validation (LOOCV)

Special case of K-Fold where:

$$
K = n \text{ (number of samples)}
$$

If there are **100 samples**:

- Train on 99.
- Test on 1.
- Repeat 100 times.

![Leave-one-out CV — one sample held out per iteration](images/leave-one-out-cv.png)

*Source: [scikit-learn — Visualizing cross-validation behavior](https://scikit-learn.org/stable/auto_examples/model_selection/plot_cv_indices.html)*

#### Advantages

- Makes maximum use of available data.
- Good for very small datasets.

#### Disadvantages

- Very slow for large datasets.
- High computational cost.

### 5. Repeated K-Fold Cross-Validation

Runs K-Fold multiple times using different random splits.

Example:

```
5-Fold × 10 repetitions
```

Produces a more stable estimate of model performance by reducing the effect of any single random split.

### 6. Time Series Cross-Validation (Rolling/Forward Validation)

Used for **time-dependent data**.

You **cannot randomly shuffle** time series data because it would leak future information into the past.

Example:

```
Train: Jan-Feb
Test : Mar

Train: Jan-Mar
Test : Apr

Train: Jan-Apr
Test : May
```

This respects the chronological order of observations.

![Time series cross-validation — expanding training window, test always on future data](images/time-series-cross-validation.png)

*Source: [scikit-learn — Visualizing cross-validation behavior](https://scikit-learn.org/stable/auto_examples/model_selection/plot_cv_indices.html)*

### Common Evaluation Metrics

#### Classification

- **Accuracy**
- **Precision**
- **Recall**
- **F1 Score**
- **ROC-AUC**
- **Log Loss**
- **Confusion Matrix**

#### Regression

- **Mean Absolute Error (MAE)**
- **Mean Squared Error (MSE)**
- **Root Mean Squared Error (RMSE)**
- **R² Score (Coefficient of Determination)**

### Comparison Table


| Technique         | Best For                  | Advantages                        | Disadvantages                         |
| ----------------- | ------------------------- | --------------------------------- | ------------------------------------- |
| Train-Test Split  | Large datasets            | Fast and simple                   | Performance depends on one split      |
| K-Fold CV         | General ML                | Reliable estimate                 | More computationally expensive        |
| Stratified K-Fold | Imbalanced classification | Preserves class distribution      | Slightly more complex                 |
| LOOCV             | Very small datasets       | Uses almost all data for training | Extremely slow for large datasets     |
| Repeated K-Fold   | Robust evaluation         | Reduces randomness                | Higher computation                    |
| Time Series CV    | Time-dependent data       | Prevents data leakage             | Not suitable for non-time-series data |


### Which One Should You Use?


| Dataset/Scenario          | Recommended Technique        |
| ------------------------- | ---------------------------- |
| Large dataset             | Train-Test Split             |
| Medium-sized dataset      | K-Fold Cross-Validation      |
| Imbalanced classification | Stratified K-Fold            |
| Small dataset             | LOOCV                        |
| Time series forecasting   | Time Series Cross-Validation |


### Interview Answer (60–90 seconds)

> "Model evaluation techniques measure how well a model generalizes to unseen data. The simplest approach is a train-test split, where the data is divided into training and testing sets. A more reliable method is K-Fold Cross-Validation, where the data is split into K folds and each fold is used once for testing. For imbalanced classification problems, Stratified K-Fold ensures each fold maintains the original class distribution. For very small datasets, Leave-One-Out Cross-Validation trains on all but one sample in each iteration. For time-series data, we use forward or rolling validation to preserve the temporal order and avoid data leakage. After evaluation, we use metrics such as Accuracy, Precision, Recall, F1 Score, and ROC-AUC for classification, or MAE, RMSE, and R² for regression."

