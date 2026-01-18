# Bank Customer Churn Prediction: Strategic Machine Learning Pipeline

##  Project Overview
This repository contains a comprehensive implementation and comparative study of machine learning models designed to predict customer churn for banking institutions. Customer retention is a critical strategic priority, as the cost of acquiring a new customer is significantly higher than retaining an existing one. 

The project evaluates five classification algorithms—**Logistic Regression, Random Forest, XGBoost, LightGBM, and Gradient Boosting**—specifically focusing on addressing class imbalance (20.4% churn rate) using **SMOTE, Class Weight Adjustment, and SMOTE+Tomek Links**.



##  Dataset Overview
The project utilizes a Kaggle dataset of 10,000 bank customers, focusing on identifying patterns that lead to account closure.
* **Source**: [Kaggle - Bank Customer Churn Dataset](https://www.kaggle.com/datasets/gauravtopre/bank-customer-churn-dataset)
### Key Features:
* **Demographics**: Age, Geography (France, Spain, Germany), and Gender.
* **Account Information**: Tenure (years with the bank), Balance, Number of Products, and Active Membership status.
* **Financial Profile**: Credit Score and Estimated Salary.
* **Target Variable**: 1 if the customer churned, 0 if they remained.

### Data Distribution:
* **Retained (Majority Class)**: 79.6%
* **Churned (Minority Class)**: 20.4%
* **Challenge**: The significant class imbalance requires specialized handling (like SMOTE) to prevent the model from ignoring the minority churn class.



##  Key Objectives
* **Recall Optimization**: Prioritizing the identification of at-risk customers to minimize the financial impact of missed churners.
* **Imbalance Mitigation**: Evaluating synthetic oversampling (SMOTE) versus model-level weight adjustments.
* **Business Impact Modeling**: Translating statistical metrics into financial outcomes through a synthetic cost-benefit simulation.

##  Methodology
1.  **Exploratory Data Analysis (EDA)**: Identified key predictors such as Age, Number of Products, and Active Membership status.
2.  **Data Preprocessing**: Handled categorical variables via one-hot encoding and applied `StandardScaler` to numerical features.
3.  **Model Training & Validation**: Implemented 15 unique configurations with **5-fold cross-validation** to ensure stability.

##  Performance Evaluation
The experimental analysis concludes that ensemble methods, particularly when paired with class-weighting techniques, provide the highest recall.

| Model | Technique | Recall | Precision | F1-Score | Accuracy |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **XGBoost** | Class Weight | **0.7494** | 0.5161 | 0.6112 | 0.8060 |
| **LightGBM** | Class Weight | 0.7420 | 0.5119 | 0.6058 | 0.8035 |
| **Random Forest** | Class Weight | 0.6855 | 0.5753 | 0.6256 | 0.8330 |
| **Gradient Boosting** | SMOTE+Tomek | 0.5405 | 0.7074 | 0.6128 | 0.8610 |

##  Synthetic Business Cost Simulation
To assess practical utility, a business-impact scenario was simulated based on industry assumptions:
* **Cost of Attrition (False Negative)**: $100 per customer.
* **Cost of Retention (False Positive)**: $10 per customer.

### Financial Findings:
* **Cost Efficiency**: **Gradient Boosting with SMOTE** achieved the lowest simulated TBC of **$15,690**, representing a **24.7% reduction** in costs.
* **Linear Model Improvement**: Logistic Regression showed a **49.9% cost reduction** when paired with SMOTE.
> **Note**: This analysis is a synthetic simulation designed for model comparison. Actual financial impact may vary based on specific institutional cost structures.
