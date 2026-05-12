# BankSim Fraud Detection Project

## Project Overview
This project builds a clean machine learning pipeline to spot fraudulent credit card transactions using the BankSim dataset. 

Because financial fraud is rare (accounting for less than 1% of the data), looking at simple accuracy scores is misleading—a model could just guess "not fraud" every time and be 99% accurate. Instead, this project focuses on **feature engineering** to catch suspicious behavior and uses proper metrics like **ROC AUC and Precision-Recall** to evaluate success.

The project is split into three separate notebooks to keep the code clean and modular.

---

## Project Structure

```text
banksim-fraud-detection/
├── data/                    # Raw and processed datasets
├── notebooks/               # Step-by-step project code
│   ├── 01_eda_cleaning.ipynb       # Cleaning, exploring, and handling missing data
│   ├── 02_baseline_model.ipynb     # Setting up our first simple model (Logistic Regression)
│   └── 03_advanced_models.ipynb    # Grouping features and building a Random Forest
└── README.md                # Project overview and summary
```

---

## What Happens in Each Notebook

### 1. Data Cleaning and Exploration (`01_eda_cleaning.ipynb`)
* Analysed spending amounts and categories to see where fraudulent transactions cluster.
* Handled the extreme imbalance in the data (separating normal spending from fraud).
* Tested different ways to fill in missing data (imputation) to make sure the data stays clean for our models.

### 2. Building a Baseline Model (`02_baseline_model.ipynb`)
* Built a simple **Logistic Regression** model first. Starting with a basic model creates a benchmark so we can tell if more advanced models are actually worth the extra effort.
* Evaluated performance using ROC curves to make sure the model is actually good at telling the difference between fraud and normal transactions.

### 3. Smart Features & Advanced Models (`03_advanced_models.ipynb`)
Instead of just giving the model raw transaction numbers, new features were created to help the model think like a fraud investigator:
* **Relative Transaction Size (Z-Score):** Measures how much a transaction deviates from that specific customer’s normal spending habits.
* **Balance Consistency Check:** Calculates the difference between the starting balance, the ending balance, and the transaction cost to find accounting mismatches.
* **Transaction Grouping:** Encodes specific high-risk categories (like cash-outs and international transfers) so the model can spot patterns easily.

Finally, a **Random Forest** model was trained on the data. It successfully handled complex patterns and significantly reduced the number of missed fraud cases (false negatives).

---

## Key Findings

* **Behavior Beats Amount:** Just looking at the dollar amount of a transaction is not enough. The most powerful indicator of fraud is how much a transaction breaks a customer's typical behavioral pattern (their Z-Score).
* **High-Risk Channels:** Fraud rarely happens on small, everyday purchases. It is heavily concentrated in specific categories like cash-outs and transfers.
* **Tree Models Win:** The Random Forest model easily beat the baseline linear model because it is much better at identifying complex, overlapping warning signs.

---

## Tech Stack
* **Languages:** Python
* **Libraries:** Pandas, NumPy, Scikit-Learn, Matplotlib, Seaborn

---

## Project Limitations & Next Steps

* **Synthetic Data Limitations:** BankSim is a simulated dataset. While it is excellent for building pipelines, real-world bank data has more complex network relationships.
* **Static Identities:** The model assumes account numbers are completely secure, whereas real fraud often involves identity theft.
* **Next Steps:** Future versions of this pipeline will test **Isolation Forests** (unsupervised anomaly detection) and graph analytics to uncover organised networks of matching fraud accounts.