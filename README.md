# Retail Sales Analysis & Forecasting 📊

An end-to-end Data Science and Exploratory Data Analysis (EDA) pipeline designed to ingest, clean, transform, and analyze retail transaction logs from a cafe sales dataset. This repository demonstrates professional workflows for data cleaning (handling mixed missing values), feature engineering, statistical transformations, and complex data aggregations using Python.

## 📋 Project Overview
Raw business data is rarely clean. This project takes a "dirty" cafe transactions dataset (`dirty_cafe_sales.csv`) and subjects it to a rigorous data engineering pipeline. The final goal is to handle missing categorical and numerical entities safely, create advanced business indicators, and map behavioral patterns through clean, high-impact visualizations.

## ✨ Core Pipeline Features

### 1. Robust Data Cleaning & Imputation
* **Numerical Interpolation:** Handled missing entities in quantitative columns (`Quantity`, `Price Per Unit`, `Total Spent`) via robust numeric type-coercion and linear interpolation.
* **Temporal Continuity:** Converted mixed-format transaction dates to strict `datetime64` objects, applying interpolation to secure time-series continuity.
* **Categorical Imputation:** Strategic use of Forward Fill (`ffill`) for `Item` and `Location` rows, and Backward Fill (`bfill`) for missing `Payment Method` records to minimize logical errors.
* **Deduplication:** Integrity evaluation via structural duplicate checks across the dataset matrix.

### 2. Advanced Feature Engineering & Transformation
* **Revenue Calculation (`Ingreso`):** Computed localized dynamic income metrics through vector multiplication ($Quantity \times Price\ Per\ Unit$).
* **Feature Scaling:** Implemented dual feature scaling strategies using `scikit-learn` for future modeling workflows:
  * **Standardization:** Z-score scaling (`StandardScaler`) on numeric distributions.
  * **Normalization:** Min-Max scaling (`MinMaxScaler`) to restrict values within a clean 0-1 range.
* **Custom Data Binning:** Segmented continuous numeric attributes into structural labels (`Low`, `Medium`, `High`) via boundary-conditional `pd.cut` operations.
* **Temporal Feature Extraction:** Extracted native calendar fields (`Dia Semana` and `Mes`) to capture seasonal or weekly consumer behavior.

### 3. Multi-Level Aggregations & Analytics
* **Group-Wise Statistics:** Extracted high-fidelity performance metrics (`sum`, `mean`, `count`, `min`, `max`, `std`, `var`) categorized by inventory items, geographical locations, and timeline indices.
* **Custom Complex Operations:** Leveraged custom `.apply()` architectures to process multi-conditional row splits (e.g., mapping transaction types like *Large Credit Card Purchases*).
* **Anomalous Variance Tracking:** Utilized `.groupby().transform('mean')` to calculate the direct deviation of individual transactions against categorical baseline means, facilitating outlier auditing.

### 4. Exploratory Data Analysis (EDA) & Visualization
Built crisp distributions and relational graphics utilizing `Seaborn` and `Matplotlib`:
* **Distribution & Outlier Subplots:** A unified multi-layered layout combining Histograms with Boxplots to visually isolate skewness and revenue outliers.
* **Time-Series Analysis:** Weekly resampled line charts (`.resample('W').sum()`) capturing chronological cashflow trends.
* **Behavioral Scatter Plots:** Visual correlation matrices plotting product volume metrics against cost factors, color-coded by pricing tiers.
* **Statistical Correlations:** A clear correlation heatmap (`sns.heatmap`) displaying structural dependencies between quantitative columns.

## 🛠️ Tech Stack
* **Language:** Python 3
* **Data Manipulation:** Pandas, NumPy
* **Machine Learning & Scaling:** Scikit-Learn
* **Data Visualization:** Matplotlib, Seaborn

## 📁 Repository Directory Structure
```text
├── dataset/
│   └── dirty_cafe_sales.csv      # Ingested raw transaction records
├── main_pipeline.py              # Main data engineering & EDA script
├── environment.yml               # Conda environment settings
└── README.md                     # Documentation
```
🚀 Getting Started
1. Clone the Repository:
   Bash
   git clone [https://github.com/longaresf/retail-sales-forecasting.git](https://github.com/longaresf/retail-sales-forecasting.git)
   cd retail-sales-forecasting

2. Run the Script:
   Bash
   python main_pipeline.py

✒️ Autor

   Francisco Longares - Científico de Datos & Desarrollador de Soluciones IA - longaresf
