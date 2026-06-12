# E-Commerce Fraud Detection
Analyzed around 300,000 transactions on e-commerce platforms across Istanbul, Berlin, New York, London, and Paris from a synthetic dataset in an end-to-end project.

This synthetic dataset recreates realistic fraud behavior across countries, channels, and user profiles — allowing anyone to build, test, and compare fraud-detection models without exposing any real user data.

(Work in progress)

## Data

https://www.kaggle.com/code/devraai/ecommerce-fraud-detection-analysis/input?select=transactions.csv

See EDA for more details on the dataset.

## Steps in the project

- Data cleaning and preparation

- Exploratory Data Analysis

- Trend and pattern identification

- Visualization and dashboard creation

- Machine learning for predictive modeling

## Tools used

**Python:** Pandas, Numpy, Matplotlib, Seaborn, Math, Scikit-Learn, XGBoost, LightGBM, PyTorch

## Some Insights and Conclusions

Fraud in this dataset is driven not by the timing of transactions, but by geographic inconsistencies, financial behavior anomalies, security-related signals, and user profile characteristics.

- The dataset exhibits a significant class imbalance, with approximately 98% legitimate transactions and only 2% fraudulent transactions.

- Fraud rates remain remarkably stable across the 24-hour cycle, with no clearly identifiable high-risk time windows. Similarly, no meaningful variation is observed across weekdays. A modest increase is detected only during the final days of the month (days 29–31). These findings suggest that temporal variables possess limited predictive value for fraud detection. A substantial concentration of fraudulent transactions was observed among accounts that had been active for less than 50 days.

- Transactions exhibiting geographic discrepancies are approximately eight times more likely to be fraudulent than those without such discrepancies.

- Fraudulent actors tend to have products shipped to locations significantly farther from the account holder's usual residential address.

- Relative financial behavior carries greater predictive value than the absolute transaction amount. The analysis reveals two distinct fraud patterns: aggressive fraud, characterized by transaction amounts that substantially exceed a user's historical spending levels, and stealth fraud, characterized by transaction amounts that closely resemble normal spending behavior and are likely intended to circumvent simple rule-based detection mechanisms.

- The data provide no evidence that attackers typically engage in large bursts of transactions. The conventional assumption that fraud is characterized by "multiple transactions occurring within a short time frame" is not supported by the observed patterns. Fraudsters also do not typically engage in excessively large purchases.

- Fraud is a multidimensional phenomenon that emerges when multiple weak signals co-occur, such as recently created accounts, long shipping distances, anomalous spending relative to historical patterns, and geographic inconsistencies.

- Improved performance is expected from tree-based and boosting models compared to simple linear models.

- Following a rigorous end-to-end evaluation of multiple machine learning architectures—ranging from baseline linear models to parallel bagging tree ensembles, sequential boosting networks, and deep connectionist tensors—we have compiled the definitive production-ready choices.

| # | Model Architecture      | Decision Threshold | Precision (UX Safety) | Recall (Fraud Capture) | F1-Score (Balance) | PR-AUC (Pure Power) |
|---|-------------------------|-------------------:|----------------------:|-----------------------:|-------------------:|--------------------:|
| 0 | Logistic Regression     | 0.5000             | 0.1500                | 0.8500                 | 0.2550             | 0.3520              |
| 1 | Random Forest           | 0.5000             | 0.9600                | 0.7400                 | 0.8400             | 0.8657              |
| 2 | XGBoost (Optimized)     | 0.9504             | 0.9069                | 0.7663                 | 0.8307             | 0.8645              |
| 3 | LightGBM (Optimized)    | 0.9504             | 0.8995                | 0.7579                 | 0.8227             | 0.8626              |
| 4 | PyTorch MLP (Optimized) | 0.9504             | 0.8475                | 0.6770                 | 0.7527             | 0.8027              |

The final choice depends on the current corporate priority:

* **Option 1: Maximize Financial Protection (XGBoost - Recommended)**
    * **The Business Impact:** Captures **76.6% of real fraud** with **90.7% precision** (only 1 in 10 alerts is a false alarm).
    * **Best For:** Minimizing chargeback liabilities, protecting capital, and keeping manual reviews safe.
    * **Operational Cutoff:** Calibrated Threshold at `0.9504`.

* **Option 2: Maximize User Experience (Random Forest)**
    * **The Business Impact:** Achieves a near-flawless **96.0% precision** (virtually zero false blocks), but drops fraud capture to **74.0%**.
    * **Best For:** Total friction-free checkouts, VIP retention, and minimizing customer support tickets.
    * **Operational Cutoff:** Standard Threshold at `0.5000`.

* **Option 3: Maximize Technological Efficiency (LightGBM)**
    * **The Business Impact:** Identical performance to XGBoost (**75.8% fraud capture / 90% precision**), but trains and operates **5x faster**.
    * **Best For:** Handling massive transactions per second and continuous cloud retraining with low server costs.
    * **Operational Cutoff:** Calibrated Threshold at `0.9504`.

Recommend deploying **XGBoost (Threshold 0.9504)**. It delivers the ultimate mathematical balance: high-tier financial protection without disrupting legitimate customer revenue streams.

