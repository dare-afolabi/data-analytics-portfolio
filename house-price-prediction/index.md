---
title: "House Price Prediction | Python | Machine Learning | Data Scientist Portfolio" 
---
[⏮️ Back to Portfolio Home](../README.md); [⬅️ Previous Project](../loan-default-risk-prediction/index.md)



# House Prices Prediction Using Machine Learning

## Overview
This project is my machine learning submission for the Kaggle competition House Prices: Advanced Regression Techniques. The objective is to predict the sale price of houses in Ames, Iowa, based on a dataset of 80 explanatory variables describing various aspects of residential homes.
The project employs advanced regression techniques, including feature engineering, ensemble modeling, and stacking, to achieve competitive performance. The final submission uses a stacked regressor ensemble, yielding a cross-validation RMSE (log scale) of approximately 0.123 and a test RMSE of 0.129.

[View Notebook](https://github.com/dare-afolabi/data-analytics-portfolio/blob/main/house-price-prediction/22092025_house_price_prediction_DA.ipynb)

- **Competition Link**: [Kaggle House Prices Competition](https://www.kaggle.com/competitions/house-prices-advanced-regression-techniques)
- **Author**: Dare Afolabi ([Kaggle Profile](https://www.kaggle.com/dafolabi))
- **Submission Date**: September 24, 2025
- **Submission Count**: 1

## Dataset
The dataset consists of two CSV files:
- **train.csv**: 1,460 training samples with 81 features (including the target SalePrice).
- **test.csv**: 1,460 test samples with 80 features (excluding SalePrice).

## Approach
The workflow follows a structured pipeline:
	
1 **Data Loading and Splitting**: Load training data and split into train/validation sets (80/20) to prevent leakage.
	
2 **Exploratory Data Analysis (EDA)**:
  - Distributions of SalePrice and LogSalePrice.
  - Histograms for numeric features.
  - Bar plots for categorical features.
	
3 **Missing Value Handling**:
  - Numeric: Median imputation by neighborhood for LotFrontage;
  - Zero-fill for other numeric columns like MasVnrArea.
  - Categorical: Prefix with “No_” (e.g., “No_Alley”).
	
4 **Feature Engineering**:
  - Derived features: Total square footage (TotalSF), age (Age), bathrooms (Bathrooms), porch area (PorchArea).
  - Interactions: Quality-Size (QualSize), Quality-Condition (QualCond).
  - Encodings: Ordinal mapping for quality ratings; frequency encoding for high-cardinality nominals.
  - Location: Neighborhood median price mapping; urban/suburban/rural categorization.
	
5 **Feature Transformation**:
  - Log1p transformation for skewed numerics to stabilize variance.
	
6 **Categorical Encoding**:
  - One-hot encoding for remaining nominals.

7 **Modeling**:
  - Base models: RidgeCV, RandomForestRegressor, GradientBoostingRegressor.
  - Ensemble: StackingRegressor with LinearRegression as meta-learner.
  - Evaluation: 5-fold cross validation and test RMSE on log scale.
	
8 **Submission**: Predict on test set and generate CSV.

Visualizations include:
  - Target distribution (pre/post log transform).
  - Numeric histograms.
  - Categorical bar charts
  - Residual plots.
  - Feature importance bar charts.

## Models and Performance
### Base Models Evaluation
|Model              | CV RMSE    | Test RMSE |<br>
|Ridge            🥈| 0.134726   | 0.134243  |<br>
|RandomForest     🥉| 0.139180   | 0.144454  |<br>
|GradientBoosting 🥇| 0.125139   | 0.134765  |

### Stacked Ensemble
- **CV RMSE (log)**: 0.123196
- **Test RMSE (log)**: 0.128989

### Top Features (Across Models):
- QualSF (Overall Quality × Total SF)
- NeighborhoodPriceMedian
- QualSize (Overall Quality × GrLivArea)

Residual analysis indicates mild heteroscedasticity at higher prices, with Gradient Boosting showing the most stable predictions.

## Insights
- The stacked model demonstrates strong generalization, with minimal overfitting (CV and test errors closely aligned).
- Key drivers: Property quality, size, and neighborhood prestige.
- Log transformation effectively handles right-skewed SalePrice (mean: $181,442; median: $165,000).

Sample submission predictions:<br>
|Id   | SalePrice |<br>
|1461 | 118,987   |<br>
|1462 | 158,082   |

## Requirements
- Python 3.11+
- Key Libraries:
  - pandas==2.0.3
  - numpy==1.25.2
  - sklearn==1.2.2
  - scipy==1.11.2
  - matplotlib==3.9.0
  - seaborn==0.13.1

## License
This project is licensed under the MIT License - see the [LICENSE](./LICENSE) file for details.

### Author
- **Dare Afolabi**
- **Email**: [dafolabi@example.com]
- **Kaggle**: dafolabi
- **LinkedIn**: [dare-afolabi-070826383](https://www.linkedin.com/in/dare-afolabi-070826383)

Contributions and issues are welcome! Please open a pull request or issue on GitHub.
