# Telco Customer Churn Prediction

## Predicting Customer Attrition with Machine Learning and Translating Results into Retention Insights

Customer churn directly affects recurring revenue, customer lifetime value and customer acquisition costs. This project applies supervised machine learning to telecommunications customer data to identify customers at greater risk of leaving and to investigate the characteristics associated with churn.

Rather than evaluating models on accuracy alone, the project places particular emphasis on **recall and false negatives**, because failing to identify a genuinely at-risk customer can prevent a business from intervening before that customer leaves.

---

## Business Problem

A telecommunications provider wants to understand:

- Which customer characteristics are associated with churn?
- Can customer churn be predicted using historical customer and account data?
- Which model provides the most useful balance between predictive accuracy and churn detection?
- Which customer segments may warrant greater retention attention?

The objective is both **predictive and diagnostic**: build churn-prediction models while translating the results into information that could support customer-retention decisions.

---

## Dataset

The original dataset contains **7,043 customers and 21 variables**. During preprocessing, `TotalCharges` was converted from text to numeric format, revealing 11 missing observations. These were removed, leaving **7,032 complete customer records**.

The target variable is `Churn`, where `0` means the customer remained and `1` means the customer churned.

The final class distribution was approximately **73.42% non-churn** and **26.58% churn**.

---

## Analytical Workflow

**Business Problem → Data Inspection → Cleaning → Exploratory Analysis → Feature Engineering → Model Preparation → Machine Learning → Model Evaluation → Business Interpretation**

The resulting modelling dataset contains **23 predictor variables**.

---

## Key Findings

- Tenure showed the strongest observed correlation with churn at approximately **-0.354**.
- Customers who churned had a median tenure of approximately **10 months**, compared with **38 months** among customers who remained.
- Longer-term contracts were associated with lower churn than month-to-month arrangements.
- Fibre-optic service, monthly charges and electronic-check payment emerged as relevant churn dimensions.

---

## Model Performance

### Logistic Regression

| Metric | Result |
|---|---:|
| Accuracy | **80.55%** |
| Precision | **65.28%** |
| Recall | **57.17%** |
| True Positives | **267** |
| False Positives | **142** |
| False Negatives | **200** |
| True Negatives | **1,149** |

### Random Forest

The Random Forest used **2,000 decision trees**, bootstrap sampling, out-of-bag estimation, `max_features="sqrt"` and `max_leaf_nodes=50`.

| Metric | Result |
|---|---:|
| Accuracy | **79.52%** |
| Precision | **66.56%** |
| Recall | **46.04%** |
| OOB Score | **79.94%** |
| True Positives | **215** |
| False Positives | **108** |
| False Negatives | **252** |
| True Negatives | **1,183** |

Under the original configurations, Logistic Regression provides the more useful balance for the retention objective because it identifies a larger proportion of actual churners.

---

## Portfolio Upgrade

The portfolio notebook extends the original bootcamp analysis with:

- F1 score
- ROC-AUC
- Precision-Recall AUC
- five-fold stratified cross-validation
- decision-threshold optimisation
- an illustrative business-cost framework
- reusable evaluation functions
- portfolio-ready visualisations

The objective is to evaluate the model in terms of **decision usefulness**, not accuracy alone.

---

## Repository Structure

```text
telco-customer-churn-prediction/
├── README.md
├── .gitignore
├── requirements.txt
├── notebooks/
│   └── telco_customer_churn.ipynb
├── data/
│   └── README.md
└── images/
    └── README.md
```

---

## Author

**Sebetja Success Phiri**

Data Science & Analytics | Python • SQL • Machine Learning • Business Innovation

[LinkedIn](https://www.linkedin.com/in/success-phiri-sebetja-b11154216)
