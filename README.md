# Sales & Demand Forecasting for Businesses

**Future Interns — Machine Learning Internship | Task 1 | 2026**  
Ritigya Mishra

---

## What this project does

This project explores retail sales forecasting using historical Superstore data. The dataset contains 9,800 transactions across Technology, Furniture, and Office Supplies, covering four US regions from 2015 to 2018.

The notebook covers exploratory analysis, time-based feature engineering, model comparisons, and a six-month forecast.

## Dataset

The analysis uses the Superstore sales dataset, with 9,800 transactions and 18 columns. The target variable is `Sales` (USD). Records span January 2015 to December 2018.

## Methodology

### Exploratory analysis

The analysis examines monthly sales trends, rolling averages, and sales by category, region, and quarter. A year-by-month heatmap is used to inspect seasonal patterns.

### Preprocessing

Order and shipment dates are parsed as dates, duplicates and missing values are handled, and records are sorted chronologically. The modelling workflow uses a time-based 80/20 train-test split rather than a random split.

### Feature engineering

Features include Year, Month, Quarter, DayOfWeek, WeekOfYear, DayOfYear, IsWeekend, ShipDays, rolling means, and lag values.

### Models

The notebook compares:

- Linear Regression
- Random Forest Regressor
- Gradient Boosting Regressor
- Simple, Weighted, and Exponential Moving Averages

## Results

### Model comparison

| Model | MAE | RMSE | R² |
|---|---:|---:|---:|
| Linear Regression | $262.60 | $589.88 | 0.0022 |
| Random Forest | $249.43 | $557.71 | 0.1080 |
| Gradient Boosting | $217.15 | $529.81 | 0.1951 |
| EMA (time series) | $9,140.23 | $11,756.47 | — |

Gradient Boosting had the lowest MAE and RMSE among the regression models in this comparison. Its R² of 0.1951 indicates that substantial variation remains unexplained; the result should not be interpreted as a highly accurate forecasting system.

The notebook also contains a six-month forecast for January to June 2019. That forecast is generated separately using a Linear Regression model on monthly aggregated data, with lag and rolling-average features.

## Selected Findings

- November has the highest sales in the historical period.
- Technology is the largest revenue-generating category in the dataset.
- The West region contributes the largest regional share.
- Q4 is the strongest quarter in the historical data.

These findings describe this dataset and should not be assumed to generalize to other retailers.

## Visualisations

The repository includes:

- `eda_overview.png`
- `sales_heatmap.png`
- `model_comparison.png`
- `actual_vs_predicted.png`
- `feature_importance.png`
- `sales_forecast.png`
- `timeseries_moving_averages.png`

## Run the Notebook

```bash
git clone https://github.com/ritigyam2/Retail-Demand-Prediction.git
cd Retail-Demand-Prediction

python -m pip install pandas numpy scikit-learn matplotlib seaborn jupyter
jupyter notebook "Retail Demand Prediction Model.ipynb"
```

## Technologies

- Python
- pandas and NumPy
- scikit-learn
- Matplotlib and Seaborn
- Jupyter Notebook

## Internship Context

Completed as Task 1 of the Future Interns Machine Learning Internship programme (24 April – 24 May 2026).
