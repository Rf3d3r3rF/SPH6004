# MIMIC-IV ICU Discharge Prediction

## Overview
This repository contains the code and methodology for predicting Intensive Care Unit (ICU) discharge outcomes (survival vs. mortality) using structured, admission-level data from the MIMIC-IV (v3.1) database. The primary objective is to develop and evaluate predictive models that handle high dimensionality and severe class imbalance (~9% mortality rate) to assist in early clinical risk stratification.

## Methodology
1. **Data Preprocessing:** Removed variables causing data leakage (e.g., length of stay, time of death). Grouped fragmented demographic variables (Race and Language) into standard clinical categories to reduce sparsity.
2. **Feature Selection:** Applied L1-regularized Logistic Regression (LASSO) to minimize multicollinearity. The feature space was successfully optimized while maintaining full predictive power.
3. **Predictive Modeling:** Evaluated six supervised learning models: Logistic Regression, Support Vector Machine (SVM), Decision Tree, Random Forest, AdaBoost, and Gradient Boosting. Class weighting was applied to address the imbalanced dataset.

## Key Results
Because the dataset is heavily imbalanced, models were evaluated using both AUROC and AUPRC (Area Under the Precision-Recall Curve).

* **Top Performing Model:** Gradient Boosting achieved the highest discrimination with an **AUROC of 0.917** and an **AUPRC of 0.624**.
* **Clinical Interpretability:** Feature importance analysis revealed that respiratory instability (mean respiratory rate), neurological status (GCS components), and hemodynamic instability (blood pressure metrics) were the dominant predictors of ICU mortality, aligning tightly with established clinical knowledge. 

## Setup and Installation
1. Clone this repository to your local machine.
2. Ensure you have the required Python packages installed (e.g., `pandas`, `numpy`, `scikit-learn`, `matplotlib`).
3. Place the pre-extracted MIMIC-IV dataset CSV file into the `data/` directory.
4. Run the Jupyter notebooks in sequential order (`01` -> `02` -> `03`).

## Author
Fendianto
