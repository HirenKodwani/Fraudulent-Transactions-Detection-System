# Fraudulent-Transactions-Detection-System

📌 Project Overview

This project was developedto detect fraudulent transactions in a financial dataset. The dataset contains over 6.3 million transactions across different types such as CASH-IN, CASH-OUT, DEBIT, PAYMENT, and TRANSFER. The goal was to build a machine learning model capable of identifying fraudulent behavior and provide actionable insights for prevention strategies.

📂 Dataset Details

Rows: 6,362,620

Columns: 10


Data Dictionary

step: Time unit (1 step = 1 hour, total 744 = 30 days simulation)

type: Transaction type (CASH-IN, CASH-OUT, DEBIT, PAYMENT, TRANSFER)

amount: Transaction amount (local currency)

nameOrig: Originating customer ID

oldbalanceOrg / newbalanceOrg: Balance before/after transaction (originator)

nameDest: Destination customer ID

oldbalanceDest / newbalanceDest: Balance before/after transaction (recipient)

isFraud: 1 if transaction is fraudulent, 0 otherwise

isFlaggedFraud: Flagged by business rule (e.g., transfers > 200,000)

Project Workflow & Key Findings
The Jupyter Notebook follows a structured approach to solve the problem:
1. Data Cleaning & Exploratory Data Analysis (EDA)
Missing Values: The dataset was found to be clean with no missing values.
Class Imbalance: The data is highly imbalanced, with fraudulent transactions accounting for only 0.13% of the total. This was a critical consideration for model training and evaluation.
Key Insight: A crucial discovery from the EDA was that fraudulent transactions only occur in TRANSFER and CASH_OUT types. This allowed us to significantly reduce the dataset size and focus the model on relevant data, improving both efficiency and performance.
2. Feature Engineering & Variable Selection
Feature Creation: New features like errorBalanceOrg were created to capture discrepancies in account balances, which proved to be highly predictive.
Feature Selection: High-cardinality and irrelevant columns (nameOrig, nameDest) were dropped. The dataset was filtered to only include TRANSFER and CASH_OUT transactions based on the EDA findings. The type column was one-hot encoded.
3. Model Development
Model Choice: An XGBoost Classifier was selected for its high performance on tabular data and its ability to handle class imbalance effectively using the scale_pos_weight parameter.
Data Preparation: The data was split into training (80%) and testing (20%) sets, and numerical features were standardized using StandardScaler.
4. Model Performance & Evaluation
The model demonstrated outstanding performance in identifying fraudulent transactions:
AUC-ROC Score: 0.9997 - Indicating an almost perfect ability to distinguish between classes.
Precision (Fraud): 0.97 - When the model predicts fraud, it is correct 97% of the time.
Recall (Fraud): 0.86 - The model successfully identified 86% of all actual fraudulent transactions in the test set.
The Confusion Matrix and ROC Curve further validate the model's excellent predictive power.
5. Key Factors Predicting Fraud
The model's feature importance analysis revealed the top predictors of fraud:
oldbalanceOrg: The sender's balance before the transaction.
errorBalanceOrg: The engineered feature capturing balance discrepancies.
amount: The transaction amount.
step: The time unit of the transaction.
type_TRANSFER: Whether the transaction is a fund transfer.
These factors logically align with fraudulent behavior, where an account is taken over and its entire balance is quickly transferred out.

✅ Results

Achieved high recall (>95%) on fraud detection

Reduced false negatives significantly

Identified key fraud risk patterns for proactive detection

🔒 Recommendations for Prevention

Real-time monitoring of suspicious TRANSFER + CASH-OUT combinations

Threshold-based alerts on abnormal balance changes

Multi-factor authentication for high-value transfers

Continuous model retraining with updated fraud data


Fraudulent Transactions Detection System - with Data Science Concepts
Data Source: The dataset can be found here : https://drive.usercontent.google.com/download?id=1VNpyNkGxHdskfdTNRSjjyNa5qC9u0JyV&export=download&authuser=0
