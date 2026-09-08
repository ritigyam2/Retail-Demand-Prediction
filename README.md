# Sales & Demand Forecasting for Businesses

**Future Interns — Machine Learning Internship | Task 1 | 2026**
Ritigya Mishra

---

## What this project does

This is an end-to-end machine learning pipeline for forecasting future retail sales using historical Superstore data. The dataset contains 9,800 real-world transactions from a US-based Superstore spanning four years (2015–2018), covering Technology, Furniture, and Office Supplies across four US regions. Total revenue across the dataset is $2,261,536.78.

The pipeline covers exploratory data analysis, time-based feature engineering, model training and evaluation, time-series analysis, and a 6-month forward sales forecast with business-ready insights.

**Core question:** How can we accurately forecast future retail sales, identify the key business drivers behind demand, and deliver actionable insights to support real-world decision-making?

---

## Dataset

The Superstore Sales Dataset from [Kaggle](https://www.kaggle.com/) — 9,800 transactions across 18 columns. The target variable is `Sales` (in USD), with records spanning January 2015 to December 2018 across three product categories (Technology, Furniture, Office Supplies) and four regions (West, East, Central, South).

---

## Methodology

### 1. Exploratory Data Analysis

Analysed monthly sales trends with 3-month and 6-month rolling averages. Broke down sales by category, region, and quarter across all four years. Built a Year × Month heatmap to surface seasonal patterns — November consistently stood out as the peak sales month, driven by holiday demand.

### 2. Data Preprocessing

Parsed `Order Date` and `Ship Date` to datetime format, removed duplicates, handled missing values, and sorted data chronologically to preserve time-series integrity. Applied a time-based 80/20 train-test split (not random) to avoid data leakage.

### 3. Feature Engineering

Built a set of time-based features to give the models seasonal and trend context:

- Core temporal identifiers: Year, Month, Quarter
- Weekly seasonality: DayOfWeek, WeekOfYear
- Fine-grained patterns: DayOfYear, IsWeekend
- Operational: ShipDays (days between order and shipment)
- Trend signals: Rolling Mean (3M and 6M), Lag features (1M and 3M)

### 4. Models Trained

Compared both ML regressors and classical time-series methods:

- **Linear Regression** — baseline
- **Random Forest Regressor** — ensemble tree-based
- **Gradient Boosting Regressor** — boosted tree (selected as final model)
- **Simple Moving Average (SMA)**, **Weighted Moving Average (WMA)**, **Exponential Moving Average (EMA)** — classical time-series baselines

### 5. Evaluation

Used three metrics across all models: MAE (Mean Absolute Error), RMSE (Root Mean Squared Error), and R² (Coefficient of Determination).

---

## Results

### Model comparison

| Model | MAE | RMSE | R² |
|---|---|---|---|
| Linear Regression | $262.60 | $589.88 | 0.0022 |
| Random Forest | $249.43 | $557.71 | 0.1080 |
| Gradient Boosting | $217.15 | $529.81 | 0.1951 |
| EMA (Time-Series) | $9,140.23 | $11,756.47 | — |

Gradient Boosting was selected as the final model — lowest MAE, lowest RMSE, and highest R² across all models tested.

### Feature importance (Random Forest)

The top five features by importance score: DayOfYear (0.206), Sub-Category (0.185), WeekOfYear (0.121), Region (0.111), and ShipDays (0.091). Temporal features dominate, confirming that seasonality is a strong driver of sales variation.

### 6-month sales forecast (2019)

| Month | Forecasted Sales |
|---|---|
| January 2019 | $67,028.05 |
| February 2019 | $76,328.21 |
| March 2019 | $66,562.70 |
| April 2019 | $70,026.29 |
| May 2019 | $72,215.26 |
| June 2019 | $70,556.29 |

Average monthly forecast: ~$70,452 — consistent with late 2018 sales trends. The forecast was generated using a Linear Regression model trained on monthly aggregated data with lag features and rolling averages as inputs, visualised with a ±15% confidence band.

---

## Key findings

1. Gradient Boosting outperformed all models including traditional time-series methods.
2. DayOfYear and Sub-Category are the strongest predictors of sales value.
3. November is consistently the highest sales month across all four years — driven by holiday demand.
4. Technology is the top revenue-generating category at $827,456 total.
5. The West region leads all regions, contributing 31.4% of total sales.
6. Q4 is the strongest quarter every year — a clear seasonal pattern.
7. Sales show a strong year-over-year upward trend from 2015 to 2018.

---

## Business snapshot

| Metric | Value |
|---|---|
| Total Revenue | $2,261,536.78 |
| Avg Monthly Sales | $47,115.35 |
| Best Month | November 2018 — $117,938.15 |
| Worst Month | February 2015 — $4,519.89 |
| Top Category | Technology |
| Top Region | West |
| Top Segment | Consumer |

---

## Visualisations

The notebook generates seven saved charts, all included in the repo:

- `eda_overview.png` — monthly trend, category breakdown, quarterly and regional charts
- `sales_heatmap.png` — Year × Month heatmap showing seasonal patterns
- `model_comparison.png` — MAE, RMSE, and R² comparison across all models
- `actual_vs_predicted.png` — Gradient Boosting actual vs predicted scatter
- `feature_importance.png` — top 13 features ranked by importance score
- `sales_forecast.png` — 6-month forecast with ±15% confidence band
- `timeseries_moving_averages.png` — SMA vs WMA vs EMA comparison

---

## How to run

```bash
git clone https://github.com/ritigyam2/Retail-Demand-Prediction.git

pip install pandas numpy scikit-learn matplotlib seaborn

jupyter notebook "FUTURE_ML_01(Sales & Demand Forecasting for Businesses).ipynb"
```

---

## Tech stack

**Language:** Python
**ML:** scikit-learn (Linear Regression, Random Forest, Gradient Boosting)
**Data processing:** pandas, NumPy
**Visualisation:** matplotlib, seaborn

---

## Internship context

Completed as Task 1 of the Future Interns Machine Learning Internship programme (24 April – 24 May 2026).

---

**Author:** Ritigya Mishra
