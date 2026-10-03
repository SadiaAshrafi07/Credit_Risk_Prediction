# 💳 Credit Risk Prediction with Machine Learning

> **An end-to-end ML application that evaluates loan applications and predicts credit risk through an interactive Streamlit interface.**

![Python](https://img.shields.io/badge/Python-3.x-blue?logo=python)
![XGBoost](https://img.shields.io/badge/ML-XGBoost-orange)
![Streamlit](https://img.shields.io/badge/App-Streamlit-red?logo=streamlit)
![Scikit Learn](https://img.shields.io/badge/Scikit--Learn-ML-F7931E?logo=scikit-learn)
![Pandas](https://img.shields.io/badge/Data-Pandas-150458?logo=pandas)

---

## 🌟 Project Snapshot

Credit institutions need to evaluate applicants before approving loans. This project demonstrates how machine learning can assist that process by analyzing applicant characteristics and estimating whether an application represents a **Good** or **Bad** credit risk.

The complete workflow is implemented in Python — from data preparation and exploratory analysis to model comparison, hyperparameter tuning, model persistence, and deployment through Streamlit.

### 🎯 Objective

Build a practical machine learning solution that can:

- 📥 Accept applicant information
- 🧹 Clean and prepare the input data
- 🔄 Transform categorical variables
- 🤖 Train multiple classification algorithms
- 🔍 Compare model performance
- ⚙️ Tune the selected models
- 💾 Save the trained model and encoders
- 🌐 Provide predictions through a Streamlit application
- 📊 Display the prediction probability to the user

---

# 📊 Dataset

The project uses the **German Credit dataset**, containing information about **1,000 loan applicants**.

### Important Features

| Feature | Description |
|---|---|
| 👤 Age | Applicant's age |
| 🚻 Sex | Applicant gender |
| 💼 Job | Skill/employment level |
| 🏠 Housing | Housing situation |
| 💰 Saving accounts | Applicant's savings level |
| 🏦 Checking account | Checking account status |
| 💵 Credit amount | Requested loan amount |
| ⏳ Duration | Loan duration in months |
| 🎯 Purpose | Reason for requesting the loan |
| ⚠️ Risk | Target variable — Good / Bad |

> **Note:** `Purpose` is currently retained in the dataset but is not included in the trained model.

The `Saving accounts` and `Checking account` columns contain missing values. In the current implementation, records containing missing values are removed before modeling, resulting in approximately **525 usable records**.

---

# 🔎 Exploratory Data Analysis

Before training the models, the dataset was explored to understand applicant characteristics and relationships between variables.

### 📈 Analysis Performed

- Distribution analysis
- 📦 Boxplots for numerical variables
- 📊 Count plots for categorical variables
- 🔥 Correlation heatmap
- 🎯 Risk-category comparisons
- 🔍 Feature-level investigation

This helped identify patterns, data quality issues, and potential relationships between applicant characteristics and credit risk.

---

# 🧹 Data Preparation Pipeline

The preprocessing workflow consists of several stages:

### 1️⃣ Data Cleaning

- Removed the unnecessary index column
- Identified missing values
- Removed records containing missing categorical account information

### 2️⃣ Categorical Encoding

Categorical variables were transformed using `LabelEncoder`.

Individual encoder objects are saved using **Joblib** so that the Streamlit application applies exactly the same mappings used during training.

### 3️⃣ Train-Test Split

The processed dataset is divided into:

```text
80% → Training Data
20% → Testing Data
