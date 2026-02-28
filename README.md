# Predicting 30-Day Hospital Readmission Risk

## Project Overview

This project develops a machine learning pipeline to predict whether a patient will be readmitted within 30 days of hospital discharge.

Hospital readmissions are costly and may indicate gaps in care coordination. Early identification of high-risk patients can support targeted interventions and improved healthcare outcomes.

---

## Dataset

Diabetes 130-US hospitals dataset (1999–2008)  
Source: UCI Machine Learning Repository  
https://archive.ics.uci.edu/ml/datasets/diabetes+130-us+hospitals+for+years+1999-2008

---

## Methodology

### 1. Data Processing
- Data cleaning and missing value handling
- Encoding categorical variables
- Feature scaling
- Stratified train-test split
- Pipeline implementation using ColumnTransformer

### 2. Machine Learning
Models evaluated:
- Logistic Regression
- Random Forest
- Gradient Boosting

Evaluation metrics:
- Accuracy
- Precision
- Recall
- F1-score
- ROC-AUC

Cross-validation and hyperparameter tuning were applied to select the best model.

### 3. Generative AI Integration
Generative AI was used to:
- Generate structured executive summaries of model performance
- Assist in documenting results and model limitations

The generative component does not influence model training and is used only for interpretability and reporting purposes.

---

## Results

The best-performing model is selected based on F1-score and ROC-AUC, prioritizing recall to minimize missed high-risk patients.

---

## Limitations

- Dataset is historical (1999–2008)
- Limited clinical detail
- No external validation
- Model not intended for real-world clinical deployment

## Walkthrough Video

[Link to be added]

---

## Repository Structure
