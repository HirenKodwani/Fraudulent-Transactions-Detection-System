# Fraudulent-Transactions-Detection-System

📌 Project Overview

This project was developed as part of an internship task to detect fraudulent transactions in a financial dataset. The dataset contains over 6.3 million transactions across different types such as CASH-IN, CASH-OUT, DEBIT, PAYMENT, and TRANSFER. The goal was to build a machine learning model capable of identifying fraudulent behavior and provide actionable insights for prevention strategies.

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

🛠️ Approach & Methodology

Data Cleaning

Handled missing values, irrelevant IDs, and outliers

Checked for multicollinearity across features

Exploratory Data Analysis (EDA)

Distribution of transaction types

Fraud percentage across categories

Balance dynamics of fraudulent vs. non-fraudulent transactions

Feature Engineering

Created transaction-based ratio features (balance changes, relative amounts)

Selected important predictors using correlation and feature importance

Model Development

Implemented and compared models: Logistic Regression, Random Forest, Gradient Boosting

Chosen model: XGBoost / Random Forest for performance balance

Model Evaluation

Metrics used: Precision, Recall, F1-score, ROC-AUC

Focused on recall (catching fraud cases) while maintaining acceptable precision

Key Insights

Fraud is concentrated in TRANSFER and CASH-OUT transactions

Large balance drops with no balance change in destination accounts are strong indicators

Business flagging misses small but frequent fraudulent attempts

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
