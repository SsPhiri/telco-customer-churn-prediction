# Dataset

This directory is reserved for the dataset used in the Telco Customer Churn Prediction project.

## Dataset

**Telco Customer Churn Dataset**

The dataset contains customer demographic information, subscribed telecommunications services, account characteristics, billing information and customer churn status.

The original dataset contains:

- 7,043 customer observations
- 21 variables
- a binary churn outcome

During preprocessing, 11 observations with missing `TotalCharges` values are removed, leaving 7,032 complete observations for analysis.

## Data Access

The dataset is not currently redistributed directly through this repository while its original source and redistribution terms are being documented.

The analysis notebook expects the dataset to be placed in this directory with the following filename:

`Telco-Customer-Churn.csv`

Expected path:

`data/Telco-Customer-Churn.csv`

## Reproducibility

After placing the dataset in this directory, the analysis can be run from:

`notebooks/telco_customer_churn.ipynb`

The notebook performs the required data cleaning and preprocessing before modelling.

## Data Usage

This project uses the dataset for educational and portfolio-based data science analysis. No individual represented in the dataset is identified within this repository.
