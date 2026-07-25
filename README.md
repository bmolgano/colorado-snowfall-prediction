# colorado-snowfall-prediction
Machine learning project using NOAA historical weather data to predict daily snowfall in Colorado.

Website URL - https://bmolgano.github.io/colorado-snowfall-prediction/

# Colorado Snowfall Prediction

## Project Overview

This project uses historical weather observations from the National Oceanic and Atmospheric Administration to develop a machine learning model for predicting daily snowfall in Colorado.

The data are obtained through the NOAA National Centers for Environmental Information Climate Data Online API using the Global Historical Climatology Network Daily dataset.

## Project Objective

The primary objective is to predict daily snowfall amounts reported by Colorado weather stations using historical weather observations and time-based features.

This is a supervised machine learning regression problem because the prediction target, daily snowfall, is numeric.

## Data Source

- Source: NOAA National Centers for Environmental Information
- Dataset: Global Historical Climatology Network Daily
- Geographic area: Colorado
- Historical period: 2016–2025
- Target variable: Daily snowfall (`SNOW`)

## Initial Data Evaluation

An initial 2024 snowfall dataset contained:

- 307,526 snowfall observations
- 1,433 Colorado weather stations
- 382 stations with at least 300 reported observations during 2024

The 382 stations meeting the reporting threshold were selected for historical data collection.

## Methodology

The project includes the following stages:

1. Connect to the NOAA Climate Data Online API.
2. Retrieve and evaluate Colorado weather observations.
3. Select stations with sufficient reporting coverage.
4. Retrieve historical snowfall data from 2016 through 2025.
5. Conduct exploratory data analysis.
6. Clean and prepare the modeling dataset.
7. Engineer weather and time-based predictor variables.
8. Train and compare regression models.
9. Evaluate model performance.
10. Present findings and visualizations.

## Repository Structure

```text
notebooks/   Google Colab notebooks
images/      Project charts and visualizations
README.md    Project overview and documentation
index.md     GitHub Pages project website
