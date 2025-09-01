# PJME Energy Forecasting Notebooks

This repository contains three Jupyter notebooks that demonstrate different approaches to time series forecasting for energy consumption using the PJME (PJM Interconnection) hourly electricity demand dataset.

## Dataset

The notebooks work with `PJME_hourly.csv`, which contains hourly electricity consumption data from the PJM Interconnection, one of the largest regional transmission organizations (RTOs) in North America. The dataset includes:

- **Datetime**: Hourly timestamps
- **PJME_MW**: Energy consumption in megawatts (MW)

## Notebooks Overview

### 1. `PJMEmw_manipulation.ipynb` - Basic Energy Forecasting

This introductory notebook covers:
- **Data Loading & Exploration**: Basic data inspection and statistical analysis
- **Data Visualization**: Time series plots and boxplots showing energy usage patterns by hour, month, and year
- **Feature Engineering**: Creation of temporal features (Hour, DayOfWeek, Month, Quarter, Year, DayOfYear)
- **Machine Learning Models**:
  - XGBoost Regressor
  - Random Forest Regressor  
  - Linear Regression
- **Model Evaluation**: Comparison using MSE, RMSE, MAE, MAPE, and R² metrics
- **Visualization**: Actual vs predicted energy usage plots for each model

**Key Learning**: Introduction to time series forecasting with traditional ML algorithms.

### 2. `PJME_hourly_week2.ipynb` - Advanced Time Series Modeling

This intermediate notebook introduces more sophisticated techniques:
- **Data Cleaning**: Outlier detection and removal (values < 19,000 MW)
- **Advanced Feature Engineering**: 
  - Extended temporal features (week of year, day of month)
  - Lag features (1-year, 2-year, 3-year historical values)
- **Time Series Cross-Validation**: Using `TimeSeriesSplit` with 5 folds
- **Hyperparameter Optimization**: GridSearchCV for XGBoost parameter tuning
- **Future Predictions**: Forecasting energy consumption from 2018-2021
- **Feature Importance Analysis**: Understanding which features contribute most to predictions

**Key Learning**: Advanced time series techniques including proper cross-validation and lag features.

### 3. `PJME_hourly_week3.ipynb` - Prophet vs XGBoost Comparison

This advanced notebook compares different forecasting approaches:
- **Facebook Prophet**: A specialized time series forecasting tool
  - Automatic seasonality detection
  - Holiday integration using US holidays
  - Component decomposition (trend, seasonality, holidays)
- **XGBoost Comparison**: Direct comparison with traditional ML approach
- **Holiday Effects**: Analysis of how holidays impact energy consumption
- **Performance Metrics**: Comprehensive comparison using RMSE, MAE, and MAPE
- **Visualization**: Side-by-side comparison of actual vs predicted values
- **Future Forecasting**: Extended predictions through 2020

**Key Learning**: Specialized time series tools vs traditional ML, and the importance of domain knowledge (holidays) in forecasting.

## Requirements

```python
# Core libraries
pandas
numpy
matplotlib
seaborn
scikit-learn

# Machine Learning
xgboost

# Time Series Forecasting
prophet

# Additional utilities
plotly
holidays
```

## Installation

```bash
pip install pandas numpy matplotlib seaborn scikit-learn xgboost prophet plotly holidays
```

## Usage

1. **Download the PJME dataset** (`PJME_hourly.csv`)
2. **Start with Notebook 1** for basic understanding
3. **Progress through Notebooks 2 and 3** for advanced techniques
4. **Modify paths** if running in different environments (Google Colab paths are included)

## Key Findings

### Model Performance Comparison
- **XGBoost**: Generally provides the best accuracy with proper feature engineering
- **Prophet**: Excellent for interpretability and automatic seasonality detection
- **Random Forest**: Good baseline performance
- **Linear Regression**: Simple but limited for complex time series patterns

### Important Features
1. **Hour of day**: Strong daily seasonality in energy consumption
2. **Day of week**: Different patterns for weekdays vs weekends  
3. **Month/Season**: Seasonal variations due to heating/cooling demands
4. **Lag features**: Historical values are strong predictors
5. **Holidays**: Significant impact on energy consumption patterns

### Best Practices Demonstrated
- Proper time series train/test splits (temporal ordering)
- Time series cross-validation techniques
- Feature engineering for temporal data
- Handling outliers in energy data
- Integration of domain knowledge (holidays)
- Model comparison and evaluation

## File Structure

```
├── PJMEmw_manipulation.ipynb          # Basic forecasting notebook
├── PJME_hourly_week2.ipynb           # Advanced XGBoost with cross-validation
├── PJME_hourly_week3.ipynb           # Prophet vs XGBoost comparison
├── PJME_hourly.csv                # Dataset (not included)
└── README.md                      # This file
```

## Educational Value

These notebooks provide a comprehensive learning path for time series forecasting:

1. **Beginner**: Learn basic ML approaches to time series (Notebook 1)
2. **Intermediate**: Understand proper time series validation and advanced features (Notebook 2)  
3. **Advanced**: Compare specialized time series tools with traditional ML (Notebook 3)

Each notebook builds upon the previous one, introducing new concepts while reinforcing fundamental time series forecasting principles.

## Notes

- Original notebooks were created in Google Colab (evident from drive mounting code)
- Some French comments are present in the original code
- The notebooks demonstrate both theoretical concepts and practical implementation
- Results show the importance of proper feature engineering in time series forecasting
