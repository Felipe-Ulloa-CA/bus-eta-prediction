# Bus ETA Prediction – Santiago, Chile

## Project Overview

This project develops a machine learning baseline model to predict bus trip durations in Santiago, Chile using structural GTFS data.

The objective is to evaluate whether supervised learning models can reduce prediction error compared to traditional schedule-based estimation methods.

---

## Data Sources

The analysis uses official GTFS data published by the Dirección de Transporte Público Metropolitano (DTPM), Chile.

Files used:
- stop_times.txt
- trips.txt
- routes.txt
- calendar.txt
- transfers.txt

These files allow reconstruction of trip durations and structural route characteristics.

---

## Methodology

The project follows a CRISP-DM framework:

1. Data Cleaning
2. Outlier Removal
3. Feature Engineering
4. Baseline Modeling
5. Residual Analysis

### Features Used

- direction_id
- is_weekend
- route_trip_count

---

## Models Implemented

- Linear Regression
- Random Forest Regressor

---

## Results

| Model | MAE (sec) | RMSE (sec) |
|-------|-----------|------------|
| Linear Regression | 1480.75 | 1831.71 |
| Random Forest | 1209.44 | 1540.75 |

Random Forest achieved:

- 16% reduction in RMSE compared to Linear Regression
- R² = 0.308 (explains 30.8% of variance)

---

## Key Findings

- Structural GTFS features partially explain trip duration variability.
- Significant unexplained variance suggests dynamic operational variables (e.g., congestion, peak-hour effects) are required for higher precision ETA prediction.
- This establishes a strong structural baseline for future real-time modeling.

---

## Future Improvements

- Integration of real-time GPS data
- Peak-hour feature engineering
- Segment-level modeling
- Cross-validation and hyperparameter tuning
- Model monitoring for production deployment

---

## How to Run

1. Open `bus_eta_model.ipynb`
2. Run all cells (Colab recommended)
3. Ensure required Python libraries are installed:
   - pandas
   - numpy
   - seaborn
   - matplotlib
   - scikit-learn

---

## Author

Felipe Eduardo Ulloa Orellana  
UC Berkeley Professional Certificate in Machine Learning & AI  
Silicon Valley, California  

---

## License

MIT License
