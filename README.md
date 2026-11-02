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

The objective is therefore both **predictive and diagnostic**: build churn-prediction models while translating the findings into information that could support customer-retention decisions.

---

## Dataset

The original dataset contains:

- **7,043 customers**
- **21 variables**
- demographic information
- service subscriptions
- account information
- billing behaviour
- customer churn status

During preprocessing, `TotalCharges` was converted from text to numeric format. This revealed **11 missing observations**, which were removed.

The final analysis therefore used:

**7,032 complete customer records**

The target variable was:

`Churn`

where:

- `0` = customer remained
- `1` = customer churned

The final churn distribution was approximately:

- **73.42% non-churn**
- **26.58% churn**

This class imbalance was considered when interpreting model performance.

---

## Analytical Workflow

The project follows an end-to-end machine-learning workflow:

**Business Problem → Data Inspection → Cleaning → Exploratory Analysis → Feature Engineering → Model Preparation → Machine Learning → Model Evaluation → Business Interpretation**

### Data Preparation

Key preprocessing steps included:

- converting `TotalCharges` to numeric format;
- handling missing observations;
- removing the customer identifier;
- encoding churn as a binary target;
- converting categorical variables into dummy variables;
- investigating redundant predictors;
- removing redundant encoded features; and
- validating the final modelling dataset.

The resulting modelling dataset contained **23 predictor variables**.

---

## Exploratory Data Analysis

Exploratory analysis was used to identify customer, service and billing characteristics associated with churn.

### Customer Tenure

Tenure showed the strongest observed correlation with churn at approximately:

**-0.354**

Customers who churned had a median tenure of approximately:

**10 months**

while customers who remained had a median tenure of approximately:

**38 months**

This suggests that the earlier stages of the customer relationship may represent an important retention period.

### Contract Structure

Longer-term contract categories showed lower associations with churn than the month-to-month reference category.

This suggests that contract structure may be associated with greater customer stability.

### Internet Service

Fibre-optic internet service showed a positive association with churn and later emerged as one of the more influential Random Forest predictors.

This does **not** establish causation, but suggests that the experience of fibre customers may warrant deeper investigation.

### Billing and Payment

Higher monthly charges and electronic-check payment also showed meaningful relationships with churn.

These patterns suggest that pricing, perceived value and payment experience may contribute useful information when identifying higher-risk customers.

---

## Machine-Learning Preparation

The cleaned data was divided using a stratified train/test split:

| Dataset | Observations | Share |
|---|---:|---:|
| Training | 5,274 | 75% |
| Test | 1,758 | 25% |

Stratification preserved the churn-class distribution across the training and test datasets.

For Logistic Regression, Min-Max scaling was fitted **only to the training data** and subsequently applied to the test data to avoid preprocessing leakage.

---

## Models

Two supervised classification algorithms were evaluated.

### Logistic Regression

Logistic Regression was used as an interpretable baseline binary classifier.

Performance on the held-out test set:

| Metric | Result |
|---|---:|
| Accuracy | **80.55%** |
| Precision | **65.28%** |
| Recall | **57.17%** |
| F1 Score* | **60.96%** |
| True Positives | **267** |
| False Positives | **142** |
| False Negatives | **200** |
| True Negatives | **1,149** |

\*F1 calculated from the recorded precision and recall values.

The model identified approximately **57% of all customers who actually churned**.

---

### Random Forest

The Random Forest model was configured using:

- **2,000 decision trees**
- bootstrap sampling
- out-of-bag estimation
- `max_features="sqrt"`
- `max_leaf_nodes=50`

Performance:

| Metric | Result |
|---|---:|
| Accuracy | **79.52%** |
| Precision | **66.56%** |
| Recall | **46.04%** |
| F1 Score* | **54.43%** |
| OOB Score | **79.94%** |
| True Positives | **215** |
| False Positives | **108** |
| False Negatives | **252** |
| True Negatives | **1,183** |

\*F1 calculated from the recorded precision and recall values.

The similarity between the **79.94% OOB score** and **79.52% test accuracy** suggests relatively consistent generalisation under the current model configuration.

---

## Model Comparison

Although Random Forest produced slightly stronger precision, Logistic Regression delivered substantially better recall.

For a retention application, this distinction matters.

Random Forest missed:

**252 actual churners**

while Logistic Regression missed:

**200 actual churners**

That represents **52 additional at-risk customers** who would be missed if the Random Forest predictions were used under the current configurations.

Because the business objective is to identify customers who may require retention intervention, **Logistic Regression provides the more appropriate current model**.

Its performance is not yet sufficient for production deployment, however. A recall of 57.17% still means that a significant proportion of churners remain unidentified.

---

## Feature Importance

Random Forest identified the following among its most influential predictors:

| Feature | Importance |
|---|---:|
| Tenure | **0.212** |
| Total Charges | **0.135** |
| Fibre-optic Internet | **0.115** |
| Monthly Charges | **0.110** |
| Two-Year Contract | **0.083** |
| Electronic Check | **0.079** |
| No Internet Service | **0.051** |
| One-Year Contract | **0.039** |
| Online Security | **0.032** |
| Technical Support | **0.026** |

Tenure emerged as the strongest feature under both exploratory and predictive analyses.

Feature importance should not be interpreted as proof that a variable causes churn. It shows how strongly the Random Forest relied on that predictor when making classifications.

---

## Business Insights

The analysis highlights several areas that could guide further customer-retention investigation.

**Early customer lifecycle:** Churned customers had substantially shorter tenure, suggesting that onboarding and early customer experience deserve particular attention.

**Contract structure:** Longer contractual relationships were associated with lower churn, suggesting that suitable longer-term retention incentives could be investigated.

**Fibre customers:** Fibre-optic customers showed a higher association with churn. Pricing, reliability, expectations and support experience could be investigated further before any causal conclusion is drawn.

**Billing experience:** Monthly charges and electronic-check payment emerged as relevant churn dimensions, suggesting that perceived value and payment experience may influence retention behaviour.

**Targeted intervention:** Predictive churn scores could eventually support differentiated retention strategies instead of applying the same intervention to every customer.

---

## Technologies

`Python`  
`pandas`  
`NumPy`  
`Matplotlib`  
`Seaborn`  
`scikit-learn`  
`Jupyter Notebook`

Machine-learning techniques include:

`Logistic Regression`  
`Random Forest Classification`  
`Feature Encoding`  
`Feature Scaling`  
`Feature Importance`  
`Classification Evaluation`

---

## Current Limitations

This project demonstrates an end-to-end classification workflow, but further work is required before the model could be considered production-ready.

The next development phase will investigate:

- F1, ROC-AUC and Precision-Recall AUC;
- cross-validation;
- classification-threshold optimisation;
- class-imbalance strategies;
- hyperparameter optimisation;
- cost-sensitive churn classification;
- reusable scikit-learn pipelines;
- model explainability;
- model persistence and deployment; and
- monitoring for model and data drift.

This is particularly important because the optimal classification threshold for a retention programme should reflect the relative business costs of false positives and false negatives.

---

## Key Takeaway

The project demonstrates that predicting churn is not simply a question of maximising model accuracy.

For customer retention, the more important question is:

> **How effectively can the model identify genuinely at-risk customers early enough for the business to act?**

Under the current configuration, Logistic Regression provides the strongest balance, but further threshold optimisation and model development are required to improve churn detection.

---

## Author

**Sebetja Success Phiri**

Data Science & Analytics  
Python • SQL • Machine Learning • Business Innovation

LinkedIn:  
www.linkedin.com/in/success-phiri-sebetja-b11154216
