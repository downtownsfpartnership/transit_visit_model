# Transit Activity and Visitor Modeling in Downtown San Francisco

This project analyzes how regional transit activity and bridge crossings influence visitor volumes in the Downtown San Francisco district. Using historical data from multiple transportation agencies and visitor analytics, the goal is to identify which factors most strongly correlate with downtown visitation.

### Overview

We use statistical and machine learning approaches to model visitor counts as a function of transit ridership and bridge traffic, while accounting for seasonal variation:

- **Ordinary Least Squares (OLS)** for baseline inference.
- **Elastic Net (LASSO/Ridge)** for feature selection and regularization.


### Key Findings

- MUNI ridership was not statistically significant in the OLS model.
- LASSO regularization excluded MUNI, confirming its limited predictive power.
- Other transit modes and bridge crossings show stronger associations with visitor volumes.


### Data Sources

- **BART ridership:** Historical data from BART
- **MUNI ridership:** San Francisco Municipal Transportation Agency records
- **Ferry ridership:** Golden Gate Ferry and Bay Ferry data
- **Bridge crossings:** Bay Bridge and Golden Gate Bridge traffic counts
- **Visitor counts:** Placer.ai data for the Downtown San Francisco district


### Why It Matters

Understanding how mobility patterns affect downtown visitation can inform:
- Economic development strategies
- Transportation planning
- Marketing and event programming for urban districts


### Methods Summary

- Log-transformations applied to continuous variables for elasticity interpretation.
- Month-level dummy variables included to capture seasonality.
- Elastic Net tuned via cross-validation for optimal balance of sparsity and stability.


### Sources

- Bay Area Rapid Transit (BART)
- San Francisco Municipal Transportation Agency (MUNI)
- Golden Gate Ferry
- Bay Ferry
- California Department of Transportation (bridge traffic data)
- Placer.ai visitor analytics
