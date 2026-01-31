# Marketing A/B Testing Analysis

This project presents an end-to-end **A/B testing analysis** on a marketing dataset to evaluate whether showing ads (`ad`) leads to higher conversion rates compared to a public service announcement (`psa`).

The focus of this notebook is **correct statistical methodology**, **robustness checks**, and **clear business interpretation**, rather than just running a hypothesis test.

---

## Problem Statement

The goal is to answer:

> **Does ad exposure increase user conversion compared to a PSA?**

- **Treatment group**: `ad`
- **Control group**: `psa`
- **Outcome variable**: `converted` (binary: True / False)

---

All analysis is contained in a single notebook for clarity and reproducibility.

---

## 🧪 Methodology

### 1. Data Cleaning & Exploration
- Removed redundant index columns
- Inspected data types and missing values
- Explored conversion rates by group
- Analyzed ad exposure distribution (`total_ads`)

Key finding:
- `total_ads` is **heavily right-skewed**, with a small fraction of users receiving extremely high exposure.

---

### 2. Outlier Analysis
- Identified extreme ad exposure using the **IQR method**
- Created a trimmed dataset excluding extreme users
- Purpose: ensure results are **not driven by a small minority**

Outliers were **not blindly removed**, but used for **sensitivity analysis**.

---

### 3. Hypothesis Testing

#### Hypotheses
- **H₀ (Null)**: Conversion rate of `ad` = conversion rate of `psa`
- **H₁ (Alternative)**: Conversion rates differ between groups

#### Statistical Test
- **Two-proportion Z-test**
- Appropriate because:
  - Outcome is binary
  - Sample size is large
  - CLT applies to the sampling distribution of proportions

---

### 4. Sensitivity Analysis
The A/B test was conducted on:
- **Full dataset**
- **Trimmed dataset (outliers removed)**

This allows comparison of:
- Statistical significance
- Effect size stability

---

## Key Results

- Ads show a **statistically significant increase** in conversion rate over PSA
- Effect size decreases after trimming extreme users
- Direction and significance of the effect remain consistent

**Interpretation**:
- Ads are effective overall
- Extreme users amplify the observed uplift
- A conservative estimate comes from the trimmed dataset

---

## Statistical Assumptions

- Binary outcome variable
- Independent observations
- Large sample size → CLT applies
- Normality of raw data is **not required** for proportion-based tests

---

## Business Takeaways

- Ads outperform PSA in driving conversions
- Impact is not solely driven by extreme users
- Results are robust but magnitude should be interpreted carefully

---

## 🛠 Tools & Libraries

- Python
- pandas
- numpy
- matplotlib / seaborn
- statsmodels
