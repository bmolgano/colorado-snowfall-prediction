---
title: Colorado Snowfall Prediction
---

# Colorado Snowfall Prediction

## Using NOAA Historical Weather Data and Machine Learning

This project examines whether historical weather observations can be used to predict daily snowfall across Colorado.

The project uses the NOAA Global Historical Climatology Network Daily dataset, accessed through the NOAA Climate Data Online API.

## Project Goal

The goal is to develop and evaluate a supervised regression model that predicts daily snowfall amounts reported by Colorado weather stations.

## Data Collection

The initial analysis identified:

- 307,526 Colorado snowfall observations in 2024
- 1,433 reporting stations
- 382 stations with at least 300 snowfall observations during 2024

Historical snowfall data are being collected for these stations from 2016 through 2025.

## Project Workflow

1. API connection and data retrieval
2. Initial exploratory data analysis
3. Weather-station coverage evaluation
4. Historical data collection
5. Data cleaning and feature engineering
6. Regression model development
7. Model evaluation
8. Results and visualizations

## Current Status

Historical NOAA snowfall data collection is in progress.

## Project Notebook

The full project notebook is available in the `notebooks` folder of this repository.
