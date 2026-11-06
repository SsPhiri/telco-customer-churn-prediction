[README.md](https://github.com/user-attachments/files/34476548/README.md)
# Dataset

This directory is reserved for the dataset used in the Telco Customer Churn Prediction project.

## Dataset

**Telco Customer Churn Dataset**

The dataset contains customer demographic information, subscribed telecommunications services, account characteristics, billing information and customer churn status.

The original dataset contains:

- 7,043 customer observations
- 21 variables
- a binary churn outcome (`Churn`)

The analysis converts `TotalCharges` to numeric form. In the source data, 11 observations contain blank `TotalCharges` values; the notebook removes these rows, leaving 7,032 complete observations for modelling.

## Source

The dataset is the IBM Telco Customer Churn sample dataset.

Official IBM-hosted CSV:
`https://raw.githubusercontent.com/IBM/telco-customer-churn-on-icp4d/master/data/Telco-Customer-Churn.csv`

A commonly used mirror is also available on Kaggle under **Telco Customer Churn**.

## Local Setup

Download the CSV and save it in this directory using the filename:

`Telco-Customer-Churn.csv`

The expected repository path is:

`data/Telco-Customer-Churn.csv`

The notebook is stored at:

`notebooks/telco_customer_churn.ipynb`

The notebook includes flexible path detection so it can be run from either the repository root or the `notebooks/` directory.

## Data Handling

The raw dataset is intentionally not included in this portfolio bundle. Keeping the data separate makes the repository lighter and keeps the data source and provenance explicit.
