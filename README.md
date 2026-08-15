# python
Revenue Forecasting Using Time-Series Analysis

**A Python data-cleaning and forecasting-readiness pipeline that transforms raw, inconsistent revenue records into an analysis-ready time series dataset for ARIMA/SARIMA forecasting.**

Overview

This project builds a **time-series forecasting pipeline** for daily revenue data. Organizations often rely on manual estimation and gut-feel assumptions to forecast revenue — this project replaces that with a structured, data-driven approach: clean historical revenue data, engineer time-based features, and (in the forecasting phase) apply **ARIMA/SARIMA models** to generate reliable, scalable revenue predictions.

This repository currently documents the **data acquisition and data cleaning phase** — the foundational step that makes accurate forecasting possible — using a real-world-style messy dataset with duplicates, typos, nulls, and inconsistent formatting.

Business Problem

Previous forecasting approaches at the organization suffered from:

- Heavy dependence on manual estimation and assumptions
- Failure to capture trends and seasonal variation in historical revenue
- Poor accuracy in financial planning and resource allocation
- Increased uncertainty in business decision-making

The business needs an analytical model that uses **historical revenue data** to generate forecasts that are both reliable and scalable.

Objective

Develop a time-series forecasting model that accurately predicts future revenue using historical data:

- Analyze historical revenue data to identify trends, seasonality, and patterns
- Clean and prepare raw data for time-series analysis
- Apply forecasting techniques such as **ARIMA / SARIMA** and trend-based models
- Evaluate forecasting accuracy using performance metrics
- Create visual dashboards/reports to make forecasting results easy to interpret
- Provide actionable insights to support strategic decision-making

**Expected outcome:** improved forecast accuracy → better budgeting, resource allocation, and more confident strategic planning around investment, staffing, and marketing.

Dataset

| Detail | Raw Dataset | Cleaned Dataset |
|---|---|---|
| **File** | `revenue_raw_uncleaned.csv` | `revenue_cleaned.csv` |
| **Rows** | 2,050 | 2,000 |
| **Columns** | 9 | 13 (5 new time-based features added) |
| **Date Range** | Inconsistent formats (e.g. `14-12-2023`) | Standardized `YYYY-MM-DD` (2019-01-01 → 2024-06-22) |

**Core columns:** `Date`, `Revenue`, `Region`, `Product_Category`, `Units_Sold`, `Discount_Pct`, `Sales_Rep`, `Month`, `Year`

**Engineered columns (post-cleaning):** `Month_Name`, `Quarter`, `Week`, `Day_Of_Week`

**Regions covered:** Central, East, North, South, West
**Product categories:** Clothing, Electronics, Food, Services, Software

Data Cleaning Process

The raw dataset had duplicate rows, inconsistent date formats, negative/null revenue values, outliers, and inconsistent text casing across categorical fields. The cleaning pipeline (built in Python/Pandas) followed these steps:

1. **Remove duplicate rows** — deleted repeated/unwanted records
2. **Standardize date format** — unified all dates into a single consistent format
3. **Sort chronologically** — ordered records by date for time-series integrity
4. **Clean Revenue** — removed negative values and nulls
5. **Handle outliers** — applied IQR-based outlier capping and estimated missing values appropriately for a time series
6. **Clean Region** — corrected typos and standardized to title case
7. **Clean Product Category** — fixed typos and standardized casing
8. **Clean Units Sold** — converted to numeric type, fixed negative values, filled nulls with the median
9. **Clean Sales Rep** — corrected spacing between first/last names, standardized to title case, filled nulls
10. **Rebuild date features** — derived `Year`, `Month`, `Quarter`, `Week`, and `Day_Of_Week` from the cleaned date column

Before vs After Cleaning

| Issue | Before | After |
|---|---|---|
| Duplicate/invalid rows | 2,050 rows | 2,000 rows |
| Missing Revenue values | 99 nulls | Handled (nulls removed/imputed) |
| Missing Region/Category/Sales Rep | 35–36 nulls each | Standardized & filled |
| Units_Sold data type | Mixed text (`"unknown"`, numeric strings) | Clean numeric (`float`) |
| Date format | Multiple formats (`DD-MM-YYYY`, inconsistent) | Uniform `YYYY-MM-DD`, chronologically sorted |
| Time-based features | None | `Month_Name`, `Quarter`, `Week`, `Day_Of_Week` added |

Tools & Technologies

- **Python** — core scripting language
- **Pandas / NumPy** — data cleaning, transformation, feature engineering
- **Matplotlib / Seaborn** *(planned for EDA & forecast visualization)*
- **Statsmodels (ARIMA / SARIMA)** *(planned for the forecasting phase)*

Project Workflow

1. **Problem Definition** — Documented business problem, objectives, and expected outcomes (`Problem_Statement.docx`)
2. **Data Collection** — Sourced raw daily revenue transaction data
3. **Data Cleaning** — Applied a 10-step cleaning pipeline in Python/Pandas (`Data_Cleaning_Steps.docx`)
4. **Feature Engineering** — Derived time-based features (Quarter, Week, Day of Week) to support seasonality analysis
5. **Exploratory Data Analysis** *(next phase)* — Trend and seasonality visualization
6. **Model Building** *(next phase)* — ARIMA/SARIMA forecasting models
7. **Evaluation** *(next phase)* — Accuracy metrics (MAE, RMSE, MAPE)
8. **Reporting** *(next phase)* — Forecast visualization dashboard and business insights

Current Status & Next Steps

**✅ Completed:** Problem definition, data collection, and full data-cleaning pipeline.

In progress:**
- Exploratory Data Analysis (trend, seasonality, region/category revenue patterns)
- ARIMA/SARIMA model building and tuning
- Forecast accuracy evaluation (MAE, RMSE, MAPE)
- Final forecasting dashboard/report

*This repository will be updated as each phase is completed — check back for the modeling notebook and forecast visualizations.*

Author

**Kamatchi Keerthika**
Data Analyst | SQL • Excel • Power BI • Tableau • Python
📍 Chennai, India

*This project is part of a self-directed data analytics portfolio built to demonstrate end-to-end data handling — from messy real-world data to forecasting-ready datasets.*

---

⭐ If you found this project useful or interesting, consider starring the repository!
