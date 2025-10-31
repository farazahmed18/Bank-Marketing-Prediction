# 🌟 Bank Mortgage Lead Identification Model

> A machine learning project to identify potential mortgage clients from an existing term deposit telemarketing campaign. This project was completed as an academic assessment for an MSc in Data Science and AI.

---

## 🎯 Business Goal

A bank's Mortgage Department wants to increase its customer base by finding new clients. Instead of launching a new, large-scale marketing campaign, this project uses data from an *existing* telemarketing campaign (for term deposits) to identify potential leads.

The objective is to build a profile of customers who are most likely to be in the market for a loan, so they can be targeted with a separate, more efficient mortgage campaign.

* **Key Business Indicator:** The model predicts **Housing Loan Propensity**, defined as a predictive measure of a customer's likelihood to need a housing loan based on their profile.

## 📊 Dataset

The data used is the **Bank Marketing Dataset** from the UCI Machine Learning Repository. It consists of 17 attributes related to customer demographics, finances, and campaign contact history.

**Key Attributes:**
* `age`: Customer's age (Numerical)
* `job`: Type of job (Categorical)
* `balance`: Average yearly balance in Euros (Numerical)
* `loan`: Has a personal loan? (Binary)
* `duration`: Last contact duration in seconds (Numerical)
* `month`: Last contact month of year (Categorical)
* **`housing` (Target Variable)**: Has a housing loan? (Binary)

---

## 🛠️ Methodology

This project follows a standard data science workflow for a binary classification problem.

### 1. Data Preprocessing
* **Encoding:** The target variable `housing` and other binary text features (like `loan`) were converted from "yes/no" to a numeric 1/0 format. Remaining categorical features (like `job` and `month`) were one-hot encoded to be used in mathematical models.
* **Data Split:** The data was split into an **80% training set** and a **20% testing set**.
* **Feature Scaling:** To prevent data leakage, `StandardScaler` was fit *only* on the 80% training data. It was then used to transform both the training and test sets, ensuring the model treats all features equally.

### 2. Model Selection
Two models were selected for this classification task:
1.  **Logistic Regression:** Chosen as a classic, fast, and efficient linear model that provides a good baseline for classification.
2.  **Random Forest:** Chosen as a powerful ensemble model that can capture complex, non-linear relationships. Its most important benefit for this project is its ability to **extract feature importances**, which is essential for the analysis and recommendations.

### 3. Evaluation Metrics
Models were evaluated on their ability to correctly classify customers, using:
* **Accuracy:** Percentage of correct predictions.
* **Precision:** Of all customers predicted to have a loan, how many *actually* did?
* **Recall:** Of all customers who *actually* have a loan, how many did the model find?
* **F1-Score:** The harmonic mean of Precision and Recall, providing a single score for the model's overall effectiveness.

---

## 📈 Results and Analysis

### Model Performance
The Random Forest model was the clear superior performer across all metrics, demonstrating it is a more robust and reliable model for this business problem.

| Model | Accuracy | Precision | Recall | F1-Score |
| :--- | :--- | :--- | :--- | :--- |
| **Random Forest** | **0.7892** | **0.7897** | **0.7892** | **0.7894** |
| Logistic Regression | 0.7547 | 0.7600 | 0.7547 | 0.7554 |

### Key Findings: What drives a mortgage lead?
Feature importance analysis from the Random Forest model revealed the top predictors for housing loan propensity.

The most important predictors were a mix of campaign timing and customer attributes:
1.  `month_may` (Importance: 0.1248)
2.  `age` (Importance: 0.1196)
3.  `balance` (Importance: 0.1195)
4.  `duration` (Importance: 0.1157)
5.  `day` (Importance: 0.1072)

The high importance of `month_may` shows a strong seasonal factor in housing loan activity. More importantly, customer-specific financial DNA like `age`, `balance`, and existing `loan` status are critical for building a predictive profile.

---

## 💡 Actionable Recommendations

Based on the model's findings, the following actions are recommended for the bank to increase the mortgage department's ROI:

1.  **Deploy a Customer Scoring System:** Use the trained Random Forest model to score the entire customer database. This creates a "hot-list" of high-propensity leads to prioritize for the mortgage department.
2.  **Analyze Seasonal & Demographic Drivers:** Investigate *why* `month_may` is such an important month to optimize campaign timing. Further analyze the high-propensity `age` and `balance` brackets to create new, tailored mortgage products.
3.  **Launch a Cross-Sell Strategy:** The `loan` feature shows a clear opportunity. The bank should create targeted campaigns for high-propensity customers:
    * For those *with* personal loans, offer debt consolidation.
    * For those *without* personal loans, offer bundled furnishing loans.

## ⚙️ How to Use This Project

1.  Clone this repository to your local machine.
2.  Install the required libraries: `pandas`, `numpy`, `scikit-learn`, `matplotlib`, `seaborn`.
3.  Open the Jupyter Notebook `bankcode.ipynb` to review the complete code and analysis.
4.  The `bank-full.csv` dataset is included in this repository.

---
*This project was completed by Faraz Ahmed Siddiqui for Machine Learning & AI assessment.*
