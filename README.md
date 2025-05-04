# Telecom User Retention - Final Project (S17)

## 📌 Project Objective

The objective of this project is to forecast customer churn for **Interconnect**, a telecom company. Predicting which users are likely to leave allows the company to proactively offer promotions or service improvements to increase customer retention.

## 🏢 Company Background

Interconnect offers:

- **Landline communication**: Customers may connect to multiple lines.
- **Internet services**: Delivered via DSL or fiber optic cable.
- **Add-on services**:
  - Device Protection (antivirus)
  - Online Security (website blocker)
  - Online Backup (cloud storage)
  - Tech Support
  - Streaming TV and Movies

Customers can choose a **monthly**, **1-year**, or **2-year** contract, with optional **paperless billing** and a variety of **payment methods**.

---

## 📂 Dataset Overview

The dataset spans from **October 1, 2013 to February 1, 2020** and includes four CSV files:

### `contract.csv`
| Column | Description |
|--------|-------------|
| `customerID` | Unique ID for each customer |
| `BeginDate` | Subscription start date |
| `EndDate` | Subscription end date or 'No' if still active |
| `Type` | Contract type (Month-to-month, One year, etc.) |
| `PaperlessBilling` | Yes/No |
| `PaymentMethod` | Method of payment (e.g., Electronic check) |
| `MonthlyCharges` | Monthly billed amount |
| `TotalCharges` | Total billed amount |

### `personal.csv`
| Column | Description |
|--------|-------------|
| `customerID` | Unique ID |
| `gender` | Male/Female |
| `SeniorCitizen` | 1 = Yes, 0 = No |
| `Partner` | Yes/No |
| `Dependents` | Yes/No |

### `internet.csv`
Contains information about services like OnlineBackup, OnlineSecurity, etc.

### `phone.csv`
Includes service details such as whether the user has a multiple line plan.

---

## 🧠 Methodology

1. Load and inspect all data frames.
2. Clean data:
   - Convert "Yes"/"No" to binary
   - Replace 'No' in `EndDate` with max date
   - Convert date columns to datetime
3. Merge all dataframes on `customerID`.
4. Feature engineering:
   - Length of subscription
   - Count of internet add-on services
   - One-hot encode categorical features
5. Exploratory Data Analysis (EDA):
   - Distributions of charges, payment types, churn, senior citizen status, etc.
6. Model training and evaluation:
   - Train/test split
   - Fit several models and assess performance using AUC-ROC and other classification metrics
   - Feature importance analysis

---

## ✅ Results

The **Gradient Boosting Classifier** delivered the strongest results:

- **AUC-ROC Score**: `0.9347` – excellent ability to distinguish churned vs. retained users.
- **Accuracy**: `89.55%`
- **Non-churned Customers**:
  - Precision: `0.90`
  - Recall: `0.97`
  - F1-score: `0.93`
- **Churned Customers**:
  - Precision: `0.90`
  - Recall: `0.66`
  - F1-score: `0.76`

These results highlight the model's strength in identifying users likely to stay while still maintaining respectable performance in flagging potential churners. However, the slightly lower recall on the churned class suggests room for improving sensitivity toward actual churn cases.

---

## 🛠 Technologies Used

- Python
- Pandas, NumPy
- scikit-learn
- Matplotlib, Seaborn
- Jupyter Notebook

---

## 📈 Future Improvements

- Tune threshold to improve recall for churned customers
- Perform cost-benefit analysis of retention offers
- Integrate the model into a real-time dashboard for business use

