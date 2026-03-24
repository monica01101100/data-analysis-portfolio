# BankSim Fraud Detection

## Overview
This project develops a fraud detection framework using the BankSim synthetic transaction dataset. The objective is to identify suspicious financial behaviour by combining exploratory data analysis, statistical reasoning, and machine learning techniques.

The project follows a structured workflow: understanding transaction patterns, building baseline models, and improving performance through feature engineering and advanced modelling.

---

## Objectives
- Analyse transaction-level data to identify fraud patterns
- Build and evaluate baseline classification models
- Engineer features that capture behavioural anomalies
- Improve model performance using machine learning techniques

---

## Dataset Description
The dataset consists of simulated financial transactions. Each row represents a transaction between a sender and a receiver.

Key variables include:

- **amount** – transaction value  
- **type** – transaction category (e.g. transfer, payment, cash-out)  
- **nameOrig** – sender ID  
- **nameDest** – receiver ID  
- **oldbalanceOrg / newbalanceOrig** – sender balance before and after transaction  
- **oldbalanceDest / newbalanceDest** – receiver balance before and after transaction  
- **isFraud** – target variable (fraud vs legitimate)  

---

## Project Structure
banksim-fraud-detection/
│
├── data/
├── notebooks/
│   ├── 01_eda_and_imputation.ipynb
│   ├── 02_modelling_and_roc.ipynb
│   ├── 03_feature_engineering_and_advanced_modelling.ipynb
└── README.md

---

## Methodology

### 1. Exploratory Data Analysis
- Analysed distributions of transaction amounts
- Compared fraud vs non-fraud behaviour
- Identified strong class imbalance
- Explored transaction types and their relationship to fraud

---

### 2. Data Preparation
- Cleaned and structured data for modelling
- Introduced missing values and applied imputation techniques
- Ensured dataset consistency and usability

---

### 3. Baseline Modelling
- Logistic Regression model used as a benchmark
- Performance evaluated using ROC AUC
- Established a baseline for comparison with advanced models

---

### 4. Advanced Extension: Feature Engineering & Machine Learning

Feature engineering was introduced to better capture behavioural anomalies:

- **Relative transaction size (z-score)**  
  Measures how unusual a transaction is compared to a customer’s typical behaviour  

- **Balance consistency checks**  
  Detect discrepancies between expected and actual balance changes  

- **Transaction type encoding**  
  Converts categorical variables into model-ready features  

A Random Forest classifier was trained on these engineered features.

To ensure computational efficiency while maintaining representativeness, a sampled dataset was used for training.

---

## Results

- Feature engineering improved the model’s ability to distinguish fraudulent transactions  
- Behavioural features (e.g. transaction deviation, balance inconsistencies) were among the most important predictors  
- Random Forest outperformed baseline models by capturing non-linear patterns in the data  

---

## Key Insights

- Fraud detection is more effective when focusing on **behavioural anomalies**, not just raw transaction values  
- Transaction type plays a significant role in fraud likelihood  
- Balance inconsistencies are strong indicators of suspicious activity  

---

## Tools & Technologies

- Python (pandas, numpy)  
- scikit-learn  
- matplotlib, seaborn  

---

## Limitations

- Dataset is synthetic and may not fully reflect real-world financial behaviour  
- Customer identifiers are assumed to be stable, which may not always hold in practice  
- Time-based and network effects are not fully explored  

---

## Future Improvements

- Time-based features (e.g. transaction frequency, velocity)  
- Network-based fraud detection (relationships between accounts)  
- Advanced anomaly detection methods (Isolation Forest, Autoencoders)  

---