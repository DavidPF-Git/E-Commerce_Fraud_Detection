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

**Python:** Pandas, Numpy, matplotlib, seaborn, math

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
