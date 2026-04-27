
# Customer Retention Strategy — End-to-End Machine Learning Project

A comprehensive end-to-end machine learning pipeline focused on **Telecom Customer Churn Prediction**. This project encompasses data cleaning, handling mixed data types, exploratory data analysis (EDA), feature engineering, and the training of multiple classification models to identify high-risk customers and drive retention strategies.

---

## 📂 Dataset

- **Name:** Telecom Customer Churn Dataset
- **Source:** Internal Company Records (provided in `Churn_Dataset.csv`)
- **Rows:** 7,043
- **Columns:** 23
- **Target Variable:** `Churn` (Yes/No)

The dataset contains detailed customer profiles, including demographics, service subscriptions (Internet, Security, Streaming), contract details, and support ticket history.

---

## 🗂️ Dataset Structure

| # | Column | Type | Description |
|---|---|---|---|
| 1 | `customerID` | object | Unique identifier for each customer |
| 2 | `gender` | object | Gender (Female, Male) |
| 3 | `SeniorCitizen` | int64 | Whether the customer is a senior citizen (1, 0) |
| 4 | `Partner` | object | Whether the customer has a partner (Yes, No) |
| 5 | `Dependents` | object | Whether the customer has dependents (Yes, No) |
| 6 | `tenure` | int64 | Number of months the customer has stayed |
| 7 | `PhoneService` | object | Whether the customer has a phone service |
| 8 | `MultipleLines` | object | Whether the customer has multiple lines |
| 9 | `InternetService` | object | Internet provider (DSL, Fiber optic, No) |
| 10 | `OnlineSecurity` | object | Whether the customer has online security |
| 11 | `OnlineBackup` | object | Whether the customer has online backup |
| 12 | `DeviceProtection` | object | Whether the customer has device protection |
| 13 | `TechSupport` | object | Whether the customer has tech support |
| 14 | `StreamingTV` | object | Whether the customer has streaming TV |
| 15 | `StreamingMovies` | object | Whether the customer has streaming movies |
| 16 | `Contract` | object | Term (Month-to-month, One year, Two year) |
| 17 | `PaperlessBilling` | object | Whether the customer has paperless billing |
| 18 | `PaymentMethod` | object | Electronic check, Mailed check, etc. |
| 19 | `MonthlyCharges` | float64 | Amount charged monthly |
| 20 | `TotalCharges` | object → float | Total amount charged |
| 21 | `numAdminTickets` | int64 | Number of administrative support tickets |
| 22 | `numTechTickets` | int64 | Number of technical support tickets |
| 23 | `Churn` | object | Binary Target (Yes, No) |

---

## 🎯 Project Objectives

### Exploratory Data Analysis (Key Findings)

| # | Objective | Graph Type | Key Insight |
|---|---|---|---|
| 1 | Churn Distribution | Pie Chart | Approximately 26.5% of the customer base has churned |
| 2 | Contract vs Churn | Bar Plot | Month-to-month contracts have significantly higher churn rates |
| 3 | Tenure vs Churn | Histogram | High churn risk during the "critical period" (first 12 months) |
| 4 | Internet Service Impact| Bar Plot | Fiber Optic users churn at a higher rate than DSL users |
| 5 | Payment Method | Count Plot | Electronic Check is the most common payment for churners |
| 6 | Support Tickets | Scatter Plot | High `numTechTickets` is a strong red flag for impending churn |
| 7 | Monthly Charges | KDE Plot | Customers with higher monthly charges are more likely to leave |
| 8 | Senior Citizen Status | Bar Plot | Senior citizens exhibit higher churn rates than younger users |
| 9 | Security/Backup | Bar Plot | Customers without Online Security/Backup churn more often |
| 10 | Gender Analysis | Bar Plot | Gender has a negligible impact on churn probability |

### Modeling Objectives
- **Classification:** Predict `Churn` (Yes/No) based on customer behavior and service features.
- **Explainability:** Identify the top features driving customer dissatisfaction.

---

## 🧹 Data Cleaning & Preprocessing

### 1. Data Type Correction
- `TotalCharges` contained empty strings for new customers (0 tenure). These were converted to numeric, and the empty values were handled by replacing them with `MonthlyCharges`.

### 2. Categorical Standardization
- Standardized values like "No internet service" or "No phone service" to a simple "No" across all service-related columns to reduce feature redundancy.

### 3. Missing Value Treatment
- Handled via median imputation for numerical features and mode for categorical features.

### 4. Feature Engineering
- **Tenure Bins:** Grouped continuous tenure into categories (e.g., 0-12 months, 12-24 months) to identify lifecycle risk.
- **Label Encoding:** Converted binary and multi-class categorical variables into numerical format for model compatibility.

---

## 🤖 Machine Learning Models

Four primary models were trained and evaluated on the processed dataset:

| Model | Task |
|---|---|
| **Logistic Regression** | Baseline linear classification |
| **K-Nearest Neighbors (KNN)** | Distance-based classification |
| **Decision Tree** | Rule-based classification & feature importance |
| **Gaussian Naive Bayes** | Probabilistic classification |

---

## 📈 Results

### Model Performance Metrics

| Model | Accuracy |
|---|---|
| **K-Nearest Neighbors (KNN)** | **75.4%** |
| Logistic Regression | 74.2% |
| Decision Tree | 72.8% |
| Naive Bayes | 71.5% |

🏆 **Best Model: KNN** with **75.4% accuracy**, providing a balanced approach to identifying churn patterns.

---

## 🔑 Key Business Insights

- **The Red Flag:** A high frequency of **Technical Support Tickets** is the strongest predictor of a customer leaving.
- **Contract Strategy:** Customers on **Month-to-Month contracts** are 4x more likely to churn than those on two-year plans.
- **Payment Friction:** The **Electronic Check** payment method is associated with higher churn; encouraging auto-pay (Credit Card/Bank Transfer) could improve retention.
- **Critical Window:** The first **12 months** are the most volatile; targeted onboarding and loyalty rewards should be focused here.

---

## 🗂️ Project Structure
Telecom-Churn-ML-Project/
│
├── Churn_Analysis_Project.ipynb    # Jupyter notebook with code & EDA
├── Churn_Dataset.csv               # Raw dataset
├── Report.pdf                      # Comprehensive project report
└── README.md                       # This summary file

## 🛠️ Tech Stack

- **Python 3.x**
- **pandas & NumPy** — Data manipulation
- **Matplotlib & Seaborn** — Advanced data visualization
- **scikit-learn** — Machine Learning algorithms and evaluation
- **Jupyter Notebook** — Development environment

---
