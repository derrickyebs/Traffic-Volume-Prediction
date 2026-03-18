# Traffic Volume Prediction on I-94 Interstate Highway 

This is a supervised machine learning project that predicts hourly traffic volume on the I-94 interstate highway (Minneapolis–St Paul, MN) using weather conditions, time of day, and other calendar features.

## Project Overview

Traffic volume prediction is a core problem in transportation engineering. Accurate forecasts allow highway authorities to make informed decisions on signal timing, maintenance scheduling, and road capacity planning. This project applies linear regression to 6 years of hourly traffic data collected by the Minnesota Department of Transportation (MnDOT) from 2012 to 2018 to build a model that predicts how many vehicles will use the highway in any given hour.


## Dataset

**Source:** [Metro Interstate Traffic Volume – Kaggle](https://www.kaggle.com/datasets/anshtanwar/metro-interstate-traffic-volume)
- **Features:** Weather conditions, temperature, holiday status, date and time
- **Target:** `traffic_volume` — hourly vehicle count on I-94


## Methodology

### 1. Exploratory Data Analysis
- Identified clear AM and PM peak traffic patterns
- Confirmed weekday traffic is significantly higher than weekends


### 2. Feature Engineering
The following features were engineered from the raw data:

| Feature | Description |
|---|---|
| `hour` | Hour of day (0–23) |
| `hour_squared` | Polynomial term to capture non-linear time patterns |
| `month` | Month of year |
| `is_rush_hour` | 1 if AM peak (7–9am) or PM peak (4–6pm) |
| `is_weekend` | 1 if Saturday or Sunday |
| `is_holiday` | 1 if US public holiday |
| `temp_celsius` | Temperature converted from Kelvin to Celsius |
| `clouds_all` | Cloud coverage percentage |
| `rain_1h` | Rainfall in mm per hour |
| `snow_1h` | Snowfall in mm per hour |

### 3. Model Training
- Algorithm: Linear Regression (scikitlearn)
- Train/test split: 80/20
- Feature scaling: StandardScaler

### 4. Results

| Metric | Baseline Model | Final Model |
|---|---|---|
| R² Score | 0.36 | 0.73 |
| RMSE | 1590 vehicles/hr | 1030 vehicles/hr |
| MAE | 1373 vehicles/hr | 798 vehicles/hr |

Adding `hour_squared` as a polynomial feature improved R² from 0.36 to 0.73. The model now explains 73% of the variation in hourly traffic volume.



## Key Findings

- Time of day is the strongest predictor of traffic volume
- Rush hour traffic is significantly busier than off-peak hours
- Weekend traffic is notably lower than weekday traffic
- Weather conditions have a secondary but measurable effect on volume
- The model predicts negative volumes for 5.7% of test cases, predominantly during low-traffic night hours.


## Engineering Application

The trained model can predict traffic volume for any combination of input conditions. For example:

- **8am, rainy weekday, January, 2°C** → 4,934 vehicles/hour

These predictions have direct applications in:
- Road capacity and Level-of-Service (LOS) assessment
- Maintenance window scheduling
- Traffic signal timing


## Limitations and Future Work

- The model produces negative predictions for low-traffic hours. A constraint-based model could probably address this
- Non-linear models would likely improve accuracy further
- Adding more features like incident data, school schedules, and local events could reduce residual patterns


## Tools and Libraries

- Python, Pandas, NumPy
- Scikit-learn
- Matplotlib, Seaborn
- Jupyter Notebook

## Author

- **Yeboah Derrick Duah**
- derrickyebs@gmail.com
- March 2026



