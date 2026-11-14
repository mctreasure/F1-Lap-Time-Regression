# F1-Lap-Time-Regression

# Formula 1 Lap Time Prediction Using Linear Regression

## Project Overview

This project investigates whether lap number can be used to predict lap times during a Formula 1 race. Using historical F1 lap time data, I explored patterns in racing performance, identified unusual observations, and developed linear regression models to examine the relationship between lap number and lap time.

The goal was to apply Python-based data analysis and machine learning techniques while understanding how data preparation and unusual race conditions can influence model performance.

## Tools and Technologies

- **Python:** Data analysis and modelling
- **Pandas:** Data cleaning, manipulation, and exploratory analysis
- **Matplotlib:** Data visualisation
- **Scikit-learn:** Linear regression, train/test splitting, and model evaluation
- **Jupyter Notebook:** Analysis and documentation

## Dataset

The project uses historical Formula 1 lap time data from the [Formula 1 World Championship dataset on Kaggle](https://www.kaggle.com/datasets/rohanrao/formula-1-world-championship-1950-2020).

The analysis focuses on a single race (`raceId = 354`) and uses the following variables:

| Variable | Description |
|---|---|
| `raceId` | Unique identifier for each race |
| `driverId` | Unique identifier for each driver |
| `lap` | Lap number |
| `milliseconds` | Lap time in milliseconds |
| `time_seconds` | Lap time converted to seconds |

## Methodology

### 1. Data Preparation and Exploratory Analysis

- Loaded and inspected the lap time dataset using Pandas.
- Filtered the data to a single Formula 1 race.
- Converted lap times from milliseconds to seconds.
- Examined the distribution of lap times and identified unusually slow laps.
- Removed two extreme observations exceeding 300 seconds.
- Investigated a significant increase in lap times around laps 50–55, suggesting a possible race-wide interruption.

### 2. Linear Regression Modelling

Two simple linear regression models were developed using **lap number as the independent variable** and **lap time in seconds as the dependent variable**.

- **Model 1:** Included all remaining laps after removing the two extreme observations.
- **Model 2:** Excluded laps 50–55 to investigate how the suspected race interruption influenced the results.

The data was divided into 80% training and 20% testing sets.

### 3. Model Evaluation

The models were evaluated using two metrics:

- **Mean Absolute Error (MAE):** Measures the average prediction error in seconds.
- **R² Score:** Measures how well the model explains variation in lap times relative to a baseline prediction.

## Results

| Metric | Original Model | Excluding Laps 50–55 |
|---|---:|---:|
| Regression Coefficient | +0.0298 | -0.0685 |
| MAE | 5.42 seconds | 1.95 seconds |
| R² | -0.0099 | 0.0664 |

### Key Findings

**1. Unusual observations influenced the regression results.**

The original model produced a positive regression coefficient, suggesting lap times increased throughout the race. After excluding the suspected interruption, the coefficient became negative, indicating that predicted lap times decreased as the race progressed.

**2. Prediction errors decreased after excluding the suspected interruption.**

MAE decreased from 5.42 seconds to 1.95 seconds. However, because the models were evaluated on different datasets, this improvement may partly reflect the removal of difficult-to-predict observations rather than a direct improvement in model quality.

**3. Lap number alone is a weak predictor of lap time.**

The model excluding the suspected interruption achieved an R² of approximately 0.066, explaining only 6.6% of the variation in test-set lap times.

This suggests that additional variables are needed to better capture the factors influencing Formula 1 lap times.

## Conclusion

This analysis demonstrated the importance of exploratory data analysis, data preparation, and model evaluation when applying linear regression to real-world data.

Although the models identified a relationship between lap number and lap time, their limited predictive performance suggests that a single-variable linear regression does not adequately capture the complexity of racing performance.

The project also highlighted how unusual race conditions can substantially influence regression coefficients and evaluation metrics.

## Next Steps

Future improvements will focus on:

- Incorporating **driver identity** as an additional predictor in a multiple linear regression model.
- Comparing simple and multiple regression performance using a consistent evaluation approach.
- Investigating whether additional variables improve prediction accuracy.

## Project Status

**Phase 1 — Complete:** Exploratory data analysis and simple linear regression.

**Phase 2 — Planned:** Multiple linear regression incorporating driver identity.

