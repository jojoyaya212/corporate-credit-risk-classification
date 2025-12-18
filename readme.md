# Corporate Credit Risk Classification

This project builds an **end-to-end corporate credit risk classification system** using firm-level financial ratios and machine learning models.  
The objective is to translate raw credit ratings into **interpretable risk levels** and evaluate how well different models can predict credit risk under real-world data challenges such as **class imbalance, outliers, and time dependence**.

---

## Project Overview

Corporate credit ratings are often granular, imbalanced, and difficult to model directly.  
This project addresses these issues by:

- Regrouping credit ratings into economically meaningful **risk levels**
- Performing extensive **exploratory data analysis**
- Applying **robust preprocessing** to financial ratios
- Training and comparing multiple **classification models**
- Interpreting results using confusion matrices, feature importance, and risk trade-offs

The focus is on **model interpretability, stability, and practical credit risk insight**, rather than black-box prediction.

---

## Data & Target Construction

### Original Credit Rating Distribution
![Original Rating Distribution](assets/images/credit_rating_original.png)

- Raw credit ratings are highly imbalanced
- Some extreme grades contain very few observations
- Direct modeling leads to unstable predictions

### Rating Regrouping Strategy
Original ratings are mapped into **five ordered risk levels**:

| Risk Level | Description |
|-----------|-------------|
| Very Low Risk | AAA / AA |
| Low Risk | A |
| Medium Risk | BBB |
| High Risk | BB / B |
| Highest Risk | CCC and below |

This regrouping improves class balance and aligns better with economic intuition.

### Post-Grouping Distribution
![Resampled Rating Distribution](assets/images/credit_rating_resampled.png)

---

## Exploratory Data Analysis (EDA)

Key EDA steps include:
- Distribution analysis of financial ratios
- Skewness and outlier diagnostics
- Sector-level and rating-agency comparisons
- Heatmaps and cross-tabulations for categorical variables

### Sector vs Risk Level
![Sector Risk Heatmap](assets/images/sector_vs_risk_level.png)

Clear structural differences appear across sectors, supporting their inclusion as predictive features.

---

## Data Preprocessing

### Numerical Variables
- Min-Max normalization
- Log10 transformation to reduce skewness
- Outlier capping using the **1.5×IQR rule**

### Categorical Variables
- One-hot encoding for:
  - Rating agency
  - Sector

### Train / Test / Validation Split
A **time-based split** is used to avoid look-ahead bias:
- Train: earlier years
- Test: subsequent year
- Validation: most recent year

---

## Modeling Approach

Multiple classification models are evaluated:

- Logistic Regression  
- K-Nearest Neighbors  
- Naive Bayes  
- LDA / QDA  
- Neural Network  
- **Random Forest**
- **XGBoost**

### Model Performance Comparison
![Model Comparison](assets/images/model_comparison.png)

Tree-based models consistently outperform linear and distance-based methods.

---

## Final Model Selection

### Why Random Forest & XGBoost?
- Handle non-linear relationships in financial ratios
- Robust to multicollinearity
- Perform well under moderate sample sizes
- Provide **feature importance** for interpretability

### Feature Importance (Example)
![Feature Importance](assets/images/feature_importance.png)

Key drivers include:
- Profitability metrics
- Leverage ratios
- Liquidity measures
- Cash flow stability indicators

---

## Model Evaluation

### Confusion Matrix (Final Model)
![Confusion Matrix](assets/images/confusion_matrix.png)

Key observations:
- Strong performance for **medium and low risk firms**
- Extreme high-risk class remains difficult due to limited samples
- Misclassifications mostly occur between adjacent risk levels, which is economically reasonable

---

## Financial Interpretation Example

### Return on Capital Employed vs Risk
![ROCE vs Risk](assets/images/return_on_capital_employed.png)

Higher credit quality firms show:
- Stronger and more stable returns
- Lower dispersion
- Clear separation from high-risk firms

---

## Key Findings

- Credit risk is **highly predictable** using financial ratios when classes are properly defined
- Class imbalance is the main limitation for extreme risk prediction
- Random Forest provides **balanced and stable performance**
- XGBoost offers strong potential with further tuning and more data
- Feature importance aligns well with financial intuition

---

## Limitations & Future Work

- Small sample sizes for extreme risk classes
- Limited macroeconomic variables
- No probability calibration (future extension)

Possible extensions:
- Macroeconomic stress scenarios
- Probability-of-default calibration
- Cost-sensitive classification
- Transition modeling across risk levels

---

## Disclaimer

This project is for **research and demonstration purposes only**.

- Results depend on historical data and modeling assumptions
- Outputs do **not** constitute investment or credit advice
- Models are not intended for real-world lending decisions without further validation

---

## Author

**Ke Zhang**  
Credit Risk Modeling · Financial Analytics · Machine Learning
