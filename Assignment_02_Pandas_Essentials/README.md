# Assignment 02: Pandas Essentials for Data Analysis

This assignment explores fundamental data wrangling, cleaning, transformation, and statistical aggregation techniques in **pandas** using historical macroeconomic data from the U.S. Bureau of Labor Statistics (BLS). The workflow processes 79 years of monthly Civilian Labor Force metrics (1948–2026), cleans text and footnote artifacts, normalizes units, calculates annual and decennial trends, and exports both tabular serializations and visualizations.

---

## Technical Stack & Environment

* **Language:** Python 3.9+
* **Libraries:** `pandas`, `matplotlib`
* **Environment:** Jupyter Notebook (`.ipynb`)
* **Reference Curriculum:** CIS 2267 / Murach's Python for Data Analysis (Sinclair Community College)

---

## Dataset Overview

* **Source:** U.S. Bureau of Labor Statistics (BLS) — Unemployment & Civilian Labor Force Level
* **File:** `data/CivilianLaborForce.csv` (exported serial backup: `data/CivilianLaborForce.pkl`)
* **Timespan:** 1948–2026 (79 annual observation records across 12 monthly features)
* **Scale & Units:** Original records reported in thousands; converted to actual headcounts ($1\text{ unit} = 1{,}000\text{ individuals}$) during preprocessing.

---

## Repository Structure

```text
Assignment_02_Pandas_Essentials/
├── data/
│   ├── CivilianLaborForce.csv                 # Source BLS timeseries data
│   └── CivilianLaborForce.pkl                 # Serialized cleaned DataFrame
├── docs/
│   └── 02_Assignment_Pandas_Essentials.pdf    # Exported assignment worksheet report
├── notebooks/
│   └── 02_Assignment_Pandas_Essentials.ipynb  # Executed analysis notebook
└── README.md
```

## Workflow & Analysis Summary

* **Data Ingestion & Attribute Inspection:**  
  Imported `CivilianLaborForce.csv` using `pd.read_csv()` and inspected dataset characteristics via `.info()`, `.index`, `.columns`, and `.shape` (79 rows × 13 columns).

* **Regex Data Cleaning & Type Casting:**  
  Addressed non-numeric data types across monthly columns caused by BLS footnote annotations (e.g., `(1)`, `(9)`, `(12)`), whitespace, and missing data dashes (`-`). Cleared footnote markers using regex pattern `replace(r'\(\d+\)', '', regex=True)` and converted columns to numeric floats using `pd.to_numeric(..., errors='coerce')`.

* **Unit Normalization:**  
  Scaled all monthly macroeconomic workforce numbers by multiplying by $1{,}000$ to represent actual headcounts instead of values reported in thousands.

* **Targeted Historical Comparisons:**  
  Queried historical benchmarks (`Year in (1961, 2021)`) to compute monthly means across annual rows (`axis=1`), demonstrating that the U.S. labor force more than doubled from **70,449,917** in 1961 to **161,212,000** in 2021.

* **Interactive Query Loop:**  
  Constructed a dynamic user-input loop with input validation against dataset bounds (`min_year` to `max_year`), outputting filtered annual records and calculating corresponding annual workforce averages.

* **Row-Wise Feature Engineering:**  
  Engineered an `Annual` feature column by computing the rounded mean across all twelve calendar months (`axis=1`).

* **Index Configuration & Serialization:**  
  Assigned `Year` as the primary DataFrame index using `set_index('Year', verify_integrity=True)` and exported the processed data to disk via `.to_pickle('CivilianLaborForce.pkl')`.

* **Visualizations & Decennial Aggregations:**  
  * **Longitudinal Timeseries Plot:** Visualized national workforce expansion from 1948 to 2026 scaled in millions (`Annual / 1e6`) using Matplotlib.
  * **Decade Grouping & Summary Statistics:** Reset the index to engineer a `Decade` feature (`(Year // 10) * 10`), calculated decennial aggregation metrics (`mean`, `median`, `std`), and rendered long-term workforce evolution via a grouped bar chart.

---

## How to Run

1. Open **Anaconda Prompt** (or your standard terminal/Command Prompt).

2. Navigate to the assignment directory:
   ```bash
   cd Assignment_02_Pandas_Essentials
   ```
3. Launch Jupyter Notebook:
   ```bash
   jupyter notebook
   ```
4. In the browser window that opens automatically, navigate to the `notebooks/` folder and open `02_Assignment_Pandas_Essentials.ipynb`.
5. Run all cells sequentially to reproduce data cleaning, queries, calculations, and plots.
 
