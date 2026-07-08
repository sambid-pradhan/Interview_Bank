**Source:** Statistics Fundamentals · Conceptual Interview Question

## Question

1. What is the **Central Limit Theorem (CLT)**? Why is it important in statistics and machine learning?

## Answer

The **Central Limit Theorem (CLT)** says that if we repeatedly take large random samples from a population and compute their means, the **distribution of those sample means becomes approximately normal**, even if the original population is not normal.

This holds when observations are independent and the population has finite variance. A common rule of thumb is **n >= 30**, but highly skewed data may require a larger sample.

### Why is CLT Important?

CLT lets us use normal-distribution-based methods even when the raw data is non-normal. It supports:

- **Confidence intervals**
- **Hypothesis testing**
- **A/B testing**
- **Statistical inference**
- **Model evaluation in machine learning**

### Example

Salary data may be highly skewed because a few executives earn much more. But if we repeatedly sample **50 employees** and calculate the average salary each time, those sample averages will be approximately normal. This helps estimate the true average salary and build confidence intervals.

### Why Does It Matter in Machine Learning?

In machine learning, CLT helps quantify uncertainty in performance estimates, such as:

- Confidence intervals for accuracy, precision, recall, or RMSE
- Comparing two models using statistical significance tests
- A/B testing recommendation or ranking systems
- Estimating average cross-validation performance

### Conditions for CLT

- Samples are **randomly selected** or representative.
- Observations are **independent** or weakly dependent.
- The population has **finite variance**.
- The sample size is sufficiently large.

### Interview Takeaway

> "The Central Limit Theorem says that for large enough samples, the distribution of sample means becomes approximately normal, even if the original data is not normal, assuming independence and finite variance. It matters because it enables confidence intervals, hypothesis testing, A/B testing, and uncertainty estimation for machine learning metrics."

---

**Source:** Statistics Fundamentals · Conceptual Interview Question

## Question

2. What are **Type I** and **Type II** errors in hypothesis testing?

## Answer

In hypothesis testing, errors happen when our decision about the **null hypothesis** is wrong.

- **Type I Error (False Positive):** Rejecting the null hypothesis when it is actually true.
- **Type II Error (False Negative):** Failing to reject the null hypothesis when it is actually false.

### Example

For a medical disease test:

- **Type I Error:** The test says a healthy person has the disease.
- **Type II Error:** The test says a sick person is healthy.

### Key Difference

| Type I Error | Type II Error |
| ------------ | ------------- |
| False Positive | False Negative |
| Reject a true null hypothesis | Fail to reject a false null hypothesis |
| Controlled by significance level, alpha | Related to statistical power, 1 - beta |

### Interview Takeaway

> "A Type I error is a false positive, where we incorrectly reject a true null hypothesis. A Type II error is a false negative, where we fail to reject a false null hypothesis. In hypothesis testing, we try to balance both errors while choosing an appropriate significance level."

---

**Source:** Statistics Fundamentals · Conceptual Interview Question

## Question

3. What is the difference between **correlation** and **causation**?

## Answer

- **Correlation** means two variables are related or move together, but one does **not necessarily cause** the other.
- **Causation** means a change in one variable **directly causes** a change in the other.

### Example

Ice cream sales and drowning incidents both increase in summer. They are **correlated**, but ice cream does **not cause** drowning. The common factor is **hot weather**.

### Key Difference

| Correlation | Causation |
| ----------- | --------- |
| Variables are associated | One variable directly affects the other |
| Does not imply cause | Establishes a cause-and-effect relationship |
| May be due to a third factor or coincidence | Requires evidence such as experiments or causal analysis |

### Interview Takeaway

> "Correlation indicates that two variables are associated, while causation means one variable directly causes changes in the other. Correlation does not imply causation because the relationship may be due to a third factor, coincidence, or confounding."

---

**Source:** Statistics Fundamentals · Conceptual Interview Question

## Question

4. What is the difference between **cross-validation** and **bootstrapping**?

## Answer

Both are **resampling techniques**, but they are used for different goals.

- **Cross-validation:** Splits the dataset into folds. The model trains on some folds and tests on the remaining fold. The average score estimates model performance.
- **Bootstrapping:** Creates new datasets by sampling **with replacement** from the original data. It is used to estimate uncertainty, variance, and confidence intervals.

### Key Difference

| Cross-Validation | Bootstrapping |
| ---------------- | ------------- |
| Samples without replacement across folds | Samples with replacement |
| Mainly used for model evaluation | Mainly used for uncertainty and variance estimation |
| Every data point is used for testing across folds | Some points may repeat, while others may be left out |
| Helps estimate generalization performance | Helps estimate stability or confidence intervals |

### Example

- Use **cross-validation** to estimate how well a model performs on unseen data.
- Use **bootstrapping** to estimate the confidence interval of a metric like accuracy or the mean.

### Interview Takeaway

> "Cross-validation evaluates model performance by training and testing on different data folds. Bootstrapping samples data with replacement to estimate the variability of statistics or models, and is commonly used for confidence intervals and ensemble methods like Random Forest."

---

**Source:** Statistics Fundamentals · Conceptual Interview Question

## Question

5. What is a **p-value**, and how is it used in hypothesis testing?

## Answer

A **p-value** is the probability of observing the current result, or a more extreme result, **assuming the null hypothesis is true**.

- **Low p-value, typically < 0.05:** Strong evidence against the null hypothesis, so we reject it.
- **High p-value, typically >= 0.05:** Not enough evidence to reject the null hypothesis.

### Example

Suppose we test whether a new drug is more effective than the current one.

- **p-value = 0.03:** Reject the null hypothesis; the result is statistically significant.
- **p-value = 0.20:** Fail to reject the null hypothesis; there is insufficient evidence that the new drug is better.

### Important Note

A p-value does **not** tell us the probability that the null hypothesis is true. It only tells us how surprising the observed data would be if the null hypothesis were true.

### Interview Takeaway

> "A p-value measures how likely the observed results, or more extreme results, are if the null hypothesis is true. A small p-value, typically less than 0.05, suggests statistical significance, so we reject the null hypothesis. A large p-value means there is not enough evidence to reject it."
