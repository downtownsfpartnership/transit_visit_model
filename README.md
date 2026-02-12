# Transit Activity and Downtown Visitation Modeling in Downtown San Francisco

This project models how regional mobility trends, such as transit ridership and bridge traffic, historically align with visitor volumes in the Downtown San Francisco Partnership district. Using monthly data from 2020 to 2025, the goal is to quantify how changes in major transportation modes correspond with changes in downtown visitation.
This work supports the Downtown SF Partnership’s transit dashboard and related advocacy tools by translating transit performance into downtown-relevant outcomes.

## Overview

Downtown visitation is treated as the dependent variable, and regional mobility indicators are treated as explanatory variables:
- **BART ridership**
- **MUNI ridership**
- **Ferry ridership**
- **Bridge crossings**
To account for seasonal travel patterns (e.g., recurring summer peaks and winter declines), the model includes monthly indicator variables (“month dummies”).
All mobility variables and visits are modeled in log form, allowing coefficients to be interpreted as elasticities (percent change relationships).


## Key Methods

### 1. Regularized Regression (Elastic Net / LASSO)
ElasticNet regression is used for variable selection and coefficient stability. This approach combines:
- LASSO (L1 penalty): encourages sparsity (dropping redundant predictors)
- Ridge (L2 penalty): improves stability when predictors are correlated
The model is tuned using cross-validation to select the optimal penalty strength (alpha) and sparsity level (l1_ratio).

### 2. Model Validation (Chronological Holdout)
To ensure results generalize beyond the training data, the model is evaluated using:
- train-test split (70/30)
- held-out performance metrics (test R²)
This ensures the model is not only fitting historical patterns but also performs well on unseen periods.

### 3. Robustness Check: Growth Rate (Log Difference) Specification
A major challenge in post-COVID data is that many variables trend upward simultaneously during recovery, which can inflate correlation in levels-based models.
To reduce this risk, the analysis includes a second specification using log differences (diff()), representing month-over-month growth rates
This formulation shifts the model from explaining recovery levels to explaining short-term fluctuations, helping isolate whether mobility changes continue to align with visitation changes after removing long-run trends.
This model is validated using a chronological holdout split (first 70% of time series for training, last 30% for testing).


## Key Findings

- BART ridership and bridge crossings consistently show positive associations with downtown visitation.
- Ferry ridership remains positive, though smaller in magnitude.
- MUNI ridership is excluded by LASSO/ElasticNet, suggesting it provides limited independent explanatory power once other regional mobility measures are included.
- Results remain directionally consistent in the log-difference growth-rate model, supporting robustness beyond the broader recovery trend.

### Outputs

This project produces:
- Elasticity coefficients for interpreting historical relationships
- Out-of-sample validation metrics (test R²)
- Predicted vs. actual visitation growth plots for the holdout period
- Coefficients used in the Downtown Visits Transit Sensitivity Simulator


## Why This Matters

This analysis helps translate transit metrics into stakeholder-relevant outcomes such as downtown activity and economic vitality. The modeling approach supports:
- transit funding and investment narratives
- regional mobility planning discussions
- downtown recovery benchmarking
- evidence-based advocacy and policy communication


