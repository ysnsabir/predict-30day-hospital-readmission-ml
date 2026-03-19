# Predicting 30-Day Hospital Readmission Risk

## Project Overview

This project develops a machine learning pipeline to predict whether a patient will be readmitted within 30 days of hospital discharge.

Hospital readmissions are costly and may indicate gaps in care coordination. Early identification of high-risk patients enables healthcare providers to prioritize interventions such as follow-up care, discharge planning, and medication management.

---

## Dataset

**Diabetes 130-US hospitals dataset (1999–2008)**  
Source: UCI Machine Learning Repository  
https://archive.ics.uci.edu/ml/datasets/diabetes+130-us+hospitals+for+years+1999-2008

The dataset contains structured clinical and administrative data, including:
- patient demographics
- hospital encounters
- diagnoses and procedures
- medication-related information

---

## Methodology

### 1. Data Processing
- Data cleaning and missing value handling
- Encoding categorical variables (one-hot encoding)
- Feature scaling for numerical variables
- Stratified train-test split to preserve class distribution
- Pipeline implementation using `ColumnTransformer` and `Pipeline` to prevent data leakage

---

### 2. Machine Learning

Models evaluated:
- Logistic Regression
- Random Forest
- Gradient Boosting
- Neural Network (MLP)

Model selection criteria:
- F1-score (primary metric)
- Recall (to reduce missed high-risk patients)
- Cross-validation stability

The final model selected is **Logistic Regression**, as it provided the best balance between performance, interpretability, and robustness.

---

### 3. Generative AI Integration

Generative AI was used to:
- Generate structured summaries of model performance
- Assist in documenting results, limitations, and insights

It was not used for model training, ensuring no impact on predictive results.

---

## Results

Final model performance (test set):

- Accuracy: **0.6742**
- Precision: **0.1718**
- Recall: **0.5024**
- F1-score: **0.2560**
- ROC-AUC: **0.6449**

The model prioritizes recall, meaning it successfully identifies approximately 50% of patients who will be readmitted.

---

## Limitations

- Dataset is historical (1999–2008)
- No external validation on independent datasets
- Limited clinical granularity
- Model is predictive only (no causal inference)
- Potential bias due to proxy variables

---

## Walkthrough Video

[Add your video link here]

---

## Repository Structure

```
capstone-readmission/
│
├── data/
│   └── diabetic_data.csv
│
├── notebooks/
│   └── capstone_readmission.ipynb
│
├── models/
│   └── best_readmission_model.joblib
│
├── outputs/
│   ├── model_comparison_results.csv
│   └── readmission_model_results.pdf
│
├── report/
│   └── written_responses.md
│
├── MODEL_CARD.md
├── README.md
├── requirements.txt
└── LICENSE
```

