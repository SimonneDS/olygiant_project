# 🛢️ Predictive Petroleum Exploration Analysis – OilyGiant

## 📜 Project Description

This Data Science project focuses on the **financial evaluation and optimal region selection** for oil well development for the OilyGiant company.

A predictive model was developed to estimate the volume of reserves in three candidate regions, followed by a rigorous risk analysis to ensure the profitability and stability of the investment. The final decision is based on a strict financial risk criterion.

## 🎯 Business Objectives

1.  **Predictive Modeling:** Create a Linear Regression model to accurately predict the volume of reserves (`product`) in each well.
2.  **Risk Analysis:** Employ the **Bootstrapping** technique to evaluate the financial risk in each region, projecting the distribution of profits.
3.  **Optimal Selection:** Select the region that guarantees a **positive average profit** and a risk of incurring losses **below 2.5%**.

## 🛠️ Methodology and Risk Analysis

### 1. Predictive Modeling (Linear Regression)

* A **Linear Regression** model was used due to its interpretability and good initial performance for product volume prediction.
* The model was trained and evaluated independently for each of the three regions.

### 2. Financial Analysis and Key Criteria

* **Budget per Region:** \$100 million for the development of **200 wells**.
* **Revenue per Product Unit:** \$4,500 for every 1000 barrels.
* **Minimum Break-Even Volume:** It was determined that a well must have an average volume of at least **111.11 thousand barrels** to cover investment costs.

### 3. Risk Evaluation (Bootstrapping)

The *Bootstrapping* technique was applied with 1000 samples to calculate the profit distribution, average profit, and percentage of loss risk for each region.

## 📈 Key Results and Conclusion

| Region | Risk of Loss (%) | Projected Average Profit | Meets Risk Criterion (< 2.5%) |
| :--- | :--- | :--- | :--- |
| **Region 0** | **6.5%** | \$3,600,000 | **NO** |
| **Region 1** | **0.7%** | **\$5,100,000** | **YES** |
| **Region 2** | **5.1%** | \$4,800,000 | **NO** |

### Final Decision

Based on the company's stringent financial criteria:

**Region 1** is the only one that meets both key requirements: a positive average profit and a risk of loss significantly below 2.5% (only 0.7%).

Therefore, the recommendation is to **focus development and investment of 200 wells in Region 1**.

## 💻 Technologies Used

* **Language:** Python
* **Key Libraries:** `pandas`, `numpy`, `sklearn.linear_model` (`LinearRegression`), `sklearn.metrics` (`mean_squared_error`).