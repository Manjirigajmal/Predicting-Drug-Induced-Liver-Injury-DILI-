# Predicting Drug-Induced Liver Injury (DILI) Using Machine Learning

## 🔍 Project Overview

Drug-Induced Liver Injury (DILI) is a major cause of late-stage drug failures, withdrawals, and serious patient safety issues.  
In this project, I built a machine learning pipeline to **predict DILI risk** for small molecules using simple, interpretable **molecular descriptors**.

- **Goal:** Classify compounds as **Safe (0)** or **Toxic (1)** for DILI risk  
- **Data:** Synthetic dataset of **2,000 compounds** with key molecular features  
- **Best model:** **Logistic Regression**  
- **Performance:** ~**82% accuracy** and **ROC-AUC ≈ 0.89** with strong recall for the toxic class  

This project demonstrates how interpretable ML can support **early safety screening** in drug discovery.

---

## 📊 Dataset

- **Samples:** 2,000 compounds  
- **Target:** `DILI_Risk`  
  - `0` = Safe  
  - `1` = Toxic  
- **Features (molecular descriptors):**
  - `LogP` – Lipophilicity  
  - `Molecular_Weight`  
  - `H_Bond_Donors`  
  - `H_Bond_Acceptors`  
  - `Rotatable_Bonds`  
  - `Aromatic_Rings`  
  - `CYP3A4_Substrate` (binary flag)  
  - (plus any additional engineered features used in the notebook)

The dataset is **synthetic**, generated to mimic realistic structure–toxicity patterns while keeping the project fully reproducible.

---

## 🔬 Methodology

1. **Data Exploration (EDA)**
   - Class balance check (Safe vs Toxic)
   - Distribution plots for all molecular descriptors
   - Boxplots comparing feature distributions between Safe vs Toxic compounds
   - Correlation analysis between features and target

2. **Preprocessing**
   - Train–test split (80/20, stratified on `DILI_Risk`)
   - Standardization of numeric features for linear models (e.g., Logistic Regression)
   - Tree-based models trained on unscaled data

3. **Models Compared**
   - Logistic Regression  
   - Random Forest  
   - Gradient Boosting  
   - XGBoost  

4. **Evaluation Metrics**
   - Accuracy  
   - Precision, Recall, F1-score (with focus on **Toxic class**)  
   - ROC-AUC  
   - 5-fold **Stratified cross-validation** for the final model

---

## 🧠 Results

### Model Comparison (Test Set)

| Model               | Accuracy | Precision | Recall | F1    | ROC-AUC |
|---------------------|----------|-----------|--------|-------|---------|
| Logistic Regression | 0.8200   | 0.7471    | 0.8141 | 0.7791| 0.8930  |
| XGBoost             | 0.7975   | 0.7551    | 0.7115 | 0.7327| 0.8813  |
| Gradient Boosting   | 0.7925   | 0.7450    | 0.7115 | 0.7279| 0.8811  |
| Random Forest       | 0.7950   | 0.7500    | 0.7115 | 0.7303| 0.8699  |

**Key takeaway:**

- **Logistic Regression** achieved the **best ROC-AUC (~0.89)** and **highest recall for toxic compounds**, making it a strong, interpretable choice for early safety screening.

---

## 🧬 Model Interpretability

For the Logistic Regression model:

- **Higher risk of DILI** is associated with:
  - Higher `LogP` (more lipophilic)
  - Higher `Molecular_Weight`
  - More `Rotatable_Bonds`
  - More `Aromatic_Rings`
  - Being a `CYP3A4_Substrate`

- Some features (e.g., higher `H_Bond_Donors`) show a mild protective or balancing effect.

These trends are consistent with **medicinal chemistry intuition** and help explain *why* certain molecules are flagged as high-risk.

---

## 🛠️ Tech Stack

- **Language:** Python  
- **Libraries:**
  - `pandas`, `numpy`
  - `scikit-learn`
  - `xgboost`
  - `matplotlib`, `seaborn`
- **Environment:** Jupyter / Google Colab

---


