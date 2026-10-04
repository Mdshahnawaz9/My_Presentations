#  Data-Driven Budget Allocation – Garment Store

> **From Common-Sense Guessing to Data-Driven Inventory Decisions**

This project demonstrates how customer data can be used to make a better **inventory budget allocation** decision for a new garment store.

The store has an initial budget of **₹1,00,000** for purchasing jeans inventory.

Instead of dividing the budget equally based on assumptions, this project analyzes customer data to understand **gender distribution, height distribution, and size demand**, and then allocates the budget according to observed demand.

---

##  Table of Contents

- [Project Overview](#-project-overview)
- [Business Problem](#-business-problem)
- [Objective](#-objective)
- [Dataset](#-dataset)
- [Common-Sense Approach](#-common-sense-approach)
- [Problems with Equal Allocation](#-problems-with-equal-allocation)
- [Data-Driven Approach](#-data-driven-approach)
- [Analysis Performed](#-analysis-performed)
- [Gender Distribution](#1-gender-distribution)
- [Height Distribution Using KDE](#2-height-distribution-using-kde)
- [Empirical Rule](#3-empirical-rule)
- [Size Classification](#4-size-classification)
- [Demand Analysis](#5-demand-analysis)
- [Budget Allocation](#6-budget-allocation)
- [Common Sense vs Data Driven](#-common-sense-vs-data-driven)
- [Final Recommendation](#-final-recommendation)
- [Technologies Used](#-technologies-used)
- [Project Structure](#-project-structure)
- [Analysis Workflow](#-analysis-workflow)
- [Key Insights](#-key-insights)
- [Future Improvements](#-future-improvements)
- [Presentation](#-presentation)
- [Conclusion](#-conclusion)

---

#  Project Overview

The goal of this project is to solve a simple business problem:

> **How should a garment store allocate its ₹1,00,000 jeans inventory budget?**

A common approach would be to divide the budget equally between customer groups.

For example:

```text
Total Budget = ₹1,00,000

Male   → ₹50,000
Female → ₹50,000
```

However, equal allocation assumes that demand is equally distributed.

This project checks that assumption using customer data.

The analysis follows:

```text
Customer Data
      ↓
Data Analysis
      ↓
Distribution Analysis
      ↓
Size Classification
      ↓
Demand Calculation
      ↓
Budget Allocation
```

---

#  Business Problem

Imagine a new garment store that wants to purchase jeans inventory.

The store has:

```text
Available Budget = ₹1,00,000
```

The store needs to decide:

- How much budget should go to male jeans?
- How much budget should go to female jeans?
- Which sizes should receive more budget?
- Which sizes may have lower demand?
- Should the budget be divided equally?

A simple equal allocation may look fair, but it may not represent actual customer demand.

Therefore, the business needs a **data-driven allocation strategy**.

---

#  Objective

The main objectives of this project are:

- Analyze the customer dataset.
- Understand the gender distribution.
- Analyze customer height distribution.
- Visualize height distributions using KDE.
- Understand whether a distribution is approximately normal.
- Apply the Empirical Rule only where appropriate.
- Convert customer height into jeans-size categories.
- Calculate demand for each gender-size combination.
- Allocate the ₹1,00,000 budget based on observed demand.
- Compare equal allocation with data-driven allocation.
- Provide a business-oriented recommendation.

---

# Dataset

The dataset contains customer information related to:

| Column | Description |
|---|---|
| Gender | Customer gender |
| Height | Customer height |

### Dataset Size

```text
Total Records = 10,000
```

### Main Variables

```text
Gender → Categorical Variable
Height → Numerical Variable
```

---

#  Common-Sense Approach

Before performing any analysis, a person might naturally think:

> "We have ₹1,00,000, so let's divide it equally."

For example:

```text
Total Budget = ₹1,00,000

Male   → ₹50,000
Female → ₹50,000
```

Then each gender could also be divided equally among the three sizes:

```text
Small  → 33.33%
Medium → 33.33%
Large  → 33.33%
```

This approach is:

- Simple
- Easy to understand
- Quick to implement
- Fair-looking

However, it is still based on **assumptions**.

---

# Problems with Equal Allocation

## Problem 1 — Customer Distribution May Not Be Equal

The equal approach assumes:

```text
Male   = 50%
Female = 50%
```

But the observed dataset shows approximately:

```text
Male   = 71.14%
Female = 28.86%
```

Therefore, a 50/50 allocation does not match the observed customer distribution.

---

## Problem 2 — Size Demand May Not Be Equal

Equal allocation assumes:

```text
Small  = 33.33%
Medium = 33.33%
Large  = 33.33%
```

But customers do not necessarily have equal height distributions.

Therefore, actual demand for different sizes may be different.

---

## Problem 3 — Inventory Risk

If the store allocates money incorrectly:

### Overstock

Too much inventory in a low-demand category can result in:

- Unsold stock
- Blocked capital
- Storage requirements
- Discounts to clear inventory

### Understock

Too little inventory in a high-demand category can result in:

- Lost sales
- Customer dissatisfaction
- Missed revenue opportunities

Therefore:

> **The goal is not equal allocation. The goal is demand-aligned allocation.**

---

# Data-Driven Approach

Instead of making assumptions, the project follows:

```text
DATA
 ↓
UNDERSTAND
 ↓
VISUALIZE
 ↓
CLASSIFY
 ↓
COUNT DEMAND
 ↓
ALLOCATE BUDGET
```

The main idea is:

> **Use observed customer demand to decide where the money should go.**

---

#  Analysis Performed

The project performs the following analysis:

1. Gender Distribution
2. Height Distribution using KDE
3. Distribution Shape Analysis
4. Empirical Rule
5. Height-to-Size Classification
6. Gender × Size Demand Analysis
7. Budget Allocation
8. Common-Sense vs Data-Driven Comparison

---

# 1 Gender Distribution

The first step is to understand the customer mix.

The observed distribution is approximately:

```text
Male   → 71.14%
Female → 28.86%
```

This immediately shows that the customer base is not equally distributed.

### Insight

A 50/50 budget allocation would ignore the observed customer distribution.

Therefore, the data suggests that the male and female budgets should not automatically be equal.

---

# 2️ Height Distribution Using KDE

## What is KDE?

KDE stands for:

> **Kernel Density Estimation**

KDE is used to understand the shape of a numerical distribution.

In this project, KDE is applied to customer height.

It helps us understand:

- Where most heights are concentrated
- The overall shape of the distribution
- Differences between male and female heights
- Whether the distribution appears approximately normal
- Whether the distribution is flat, skewed, or concentrated

### Important

We do **not** assume that the distribution must be bell-shaped.

Instead:

```text
Actual Data
     ↓
KDE
     ↓
Observe the Shape
```

For example:

```text
Normal-like distribution
→ Bell-shaped KDE

Uniform-like distribution
→ Relatively flat KDE

Skewed distribution
→ Asymmetric KDE
```

Therefore, the KDE plot should represent the **actual shape of the dataset**.

---

# 3️ Empirical Rule

The Empirical Rule is also known as the:

> **68–95–99.7 Rule**

For an approximately normal distribution:

```text
Mean ± 1 Standard Deviation
→ Approximately 68%

Mean ± 2 Standard Deviations
→ Approximately 95%

Mean ± 3 Standard Deviations
→ Approximately 99.7%
```

### Formula

```text
68%  → μ ± 1σ

95%  → μ ± 2σ

99.7% → μ ± 3σ
```

Where:

```text
μ = Mean
σ = Standard Deviation
```

### Important Statistical Point

The Empirical Rule should **not be blindly applied to every distribution**.

First:

```text
KDE / Distribution Analysis
          ↓
Understand Shape
          ↓
Check Approximate Normality
          ↓
Apply Empirical Rule if Appropriate
```

This prevents incorrect statistical assumptions.

---

# 4️ Size Classification

After understanding the height distribution, customer height is converted into jeans-size categories.

The categories are:

```text
Small
Medium
Large
```

The classification is performed separately for:

```text
Male
Female
```

This creates six demand categories:

```text
Male Small
Male Medium
Male Large

Female Small
Female Medium
Female Large
```

---

# 5️ Demand Analysis

After classification, the number of customers in each category is counted.

The analysis uses:

```text
Gender × Size
```

For example:

```text
Male + Small
Male + Medium
Male + Large

Female + Small
Female + Medium
Female + Large
```

These counts represent the observed demand distribution in the dataset.

The category with the highest customer count represents the largest observed demand segment.

---

# 6️ Budget Allocation

The total available budget is:

```text
₹1,00,000
```

Instead of dividing this amount equally, the project allocates the budget according to observed demand.

## Formula

```text
Category Budget =
(Category Customers / Total Valid Customers)
× Total Budget
```

### Example

Suppose a category represents 20% of the valid customer demand.

Then:

```text
Category Budget
= 20% × ₹1,00,000

= ₹20,000
```

This means the budget follows the observed customer distribution.

---

#  Final Allocation Logic

The final allocation follows:

```text
Customer Count
       ↓
Percentage of Demand
       ↓
Percentage of Budget
       ↓
Inventory Allocation
```

Therefore:

> Higher observed demand → Higher budget allocation

and:

> Lower observed demand → Lower budget allocation

---

#  Common Sense vs Data-Driven

| Category | Common-Sense Approach | Data-Driven Approach |
|---|---|---|
| Gender | 50 / 50 | Based on observed distribution |
| Size | Equal allocation | Based on observed demand |
| Distribution | Assumed | Analyzed using KDE |
| Statistics | Not considered | Used carefully |
| Decision | Assumption-based | Evidence-based |
| Risk | Higher | Better aligned with demand |

---

#  Analysis Workflow

```text
                 DATASET
                    │
                    ▼
             DATA CLEANING
                    │
                    ▼
          GENDER DISTRIBUTION
                    │
                    ▼
        HEIGHT DISTRIBUTION
                    │
                    ▼
                KDE
                    │
                    ▼
       CHECK DISTRIBUTION SHAPE
                    │
                    ▼
       EMPIRICAL RULE IF SUITABLE
                    │
                    ▼
          SIZE CLASSIFICATION
                    │
                    ▼
          DEMAND CALCULATION
                    │
                    ▼
          BUDGET ALLOCATION
                    │
                    ▼
       BUSINESS RECOMMENDATION
```

---

#  Key Insights

The analysis provides several important insights.

### Insight 1

The customer distribution is not 50/50.

```text
Male   → 71.14%
Female → 28.86%
```

Therefore, equal gender allocation may not reflect actual demand.

---

### Insight 2

Height distributions should be explored rather than assumed.

KDE helps us understand the actual distribution shape.

---

### Insight 3

The Empirical Rule is useful only when the distribution is approximately normal.

It should not be automatically applied to a uniform-like or strongly skewed distribution.

---

### Insight 4

Different height distributions can lead to different size demands.

Therefore, size-level allocation should be based on observed customer counts.

---

### Insight 5

The Male Medium category has the highest observed demand in this analysis.

Therefore, it receives the largest budget share under the demand-proportional allocation approach.

---

#  Final Recommendation

The project recommends moving away from:

```text
Equal Budget Allocation
```

and moving toward:

```text
Demand-Based Budget Allocation
```

The recommended strategy is:

```text
Analyze Customer Data
        ↓
Understand Customer Distribution
        ↓
Identify Size Demand
        ↓
Calculate Demand Percentage
        ↓
Allocate Budget Proportionally
```

This approach provides a more evidence-based starting point for inventory planning.

---

# 🛠️ Technologies Used

The project uses the following technologies:

```text
Python
Pandas
NumPy
Matplotlib
Seaborn
Jupyter Notebook
Git
GitHub
```

---

#  Python Libraries

Main libraries used for analysis:

```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
```

These libraries are used for:

| Library | Purpose |
|---|---|
| Pandas | Data manipulation |
| NumPy | Numerical calculations |
| Matplotlib | Data visualization |
| Seaborn | Statistical visualization |

---

#  Project Structure

```text
Data-Driven-Budget-Allocation/
│
├── 📁 dataset/
│   └── height_gender_data.csv
│
├── 📁 presentation/
│   └── Data_Driven_Budget_Allocation.pptx
│
├── 📁 notebook/
│   └── analysis.ipynb
│
│
├── 📄 README.md
```

---

#  Project Workflow

### Step 1 — Load Dataset

```python
df = pd.read_csv("height_gender_data.csv")
```

### Step 2 — Explore Data

```python
df.head()
df.info()
df.describe()
```

### Step 3 — Analyze Gender

```python
df["gender"].value_counts(normalize=True) * 100
```

### Step 4 — Visualize Height Distribution

```python
sns.kdeplot(
    data=df,
    x="height",
    hue="gender"
)

plt.title("Height Distribution by Gender")
plt.show()
```

### Step 5 — Classify Customers

Customers are classified into:

```text
Small
Medium
Large
```

based on the defined height ranges.

### Step 6 — Calculate Demand

```python
df.groupby(["gender", "size"]).size()
```

### Step 7 — Calculate Budget

```python
budget = (
    category_customers / total_valid_customers
) * 100000
```

---

#  Budget Allocation Formula

The main formula used in the project is:

```text
Budget Allocation =
(Category Demand / Total Demand)
× Total Budget
```

Where:

```text
Total Budget = ₹1,00,000
```

This ensures that the complete budget is distributed according to observed demand.

---

#  Why Data-Driven Allocation?

A business should not make important inventory decisions only because an allocation:

- Looks equal
- Feels fair
- Is simple
- Is easy to calculate

Instead, the decision should be supported by:

```text
Customer Data
+
Statistical Analysis
+
Demand Patterns
```

This can help reduce the risk of:

```text
Overstock
Understock
Blocked Capital
Missed Sales
```

---

# Future Improvements

This project can be extended by adding more real-world business information.

### 1. Historical Sales Data

Use previous sales to estimate actual product demand.

### 2. Product Prices

Different products may have different costs.

### 3. Profit Margins

Budget allocation can consider profitability instead of only customer count.

### 4. Seasonal Demand

Demand may change during:

```text
Summer
Winter
Festivals
Sales Events
```

### 5. Customer Age

Age groups may have different clothing preferences.

### 6. Location

Different locations may have different customer demand patterns.

### 7. Machine Learning

A demand forecasting model could be developed to predict future inventory requirements.

### 8. Real Sales Forecasting

Instead of allocating based only on customer distribution:

```text
Customer Data
      +
Historical Sales
      +
Price
      +
Seasonality
      ↓
Demand Forecast
      ↓
Optimal Budget Allocation
```

---

# Business Impact

A data-driven inventory strategy can help businesses:

- Make better purchasing decisions
- Reduce excess inventory
- Reduce stock-out risk
- Improve capital utilization
- Understand customer demand
- Plan inventory more effectively

---

#  Learning Outcomes

Through this project, the following concepts were practiced:

### Python

- Pandas
- NumPy
- Data manipulation

### Statistics

- Mean
- Standard Deviation
- Distribution
- Empirical Rule
- KDE

### Data Visualization

- Distribution plots
- KDE plots
- Comparison charts
- Business-oriented visualizations

### Business Analytics

- Demand analysis
- Customer segmentation
- Inventory planning
- Budget allocation
- Data-driven decision making

---

#  Project Presentation

A presentation explaining the complete analysis and business problem is included in the repository.

The presentation covers:

```text
Business Problem
      ↓
Common-Sense Approach
      ↓
Problems With Equal Allocation
      ↓
Data Analysis
      ↓
Gender Distribution
      ↓
KDE Analysis
      ↓
Empirical Rule
      ↓
Size Classification
      ↓
Demand Analysis
      ↓
Budget Allocation
      ↓
Final Recommendation
```

---

# Final Conclusion

The main conclusion of this project is:

> **Budget allocation should be based on observed customer demand rather than simply dividing the budget equally.**

A common-sense approach is useful as a starting point, but data analysis helps validate whether that assumption is actually correct.

By combining:

```text
EDA
+
KDE
+
Statistical Understanding
+
Size Classification
+
Demand Analysis
```

we can create a more informed inventory budget allocation strategy.

---

# Key Takeaway

```text
Don't Guess.
Don't Assume.
Analyze the Data.
Understand the Demand.
Allocate the Budget Smarter.
```

---

#  Project Type

```text
Data Science
Exploratory Data Analysis
Business Analytics
Statistical Analysis
Data Visualization
Inventory Planning
Budget Allocation
```

---

#  Tags

```text
#Python
#DataScience
#EDA
#Pandas
#NumPy
#Matplotlib
#Seaborn
#Statistics
#KDE
#DataVisualization
#BusinessAnalytics
#InventoryManagement
#BudgetAllocation
#GitHub
```

---

##  Author

**Mohammed Shahnawaz**

Data Science | Python | Data Analytics

---

⭐ **If you find this project useful, consider giving the repository a star!**
