# Financial-Default-Prediction

# 📊 Financial Risk Analysis Project

This project is divided into two comprehensive parts focusing on different dimensions of financial risk management:

- **PART A**: Credit Risk Prediction using financial statement data
- **PART B**: Market Risk Analysis using historical stock price data

---

## 📁 PART A: Credit Risk Prediction from Financial Statements

### 🔍 Context

In the realm of modern finance, companies must effectively manage debt to maintain favorable credit ratings and ensure sustainable growth. This analysis focuses on predicting default likelihood based on financial health indicators using supervised machine learning.

---

### 🧮 Step 1: Binary Target Variable Creation

**Target Variable: `Default`**

- **Default = 0**: Net Worth Next Year > 0 → Financially stable
- **Default = 1**: Net Worth Next Year ≤ 0 → Likely to default

---

### 📊 Label Distribution

- **Default (0)**: 3,352 (79%)
- **Default (1)**: 904 (21%)

---

### 📈 Feature Importance Methods

Two techniques were used to evaluate feature importance:

#### 1. Gini Importance (Mean Decrease in Impurity)
- Fast and integrated into training
- Biased toward high-cardinality or correlated features

#### 2. Permutation Importance (Mean Decrease in Accuracy)
- Model-agnostic and robust to correlations
- Computationally expensive

| Aspect                | Gini Importance      | Permutation Importance   |
|----------------------|----------------------|---------------------------|
| Basis                | Impurity reduction   | Accuracy decrease         |
| Speed                | Fast (O(1))          | Slow (O(n_repeats))       |
| Correlation Handling | Poor                 | Excellent                 |
| Feature Bias         | High-cardinality     | None                      |
| Model Compatibility  | Tree-based only      | Any model                 |

---

### 🥇 Top 5 Features by Importance

| Rank | Gini Importance         | Permutation Importance   |
|------|--------------------------|---------------------------|
| 1    | Networth Next Year       | Networth Next Year        |
| 2    | PAT / Net Worth          | PAT / Net Worth           |
| 3    | Cash Profit              | TOL / TNW                 |
| 4    | Debt-to-Equity           | Shareholders Funds        |
| 5    | Cumulative Profits       | Cash Profit               |

---

### ✅ Final Model Selection

**Best Model**: Random Forest Classifier  
**Top 15 Final Features Used:**

- `Networth_Next_Year`
- `PAT_as_percentage_of_net_worth`
- `Cash_profit`
- `Debt_to_equity_ratio__times_`
- `Cumulative_retained_profits`
- `TOLtoTNW`
- `Shareholders_funds`
- `Profit_after_tax`
- `Net_worth`
- `PAT_as_percentage_of_total_income`
- `Reserves_and_funds`
- `Total_term_liabilities_to_tangible_net_worth`
- `Cash_profit_as_percentage_of_total_income`
- `PBT`
- `PE_on_BSE`

---

### 💡 Actionable Insights

- Use Random Forest output to flag potential defaulters
- Focus on PAT, PBT, and Cash Profit as leading indicators
- Evaluate debt ratios (Debt/Equity, TOL/TNW) for restructuring opportunities
- Monitor capital strength (Reserves, Shareholder Funds)
- Improve liquidity dashboards using Cash-based metrics
- Investigate outlier firms with extreme values
- Combine market indicators (e.g., PE on BSE) with fundamentals

---

## 📁 PART B: Market Risk Analysis using Stock Price Data

### 🔍 Context

Investors face **market risk** due to external macroeconomic or geopolitical events. To build robust investment strategies, analyzing stock volatility is crucial.

---

### 📄 Dataset Overview

- **Rows**: 418
- **Columns**: 6
- **Key Features**: Stock prices across multiple time periods
- **Note**: Only the `Date` column is converted to datetime; rest are numerical.

---

### 📈 Normalizing Volatility: Coefficient of Variation (CV)

Since direct comparisons using standard deviation are misleading due to scale differences, the **Coefficient of Variation (CV)** is used:

\[
\text{CV} = \frac{\text{Standard Deviation}}{\text{Mean}}
\]

- Helps in comparing volatility across different stock price levels
- Enables fair analysis of risk and return

---

### 📉 Graphical Analysis

- Stock Price vs. Time plotted for each company
- Volatility and trends observed visually

---

### 📊 Return Analysis

Stock returns are calculated to evaluate profitability and risk-adjusted returns.

---

## 📌 Summary

- **PART A** equips financial institutions with a machine-learning powered credit risk assessment model.
- **PART B** provides a quantitative framework to measure market risk and asset return stability using normalized volatility metrics.

---

## ✅ Tools Used

- Python (Pandas, NumPy, Scikit-learn, Matplotlib, Seaborn, Logistic Regression, KNN Imputation, Random Forest Classifier)
- Jupyter Notebook
- LaTeX for formulas
- Excel (for intermediate checks)

---

## 📚 References

- [Investopedia - Coefficient of Variation](https://www.investopedia.com/terms/c/coefficientofvariation.asp)
- [Scikit-learn: Feature Importance](https://scikit-learn.org/stable/modules/permutation_importance.html)
- [Random Forest Documentation](https://scikit-learn.org/stable/modules/generated/sklearn.ensemble.RandomForestClassifier.html)
