# colorado-snowfall-prediction
Machine learning project using NOAA historical weather data to predict daily snowfall in Colorado.

Website URL - https://bmolgano.github.io/colorado-snowfall-prediction/

# Colorado Snowfall Prediction

## Project Overview

This project uses historical weather observations from the National Oceanic and Atmospheric Administration (NOAA) to develop a machine learning model for predicting daily snowfall across Colorado.

Weather observations were obtained directly through the NOAA National Centers for Environmental Information (NCEI) Climate Data Online API using the Global Historical Climatology Network Daily (GHCN-Daily) dataset. The project demonstrates an end-to-end machine learning workflow, including API-based data acquisition, data cleaning, exploratory data analysis, feature engineering, model development, hyperparameter tuning, and performance evaluation.

## Project Objective

The objective of this project is to predict daily snowfall amounts reported by Colorado weather stations using historical temporal and station-level information.

The project is formulated as a supervised machine learning regression problem because the prediction target, daily snowfall (`SNOW`), is a continuous numeric variable.

## Data Source

- **Source:** NOAA National Centers for Environmental Information (NCEI)
- **Dataset:** Global Historical Climatology Network Daily (GHCN-Daily)
- **Access Method:** NOAA Climate Data Online API
- **Geographic Area:** Colorado
- **Study Period:** 2016–2024
- **Final Weather Stations:** 245
- **Final Observations:** Approximately 747,000
- **Target Variable:** Daily snowfall (`SNOW`), measured in millimeters

## Data Preparation

An initial evaluation of 2024 snowfall observations identified 1,433 Colorado weather stations. Stations were evaluated based on reporting frequency to avoid selecting locations with high snowfall totals but incomplete observations.

A minimum threshold of 300 snowfall observations during 2024 was established, resulting in 382 candidate stations for historical data collection. Historical reporting coverage was then evaluated across the full study period, and stations with insufficient coverage were removed.

The final modeling dataset contained approximately 747,000 daily snowfall observations from 245 Colorado weather stations covering 2016 through 2024.

## Exploratory Data Analysis

Exploratory analysis identified several important characteristics of the snowfall dataset:

- Snowfall demonstrated strong seasonal patterns across Colorado.
- Snowfall totals varied substantially among weather stations.
- Positive snowfall amounts were strongly right-skewed, with smaller snowfall events occurring more frequently than extreme events.
- Approximately 91.6% of observations recorded no snowfall.
- Approximately 8.4% of observations recorded measurable snowfall.

These findings demonstrated that snowfall prediction is affected by both seasonal timing and station-level differences while also presenting a highly imbalanced target distribution.

## Feature Engineering

Temporal features were derived from each observation date to represent seasonal snowfall patterns. Engineered features included:

- Year
- Month
- Day of month
- Week of year
- Day of year
- Day of week
- Meteorological season

Weather station identifier was retained as a categorical predictor to capture station-level differences in snowfall.

Categorical variables were transformed using One-Hot Encoding through a Scikit-learn preprocessing pipeline, while numeric variables were passed directly to the model.

## Machine Learning Model

A Random Forest Regressor was selected as the primary machine learning algorithm because of its ability to capture nonlinear relationships and interactions among temporal and station-level features.

The modeling process included three stages:

1. Mean prediction baseline
2. Initial Random Forest model
3. Hyperparameter-tuned Random Forest model

Because of the size of the dataset, a random sample of 100,000 observations from the training data was used for Random Forest model development and hyperparameter tuning.

Hyperparameter optimization was performed using `RandomizedSearchCV` with three-fold cross-validation.

### Best Random Forest Parameters

- **Number of Trees:** 25
- **Maximum Depth:** None
- **Minimum Samples Split:** 10
- **Minimum Samples Leaf:** 2
- **Maximum Features:** Square root

## Model Performance

| Model | MAE (mm) | RMSE (mm) | R² |
|---|---:|---:|---:|
| Mean Baseline | 8.61 | 24.21 | 0.0000 |
| Initial Random Forest | 7.93 | 23.52 | 0.0562 |
| **Tuned Random Forest** | **6.90** | **22.07** | **0.1691** |

The tuned Random Forest produced the strongest performance, reducing Mean Absolute Error from 7.93 mm to 6.90 mm and increasing R² from 0.0562 to 0.1691 compared with the initial Random Forest.

## Feature Importance

Feature importance analysis showed that the model relied primarily on seasonal timing and station-level information.

The two most influential feature groups were:

- **Day of Year:** 20.8%
- **Weather Station:** 20.2%

Week of year, month, day of month, season, and year also contributed to model predictions. These findings indicate that the Random Forest primarily learned seasonal and geographic patterns within Colorado's historical snowfall observations.

## Key Findings

The tuned Random Forest substantially outperformed both the mean baseline and initial Random Forest models. Hyperparameter tuning reduced prediction error and increased the amount of variation in snowfall explained by the model.

However, the final R² of 0.1691 indicates that much of the variability in individual daily snowfall events remains unexplained. The current model primarily captures broad seasonal and station-level patterns rather than the atmospheric conditions responsible for individual snowfall events.

Future work could incorporate meteorological predictors such as precipitation and temperature, evaluate chronological train-test splitting, and compare Random Forest performance with additional regression algorithms.

## Repository Structure

```text
notebooks/   Google Colab notebooks and machine learning analysis
data/        Cleaned project datasets
images/      EDA and model visualizations
README.md    Project overview and results
index.md     GitHub Pages project website
