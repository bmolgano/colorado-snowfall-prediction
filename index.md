---
title: Colorado Snowfall Prediction
---

# Colorado Snowfall Prediction

## Predicting Daily Snowfall Using NOAA Historical Weather Data and Machine Learning

This project develops and evaluates a machine learning model to predict daily snowfall across Colorado using historical observations obtained directly from the National Oceanic and Atmospheric Administration (NOAA). Weather data were collected through the NOAA National Centers for Environmental Information (NCEI) Climate Data Online API using the Global Historical Climatology Network Daily (GHCN-Daily) dataset.

The project demonstrates an end-to-end machine learning workflow, including data acquisition, exploratory data analysis, feature engineering, model development, hyperparameter tuning, and model evaluation.

---

## Project Objective

The objective of this project was to predict daily snowfall amounts reported by Colorado weather stations using historical temporal and station-level information.

The problem was formulated as a supervised machine learning regression task, where the target variable was daily snowfall (`SNOW`) measured in millimeters.

---

## Dataset Summary

The final modeling dataset included:

- **Study Period:** 2016–2024
- **Weather Stations:** 245 Colorado stations
- **Observations:** Approximately 747,000 daily snowfall records
- **Data Source:** NOAA Global Historical Climatology Network Daily (GHCN-Daily)

During exploratory data analysis, the dataset was found to be highly imbalanced:

- **91.6%** of observations recorded no snowfall
- **8.4%** recorded measurable snowfall

---

## Feature Engineering

Temporal features were engineered from the observation date to capture seasonal snowfall patterns, including:

- Year
- Month
- Day of Month
- Week of Year
- Day of Year
- Day of Week
- Meteorological Season

Weather station identifier was retained as a categorical predictor and encoded using One-Hot Encoding within a Scikit-learn preprocessing pipeline.

---

## Machine Learning Models

Three models were evaluated:

| Model | MAE (mm) | RMSE (mm) | R² |
|:------|---------:|----------:|---:|
| Mean Baseline | 8.61 | 24.21 | 0.0000 |
| Initial Random Forest | 7.93 | 23.52 | 0.0562 |
| **Tuned Random Forest** | **6.90** | **22.07** | **0.1691** |

The tuned Random Forest produced the strongest performance after hyperparameter optimization using **RandomizedSearchCV**.

---

## Key Findings

Feature importance analysis showed that the model relied primarily on seasonal timing and station-level information.

The most influential feature groups were:

- **Day of Year (20.8%)**
- **Weather Station (20.2%)**

The tuned Random Forest substantially improved prediction accuracy over both the baseline model and the initial Random Forest. However, calendar and station-based features alone explained only about **17%** of the variability in daily snowfall, indicating that additional meteorological variables would likely improve predictive performance.

---

## Skills Demonstrated

This project demonstrates experience with:

- Data acquisition using REST APIs
- Data cleaning and preprocessing
- Exploratory Data Analysis (EDA)
- Feature engineering
- Scikit-learn Pipelines
- Random Forest Regression
- Hyperparameter tuning with RandomizedSearchCV
- Model evaluation using MAE, RMSE, and R²
- Feature importance interpretation
- GitHub documentation and project organization

---

## Repository Contents

```text
notebooks/   Google Colab notebooks
data/        Cleaned modeling datasets
images/      EDA and model visualizations
README.md    Project documentation
index.md     GitHub Pages project site
```

---

## Future Enhancements

Future improvements to this project include:

- Incorporating meteorological predictors such as precipitation, temperature, humidity, and snow depth.
- Evaluating time-based train-test splits for forecasting future snowfall.
- Comparing Random Forest performance with Gradient Boosting, XGBoost, and LightGBM regression models.
- Deploying the trained model as an interactive web application.

---

**Author:** Betsy Molgano  
**Project:** Independent Study – Machine Learning Portfolio
