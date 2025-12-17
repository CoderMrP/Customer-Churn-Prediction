# Customer Churn Prediction (XGBoost)

## Project Overview
This project focuses on predicting customer churn using machine learning techniques.
The goal was not only to build a predictive model, but also to understand the **limitations
of churn prediction when customer behavior overlaps heavily**.

Multiple models and feature sets were tested, including Logistic Regression, Random Forest,
and XGBoost.

---

## Business Problem
Customer churn directly impacts revenue.  
The objective is to identify customers at risk of churn so that proactive retention
strategies can be applied.

Key challenges:
- Churn and non-churn customers exhibit similar behavior
- Strong feature overlap limits separability
- Accuracy alone is not a reliable metric for churn problems

---

## Dataset Summary
The dataset contains:
- Usage metrics (usage per seat, total usage)
- Support metrics (tickets, resolution time)
- Account attributes (tenure, seats, MRR)
- Satisfaction indicators

Target variable:
- `churn_lables` (1 = churn, 0 = not churn)

---

## Feature Engineering
Several engineered features were created:
- Usage normalization (usage per seat)
- Error and ticket rates
- Tenure-based features

Each feature was **validated against churn behavior** using quantile analysis
and cross-tabulation.

Features that did not show meaningful separation (e.g. trial flags,
binary satisfaction flags) were removed.

---

## Models Tested
- Logistic Regression (baseline)
- Random Forest
- XGBoost (final model)

All models converged to similar performance, indicating that **data limitations,
not model choice**, were the primary constraint.

---

## Final Model
- Algorithm: XGBoost
- Threshold: 0.6 (chosen to balance false positives and false negatives)
- Accuracy: ~0.55
- Strength: Identifies high-risk churn customers reasonably well
- Limitation: Non-churn customers lack strong distinguishing signals

---

## Why Accuracy is Limited
Despite extensive feature engineering and model tuning, accuracy plateaued around 55–60%.

This is due to:
- Heavy behavioral overlap between churn and non-churn customers
- Lack of time-based trend features (usage decay, inactivity streaks)
- Absence of renewal timing or billing-related signals

This is a common and realistic limitation in churn modeling.

---

## Key Takeaways
- Accuracy is not the primary success metric for churn models
- Threshold calibration is crucial for business decision-making
- Feature quality matters more than model complexity
- Honest evaluation is better than overfitting or leakage

---

## Future Improvements
Accuracy could be significantly improved by adding:
- Time-series usage trends
- Inactivity and recency features
- Renewal proximity and billing signals
- Engagement decay indicators

---

## Tools & Libraries
- Python
- Pandas, NumPy
- Scikit-learn
- XGBoost
- Matplotlib / Seaborn

---

## Author
Paras Saini  
MSc Data Analytics | Berlin  
