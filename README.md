# Python Data Analytics Coursework

This repository serves as a structured workspace for coursework, data wrangling labs, and analytical projects based on **Murach's Python for Data Analysis** and CIS program requirements at Sinclair Community College.

---

## Technical Stack & Libraries

* **Language:** Python 3.9+
* **Core Data Tools:** `pandas`, `NumPy`
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
*(Future assignments and capstone projects will be added here progressively.)*
* **[Assignment 06: Income Inequality vs GDP per Capita](Assignment_06_Income_Inequality_GDP/)**  
  * *Focus:* Data cleaning and temporal imputation (`ffill`/`bfill`), target year snapshot filtering (2019), logarithmic scale data visualization with Seaborn and Matplotlib, custom axis formatting, and analytical interpretation of wealth distribution versus economic output.
  * *(Future assignments and capstone projects will be added here progressively.)*
    
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
