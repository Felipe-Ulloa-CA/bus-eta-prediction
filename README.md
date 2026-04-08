# Bus ETA Prediction – Santiago, Chile

## Project Overview

This project develops a machine learning model to predict bus trip durations in Santiago, Chile using GTFS (General Transit Feed Specification) data.

The objective is to evaluate how much predictive performance can be achieved using engineered structural and temporal features, and to establish a strong baseline before incorporating real-time operational data.

---

## Problem Context

Bus ETA prediction is a complex spatiotemporal problem influenced by traffic conditions, operational variability, and route characteristics.

Traditional schedule-based methods often fail to capture these dynamics. This project evaluates whether machine learning models using GTFS-derived features can reduce prediction error and improve reliability.

---

## Data Sources

The analysis uses official GTFS data published by the Dirección de Transporte Público Metropolitano (DTPM), Chile.

Files used:
- `stop_times.txt` – stop-level timestamps  
- `trips.txt` – trip-level metadata  
- `routes.txt`  
- `calendar.txt`  
- `transfers.txt`  

These datasets allow reconstruction of trip durations and route structure.

---

## Methodology

The project follows the CRISP-DM framework:

1. Data Cleaning  
2. Feature Engineering  
3. Exploratory Data Analysis (EDA)  
4. Baseline Modeling  
5. Model Validation (Cross-Validation)  
6. Hyperparameter Tuning (GridSearchCV)  
7. Final Model Evaluation (Test Set)  
8. Residual Analysis  

---

## Feature Engineering

The model incorporates both structural and temporal features derived from GTFS data:

- `direction_id`  
- `is_weekend`  
- `route_trip_count`  
- `hour` (departure hour)  
- `day_of_week`  
- `number_of_stops`  
- `scheduled_duration` (proxy based on GTFS timing)  

These features significantly expand the predictive capability compared to the initial baseline.

---

## Exploratory Data Analysis (EDA)

EDA was conducted to understand patterns in trip duration:

- Distribution of trip durations  
- Trip duration by hour of day  
- Weekend vs weekday comparisons  
- Correlation analysis between features  

Key findings:
- Strong temporal patterns exist across different hours of the day  
- Trip duration varies between weekdays and weekends  
- Relationships are mostly non-linear, supporting tree-based models  

---

## Models Implemented

- Linear Regression (baseline model)  
- Random Forest Regressor  
- Tuned Random Forest (GridSearchCV)  

---

## Model Validation and Optimization

- Cross-validation was used to evaluate robustness across multiple splits  
- GridSearchCV was applied to optimize hyperparameters  

Optimal parameters:
- `n_estimators = 50`  
- `max_depth = 10`  

---

## Model Evaluation (Test Set)

The final tuned model was evaluated on a held-out test set to assess real-world performance.

Results:

- Random Forest reduces RMSE by approximately **15–16%** compared to Linear Regression  
- R² ≈ **0.30**, indicating moderate explanatory power  

---

## Key Findings

- GTFS-derived structural and temporal features partially explain trip duration variability  
- Feature expansion significantly improves model performance  
- Non-linear models outperform linear models  
- Remaining error suggests missing dynamic variables (traffic, congestion, GPS)  

---

## Model Insights

- Feature importance analysis shows that temporal and duration-related features dominate  
- Residual analysis indicates underestimation in high-variability scenarios  
- The gap between cross-validation and test performance suggests mild overfitting  

---

## Limitations

- No real-time GPS data included  
- No congestion or traffic indicators  
- Model relies on static GTFS features  
- Moderate generalization performance  

These limitations define the baseline nature of the model.

---

## Future Improvements

- Integration of real-time GPS data  
- Traffic and congestion features  
- Segment-level modeling  
- Gradient Boosting / XGBoost  
- Real-time deployment (streaming pipelines, APIs)  

---

## Scalability Considerations

- Current pipeline operates on batch GTFS data  
- Can be extended to distributed processing (e.g., Spark)  
- Real-time deployment could use Kafka + model APIs  
- Feature store integration for production systems  

---

## How to Run

1. Open the notebook:  
   `bus_eta_model_calibrated.ipynb`

2. Run all cells (Google Colab recommended)

3. Required libraries:
   - pandas  
   - numpy  
   - matplotlib  
   - seaborn  
   - scikit-learn  

---

## Author

Felipe Eduardo Ulloa Orellana  
UC Berkeley Professional Certificate in Machine Learning & AI  
Silicon Valley, California  

---

## License

MIT License  
https://github.com/Felipe-Ulloa-CA/bus-eta-prediction
