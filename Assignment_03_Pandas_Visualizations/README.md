# Assignment 03: The Pandas Essentials for Data Visualization

This assignment demonstrates foundational and exploratory data visualization techniques using the built-in plotting capabilities of **pandas** (backed by Matplotlib). The analysis evaluates historical US demographic trends across 50 states and jurisdictions from 1900 to 2020 based on USAFacts population data.

---

## Technical Stack & Environment

* **Language:** Python 3.9+
* **Libraries:** `pandas`, `openpyxl`, `matplotlib`
* **Environment:** Jupyter Notebook (`.ipynb`)
* **Reference Curriculum:** CIS 2267 / Murach's Python for Data Analysis (Sinclair Community College)

---

## Dataset Overview

* **Source:** USAFacts Population & Demographics (Creative Commons Attribution-ShareAlike 4.0)
* **File:** `data/population_usafacts.xlsx`
* **Dimensions:** 121 rows × 53 columns (1900–2020 annual metrics across states and territories)
* **Indexing:** Timeseries indexed on `Year`

---

## Repository Structure

```text
Assignment_03_Pandas_Visualizations/
├── data/
│   └── population_usafacts.xlsx            # Source demographic dataset
├── docs/
│   └── 03_Assignment_Ch3_Pandas.pdf        # Exported assignment worksheet report
├── notebooks/
│   └── 03_Assignment_Pandas.ipynb          # Executed notebook workflow
└── README.md

```
---

## Visualizations & Workflow Summary

* **Data Ingestion & Timeseries Indexing:**  
  Loaded the demographic Excel dataset via `pd.read_excel("population_usafacts.xlsx")` and set the `Year` column as the index with `pop.set_index('Year')`.

* **Default Multi-Series Line Plotting:**  
  Created an initial baseline chart using `pop.reset_index().plot()` to inspect full-table series trends across all jurisdictions.

* **Targeted Regional Timeseries Comparison:**  
  Filtered specific Midwestern states using `pop[['Ohio', 'Indiana', 'Kentucky']].plot.line()` to generate a readable longitudinal line chart.

* **Filtered Discrete Bar Chart:**  
  Queried post-2000 records using `.query('Year > 2000')` to render recent Ohio population trends via a vertical bar chart (`.Ohio.plot.bar()`).

* **Decennial Modulo Sampling (Horizontal Bar Chart):**  
  Isolated ten-year census milestones using arithmetic modulo filtering (`Year % 10 == 0`) and rendered historical national totals with a horizontal bar plot (`.Total.plot.barh()`).

* **Kernel Density Estimation (KDE):**  
  Generated univariate density distributions for Ohio's population using `pop.Ohio.plot.density()` to visualize data clustering over time.

* **Proportional Categorical Composition:**  
  Extracted cross-sectional 2020 counts with `pop.loc[2020, ['Ohio', 'Indiana', 'Kentucky']]` to display regional distribution using a pie chart (`.plot.pie()`).

* **Multi-Panel Comparative Subplots:**  
  Produced side-by-side subplots with a 1×3 layout (`subplots=True`, `layout=(1, 3)`), locked value scaling (`sharey=True`), rotated tick labels (`rot=45`), and a custom range (`xlim=(1990, 2020)`) to contrast modern regional growth.

---

## How to Run

1. Open **Anaconda Prompt** (or your standard terminal/Command Prompt).

2. Navigate to the assignment directory:
   ```bash
   cd Assignment_03_Pandas_Visualizations
   ```
3. Launch Jupyter Notebook:
   ```bash
   jupyter notebook
   ```
4. In the browser window that opens automatically, navigate to the `notebooks/` folder and open `03_Assignment_Pandas.ipynb`.
5. Run all cells sequentially to load the dataset and generate the plots.
