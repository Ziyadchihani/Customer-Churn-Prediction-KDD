# Customer Churn Prediction: A Comparative Study of 10 ML Models

An end-to-end data mining solution for predicting customer churn using the [Kaggle Customer Churn Dataset](https://www.kaggle.com/datasets/muhammadshahidazeem/customer-churn-dataset), following the **KDD (Knowledge Discovery in Databases)** methodology[cite: 1].

## 📊 Executive Summary
* **Problem:** Customer churn directly impacts revenue[cite: 1]. Retaining an existing customer is estimated to be 5 to 7 times more cost-effective than acquiring a new one[cite: 1].
* **Solution:** Developed a systematic multi-step preprocessing pipeline and evaluated 10 machine learning classification models[cite: 1].
* **Top Performer:** **XGBoost** achieved the best predictive power with **76% Accuracy** and an **AUC-ROC of 81%** on the fully preprocessed dataset[cite: 1].

---

## 🛠️ Data Preprocessing Pipeline (KDD Process)
The target variable exhibits a pronounced class imbalance (~90% non-churned vs. ~10% churned)[cite: 1]. Preprocessing steps were systematically evaluated to measure their cumulative impact on dataset quality and model performance[cite: 1]:

1. **Feature Dropping:** Irrelevant unique identifiers that carry no predictive signal were dropped to prevent noise and data leakage[cite: 1].
2. **Missing Value Imputation:** Handled 2,045 missing values in `complaint_type` by treating the absence of a complaint type as a dedicated category ("No Complaint")[cite: 1].
3. **Categorical Encoding & Feature Scaling:** Applied robust transformations and feature normalization (crucial for distance-based models like SVM and KNN)[cite: 1].
4. **Feature Selection:** Filtered the dataset down to the **Top 8 most impactful features** (such as `tenure_months`, `csat_score`, and `payment_failures`) using XGBoost-derived importance scores to reduce model complexity[cite: 1].

---

## 🤖 Models Evaluated & Performance
Ten classification models were trained and compared using an 80/20 stratified train-test split and 5-fold cross-validation on the training set[cite: 1].

### Final Model Rankings (Preprocessed Test Set)
| Rank | Model | Accuracy | F1-Score | AUC-ROC |
|------|-------|----------|----------|---------|
| **1** | **XGBoost** | **0.76** | **0.38** | **0.81** |
| 2 | Gradient Boosting | 0.75 | 0.38 | 0.81 |
| 3 | AdaBoost | 0.74 | 0.38 | 0.80 |
| 4 | Random Forest | 0.83 | 0.31 | 0.76 |
| 5 | SVM | 0.73 | 0.31 | 0.76 |
| 6 | Decision Tree | 0.77 | 0.35 | 0.67 |
| 7 | Logistic Regression | 0.65 | 0.27 | 0.74 |
| 8 | MLP | 0.90 | 0.16 | 0.76 |
| 9 | Naïve Bayes | 0.90 | 0.08 | 0.78 |
| 10 | KNN | 0.90 | 0.01 | 0.69 |

---

## 🎯 Key Business Insights & Recommendations
* **Deploy Churn Scoring:** Implement the trained XGBoost model to score existing customers monthly, proactively flagging accounts with a predicted churn probability above 76%[cite: 1].
* **Prioritize Contract Incentives:** Focus retention campaigns on month-to-month contract holders, as they demonstrated a higher propensity to churn[cite: 1].
* **Target High-Value Retention:** Proactively offer personalized discounts or account reviews to high-charge, short-tenure customers who present a strong churn signal[cite: 1].
