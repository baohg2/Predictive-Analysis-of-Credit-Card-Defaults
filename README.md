# Predictive Analysis of Credit Card Defaults

## 📌 Project Objective
The goal of this project is to predict the likelihood of credit card clients defaulting on their payments. By moving beyond traditional binary classification, this analysis aims to refine risk assessment by identifying specific individuals likely to default, thereby enhancing the precision of financial risk management strategies.

## 📊 Dataset Overview
The dataset contains information on **10,000 clients** and includes 23 key predictors:
* **Target Variable:** `default payment next month` (1 = Yes, 0 = No).
* **Financial Features:** Credit limit (`LIMIT_BAL`), bill statement amounts, and previous payment amounts (April–September).
* **Demographic Features:** Age, Gender, Education, and Marital Status.
* **Repayment Status:** Monthly records of payment delays.

## 🛠️ Data Preprocessing & Engineering
To ensure high data quality and model performance, the following steps were taken:
* **Missing Value Imputation:** * Numerical variables (Age, Bill amounts) were filled using the **mean**.
    * Categorical/Ordinal variables (Sex, Education, Marriage, Pay status) were filled using the **mode**.
* **Feature Refinement:**
    * **Education:** Consolidated undocumented categories (`0`, `5`, `6`) into category `4` (Others) to reduce noise.
    * **Marriage:** Reassigned abnormal `0` values to category `3` (Others).
* **One-Hot Encoding:** Categorical variables (`SEX`, `MARRIAGE`, `EDUCATION`) were converted into dummy variables using `drop_first=True` to avoid the dummy variable trap (multicollinearity).
* **Feature Scaling:** Applied `StandardScaler` to normalize the data, ensuring distance-based models (like KNN) perform optimally.

## 🤖 Modeling & Performance
We compared two distinct classification models:

| Model | Training Accuracy | Test Accuracy | Status |
| :--- | :---: | :---: | :--- |
| **Logistic Regression** | **0.820** | **0.804** | ✅ Stable & Robust |
| **K-Nearest Neighbors** | 0.842 | 0.784 | ⚠️ Overfitting |

### Key Findings:
* **Logistic Regression** demonstrated excellent generalization with a minimal gap (1.6%) between training and test performance.
* **KNN** showed signs of overfitting, capturing noise in the training set that did not translate to unseen data.

## 💡 Conclusion & Recommendation
**Logistic Regression** is the recommended model for this application. While its training accuracy was slightly lower than KNN, its **superior test performance and high interpretability** make it ideal for the financial sector. In credit risk modeling, the ability to explain *why* a client is flagged for default (via model coefficients) is as critical as the prediction itself.

## 🚀 Author

Gia Bao Hoang
2. Ensure you have the following libraries installed:
   ```bash
   pip install pandas numpy matplotlib scikit-learn openpyxl
