# 🏭 End-to-End Machine Learning Pipeline for Surface Coating Corrosion Prediction


---

## 📈 Project Overview

This project develops an end-to-end machine learning pipeline to predict and optimize the corrosion resistance of industrial surface coatings. Leveraging both historical experimental and production data, the pipeline covers data exploration, regression, classification, feature engineering, model selection, and interpretation.

Surface coatings are critical in manufacturing, protecting products from corrosion and extending their lifespans. Machine learning models can help optimize coatings by predicting performance and identifying key factors that minimize corrosion.

---

## 🗂️ Project Structure

| Part | Description |
|------|-------------|
| 1. Data Exploration | Visualize and analyze variable distributions, relationships, and group differences. |
| 2. Regression      | Predict logit-transformed corrosion fraction using linear, Bayesian, and advanced regression models. |
| 3. Classification  | Classify whether corrosion is below 33% (EVENT) and identify key drivers using linear, Bayesian, and advanced classifiers. |
| 4. Feature Engineering & Selection | Engineer and evaluate derived features based on SME input. |
| 5. Model Selection & Interpretation | Compare, interpret, and visualize best models; recommend optimal input settings. |

---

## 🧪 Data Description

- **Inputs:**
  - Chemistry variables: `x1`, `x2`, `x3`, `x4`
  - Manufacturing process variables: `v1`, `v2`, `v3`, `v4`, `v5`
  - Machine used: `m` (categorical)
- **Output:**
  - Fraction of corroded surface after accelerated life testing (`output`)
- **Derived Features:**
  - `x5 = 1 - (x1 + x2 + x3 + x4)` (balance constituent)
  - `w = x2 / (x3 + x4)`
  - `z = (x1 + x2) / (x4 + x5)`
  - `t = v1 * v2`

---

## 🛠️ Pipeline Steps

### 1. Data Exploration
- Visualize distributions of all features and the response (including logit transformation).
- Explore group differences by machine type (`m`).
- Analyze correlations and relationships among features and response.

### 2. Regression Modeling
- **Base Features:** Use original input variables.
- **Expanded Features:** Use derived features and select subsets as appropriate.
- Fit 9 linear models (additive, interaction, basis functions), select and visualize top 3.
- Fit 2 Bayesian linear models (using `rstanarm` or Laplace Approximation).
- Compare models using appropriate metrics (e.g., RMSE, R²).
- Visualize predictive trends, confidence, and prediction intervals.

### 3. Classification Modeling
- Binary classification: EVENT if corrosion < 33%, NON-EVENT otherwise.
- Fit 9 GLMs (additive, interaction, basis functions), select and visualize top 3.
- Fit 2 Bayesian GLMs.
- Compare models using metrics (e.g., Accuracy, ROC AUC).
- Visualize predicted probabilities and feature importances.

### 4. Advanced Modeling & Feature Selection
- Train and tune complex models:
  - Regularized regression (Elastic Net)
  - Neural Networks
  - Random Forest
  - Gradient Boosted Trees
  - 2 additional methods (e.g., SVM, GAM, MARS, PLS, KNN, Stacking)
- Evaluate both base and expanded feature sets.
- Rank features by importance.

### 5. Model Interpretation & Optimization
- Identify best models and most important variables.
- Visualize predicted outcomes vs. key inputs.
- Recommend input settings to minimize corrosion.
- Explore differences across machine types.
- (Bonus) Perform input optimization for selected machine types.

---

## 📊 Technologies Used

- Python (or R, as appropriate)
- pandas, numpy, matplotlib, seaborn, scikit-learn, xgboost, lightgbm, tensorflow/keras, caret/tidymodels (R)
- Bayesian modeling: `rstanarm`, Laplace Approximation
- Jupyter Notebook / RMarkdown

---

## 💡 Key Insights & Goals

- **Optimize** surface coating recipes and process conditions to minimize corrosion.
- **Identify** which features (including derived SME features) are most predictive.
- **Classify** which conditions lead to high vs. low corrosion.
- **Interpret** the impact of chemistry, process, and machinery on corrosion outcomes.



## 📂 Getting Started

1. Clone this repository.
2. Place your data CSV file in the `data/` directory.
3. Run the notebooks or scripts in order:
    - `1_data_exploration.ipynb`
    - `2_regression.ipynb`
    - `3_classification.ipynb`
    - `4_feature_engineering.ipynb`
    - `5_model_selection_and_interpretation.ipynb`
4. Follow the instructions in each notebook/script for results and visualizations.

---

## 📑 References

- [PPG Industries](https://www.ppg.com)
- [Surface Coating Design and Testing](https://www.ppg.com/our-products)
- [scikit-learn documentation](https://scikit-learn.org/)
- [rstanarm documentation](https://mc-stan.org/rstanarm/)
- [tidymodels documentation](https://www.tidymodels.org/)

---

**Author:** Sharika Loganathan
**Date:** Dec 2022

---

