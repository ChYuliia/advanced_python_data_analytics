# Python Data Analytics Coursework

This repository serves as a structured workspace for coursework, data wrangling labs, and analytical projects based on **Murach's Python for Data Analysis** and CIS program requirements at Sinclair Community College.

---

## Technical Stack & Libraries

* **Language:** Python 3.9+
* **Core Data Tools:** `pandas`, `NumPy`, `scikit-learn`
* **Visualization:** `matplotlib`, `seaborn`
* **Environment:** Jupyter Notebooks (`.ipynb`) & Reproducible Python Scripts

---

## Repository Structure & Assignments

Each assignment is self-contained within its own directory, including raw datasets, Jupyter notebooks, exported PDF reports, and documentation:

* **[Assignment 01: Introduction to Python & Process Review](Assignment_01_Python_Review/)**  
  * *Focus:* Python control flow, interactive console loops, custom statistical functions, and data analytics process documentation.
* **[Assignment 02: Pandas Essentials (BLS Labor Force)](Assignment_02_Pandas_Essentials/)**  
  * *Focus:* Data cleaning with regex, handling missing values, unit normalization, timeseries indexing, and decennial aggregations.
* **[Assignment 03: Pandas Essentials for Data Visualization](Assignment_03_Pandas_Visualizations/)**  
  * *Focus:* Exploratory Data Analysis (EDA) using built-in pandas/Matplotlib plotting (line charts, bar charts, KDE density plots, pie charts, and multi-panel subplots).
* **[Assignment 04: The Seaborn Essentials for Data Visualization](Assignment_04_Seaborn_Visualizations/)**  
  * *Focus:* Advanced data visualization with Seaborn, data reshaping using `pandas .melt()`, relational line plots, multi-panel faceted subplots, categorical bar plots, and Kernel Density Estimation (KDE) over historical US population data.
* **[Assignment 05: Obtaining Data (Statistics Canada)](Assignment_05_GetData/)**  
  * *Focus:* Automated data retrieval via URLs and ZIP extraction, data governance and copyright compliance under StatCan Open Licence, exploratory data analysis, and professional visualizations with Seaborn.
* **[Assignment 06: Clean Data (Income Inequality vs GDP per Capita)](Assignment_06__CleanData/)**  
  * *Focus:* Data cleaning and temporal imputation (`ffill`/`bfill`), target year snapshot filtering (2019), logarithmic scale data visualization with Seaborn and Matplotlib, custom axis formatting, and analytical interpretation of wealth distribution versus economic output.
* **[Assignment 07: Preparing Data (Avocado Prices)](Assignment_07_PreparingData/)**  
  * *Focus:* Data cleaning and inspection, handling missing values, filtering geographical regions, dropping irrelevant index and PLU columns, datetime conversion, column name standardization, feature engineering (calculating bag size percentages), and multi-level data aggregation with `groupby` and `unstack`.
* **[Midterm Project: US Farmland Data Analysis (2012 vs 2017)](Midterm_Project_Farmland/)**  
  * *Focus:* Multi-part analytical project involving loading and cleaning USDA NASS Census of Agriculture data, calculating absolute and relative changes, merging state landmass data from U.S. Census Bureau Gazetteer Files, computing agricultural density proportions, and synthesizing findings into a structured policy report.
* **[Assignment 09: Analyzing Data (Solar Panels Sales)](Assignment_09_AnalyzingData/)**  
  * *Focus:* Multidimensional data analysis using `groupby` aggregations (`agg(['sum', 'mean', 'min', 'max'])`), cross-tabulation and multi-index aggregation with `pivot_table`, and sequential rate-of-change analysis using `.pct_change()`.
* **[Assignment 10: Time-Series Data & Outlier Analysis (BLS Employment Trends)](Assignment_10_Time_Series_Data/)**  
  * *Focus:* Time-series annualization of monthly labor statistics (handling incomplete final years), comparative outlier treatment methodologies (COVID-19 impact), linear interpolation modeling (`interpolate()`), OLS trendline regression forecasting for 2023–2025, coefficient of determination ($R^2$) evaluation, and scenario-based absolute/relative variance analysis.
* **[Assignment 11: Machine Learning & Linear Regression (Diamonds Price Prediction)](Assignment_11_Linear_Regression/)**  
  * *Focus:* Simple linear regression workflow using `scikit-learn`, correlation matrix analysis with condensed Seaborn heatmaps, train/test splitting (`train_test_split`), model fitting and $R^2$ score evaluation, prediction transformation into pandas DataFrames, data reshaping with `.melt()`, and regression line visualization.
* **[Assignment 12: Multiple Linear Regression & Feature Selection (Auto MPG)](Assignment_12_Multiple_Regression/)**  
  * *Focus:* Multiple linear regression workflow using `scikit-learn`, data cleaning and categorical string extraction with lambda expressions, categorical encoding via `pd.get_dummies()`, feature scaling with `StandardScaler`, correlation analysis, automated feature selection using `SelectKBest` with `mutual_info_regression`, dynamic $k$-feature iterative evaluation via `for` loops, model performance tracking ($R^2$ train vs test scores), and evaluation of optimal model complexity.
* **[Case Study 01: U.S. Maple Syrup Production & Sustainability Analysis](Case_Study_01_Maple_Syrup/)**  
  - *Focus:* End-to-end data analytics case study aligned with UN Sustainable Development Goal 15 (Life on Land) using USDA NASS Quick Stats data (2012, 2013 proxy, and 2017); filtering state-level `TOTAL` aggregates, reshaping wide/long tables (`.melt()`, `.pivot()`), multi-chart exploratory visualization (pie, bar, scatter, pairplot, and condensed correlation heatmaps), simple linear regression modeling with `scikit-learn`, and environmental policy recommendations.
* **[Case Study 02: Strategic KPI Dashboard: Apple Inc. vs. Alphabet & Meta (2019–2021)](Case_Study_02_KPI_Dashboard/)**  
  - *Focus:* Executive financial benchmarking from the perspective of Apple's CIO using SEC EDGAR 10-K filings (36 baseline observations across Profit, Sales, Assets, and Equity); computing efficiency ratios (ROS, ROA, ROE) and three-year growth metrics (Dollar, Percent, and Return Growth) in `pandas`, reshaping multi-index tables into PDF-safe flat summary views, and building standardized 2×2 Seaborn/Matplotlib trend and market-share dashboards.
* *(The Final Capstone Project will be added here upon completion.)*
  
---

## How to Navigate & Run

1. Clone the repository to your local machine:
   ```bash
   git clone [https://github.com/](https://github.com/)<your-username>/python_data_analytics.git
   ```
2. Navigate to any assignment folder:
   ```bash
   cd Assignment_0X_Name
   ```
3. Launch Jupyter Notebook to explore or run the code:
   ```bash
   jupyter notebook notebooks/
   ```
