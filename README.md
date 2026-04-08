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

The model incorporates structural and temporal features derived from GTFS data:

- `direction_id`  
- `is_weekend`  
- `route_trip_count`  
- `day_of_week`  
- `number_of_stops`  

These features expand the predictive capability compared to the initial baseline (3 → 5 features).

---

## Exploratory Data Analysis (EDA)

EDA was conducted to understand patterns in trip duration:

- Distribution of trip durations  
- Weekend vs weekday comparisons  
- Correlation analysis between features  

Key findings:

- Trip duration varies between weekdays and weekends  
- Strong relationship exists between number of stops and trip duration  
- Relationships are non-linear, supporting tree-based models  

---

## Models Implemented

- Linear Regression (baseline model)  
- Random Forest Regressor  
- Tuned Random Forest (GridSearchCV)  

---

## Model Validation and Optimization

- Cross-validation was used to evaluate robustness  
- GridSearchCV was applied for hyperparameter tuning  

Optimal parameters:

- `n_estimators = 50`  
- `max_depth = 5`  

---

## Model Evaluation (Test Set)

The final tuned model was evaluated on a held-out test set to assess real-world performance.

Results:

- Linear Regression RMSE ≈ 385  
- Random Forest RMSE ≈ 211  
- Tuned Random Forest RMSE ≈ 164  

- RMSE improvement ≈ **57%** over Linear Regression  
- R² ≈ **0.97**, indicating strong predictive performance  

---

## Key Findings

- Feature expansion significantly improves model performance  
- Non-linear models outperform linear models  
- Structural GTFS features can explain a large portion of trip duration variability  
- Number of stops is a key driver of travel time  

---

## Model Insights

- Feature importance analysis highlights structural variables as dominant predictors  
- Residual analysis shows remaining variability in complex scenarios  
- The gap between cross-validation and test performance suggests mild overfitting  

The strong model performance may be influenced by the structured nature of GTFS data, which captures consistent relationships between operational variables and trip duration.

---

## Limitations

- No real-time GPS data included  
- No traffic or congestion indicators  
- Model relies on static GTFS features  
- Performance may be optimistic due to structured data  

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
