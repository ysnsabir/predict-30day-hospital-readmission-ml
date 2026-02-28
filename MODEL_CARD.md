# Model Card – 30-Day Hospital Readmission Prediction

## Model Overview
This project predicts whether a patient will be readmitted within 30 days of hospital discharge using structured clinical and administrative data.

**Task:** Binary classification  
- **1:** Readmitted within 30 days  
- **0:** Not readmitted within 30 days

---

## Intended Use
**Intended:**
- Educational / academic demonstration of an end-to-end ML pipeline
- Risk stratification exploration (research/learning context)

**Not intended:**
- Real-world clinical deployment
- Medical decision-making or patient care
- Use without clinical validation and governance approvals

---

## Dataset
**Name:** Diabetes 130-US hospitals dataset (1999–2008)  
**Source:** UCI Machine Learning Repository  
https://archive.ics.uci.edu/ml/datasets/diabetes+130-us+hospitals+for+years+1999-2008

**High-level features:**
- Demographics (e.g., age group)
- Encounter history (e.g., number of visits, length of stay proxies)
- Diagnoses and procedures (coded)
- Medication indicators

---

## Modeling Approach
**Preprocessing:**
- Missing-value handling
- One-hot encoding for categorical features
- Scaling for numeric features (as needed)
- Implemented with `ColumnTransformer` + `Pipeline` to reduce leakage risk

**Models evaluated:**
- Logistic Regression (baseline)
- Random Forest
- Gradient Boosting (or equivalent)

**Selection criteria:**
- Cross-validation performance
- F1-score and ROC-AUC
- Preference for higher recall to reduce missed high-risk patients

---

## Evaluation
**Metrics reported:**
- Accuracy
- Precision
- Recall
- F1-score
- ROC-AUC

**Why recall matters:**
Missing a high-risk patient (false negative) can be costly in healthcare settings, so recall is emphasized.

---

## Ethical Considerations & Risks
- **Bias:** Historical patterns may reflect demographic or systemic biases.
- **Data age:** 1999–2008 data may not reflect current clinical practice.
- **Proxy variables:** Some features may indirectly encode sensitive information.
- **Clinical risk:** Model outputs can be misused if interpreted as medical advice.

---

## Limitations
- Historical dataset; no external validation
- Limited clinical granularity
- No causal claims (predictive only)
- Not evaluated in a prospective or real-time setting

---

## Future Improvements
- External validation on newer/independent datasets
- Fairness assessment across subgroups
- Explainability methods (e.g., SHAP) to support interpretability
- Calibrated probabilities and threshold tuning aligned with clinical costs
