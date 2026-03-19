# Capstone Project — Written Responses
## 30-Day Hospital Readmission Prediction

## Question 1 — Problem Definition

Hospital readmissions within 30 days represent a major challenge in healthcare systems. They are associated with increased costs, inefficient resource utilization, and potential indicators of suboptimal care quality.

From a business and operational perspective, hospitals aim to reduce avoidable readmissions because they lead to financial penalties, higher workload, and reduced capacity for new patients. Identifying high-risk patients early can support targeted interventions such as follow-up care, medication adjustments, or improved discharge planning.

This project focuses on predicting whether a patient will be readmitted within 30 days using structured clinical and administrative data. The goal is to support risk stratification by identifying patients who are more likely to return shortly after discharge.

A useful outcome of this model is the ability to prioritize high-risk patients for preventive actions. For example, a model with a recall of approximately 0.50 can correctly identify about half of the patients who will be readmitted, which is valuable for proactive care management.

Ultimately, this project demonstrates how data-driven approaches can support better decision-making in healthcare systems by improving patient outcomes and reducing unnecessary costs.

## Question 2 — Approach & Tools

The problem was formulated as a supervised binary classification task, where the objective is to predict whether a patient will be readmitted within 30 days (1) or not (0).

The dataset consists of structured tabular healthcare data, which makes classical machine learning models more appropriate than more complex neural-network approaches. The available features are mainly categorical and numerical variables describing patient demographics, healthcare utilization, and treatment-related information.

A complete machine learning pipeline was implemented using scikit-learn, including:

- data preprocessing (handling missing values, encoding categorical variables, scaling numerical features)
- train-test split with stratification to preserve class distribution
- model training and evaluation using cross-validation

Several models were evaluated:

- Logistic Regression
- Random Forest
- Gradient Boosting
- Neural Network (MLP)

Model selection was based on cross-validated performance, with a focus on F1-score and recall due to class imbalance.

Logistic Regression was selected as the final model after hyperparameter tuning using RandomizedSearchCV. It achieved the strongest cross-validated balance between recall, F1-score, and interpretability. In comparison, more complex models such as Random Forest, Gradient Boosting, and MLP did not produce better F1 results on this dataset.

Final test performance:

- Accuracy: 0.6742
- Precision: 0.1718
- Recall: 0.5024
- F1-score: 0.2560
- ROC-AUC: 0.6449

Recall was prioritized because missing high-risk patients (false negatives) is more critical in healthcare settings than generating false positives.

More complex models such as neural networks were tested but not retained due to lower recall performance, reduced interpretability, and no significant improvement over simpler models.

## Question 3 — Reflection

This project highlighted several important challenges and insights related to applying machine learning to real-world healthcare data.

A major challenge was class imbalance. Most patients are not readmitted, which makes accuracy a misleading metric. A model predicting "no readmission" for all patients could still achieve high accuracy but would not be useful. Therefore, recall and F1-score were prioritized.

Another key insight is the trade-off between precision and recall. The final model achieved a recall of approximately 0.50 but a relatively low precision (0.17). This means that while many high-risk patients are correctly identified, there are also many false positives. In healthcare contexts, this trade-off is acceptable because failing to identify a high-risk patient can have more serious consequences.

Overfitting was addressed using cross-validation and evaluation on a separate test set. The similarity between the cross-validated F1-score and the final test F1-score suggests that overfitting was reasonably controlled.

Data leakage was mitigated by using a proper pipeline (ColumnTransformer and Pipeline), ensuring that preprocessing steps were applied only to the training data and not to the entire dataset.

However, several limitations remain:

- The dataset is historical (1999–2008) and may not reflect current clinical practices
- No external validation was performed
- The model is predictive only and does not establish causal relationships
- Some variables may indirectly encode sensitive information, introducing potential bias

Future improvements could include:

- validation on more recent or external datasets
- fairness analysis across patient subgroups
- use of explainability methods such as SHAP
- threshold tuning based on clinical cost considerations

Overall, this project demonstrates that building a machine learning model involves not only optimizing performance, but also understanding trade-offs, limitations, and real-world implications.
