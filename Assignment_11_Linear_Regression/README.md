# Assignment 09: Analyzing Data (Solar Panels Sales & Multi-Dimensional Aggregation)

This assignment focuses on multidimensional sales data analysis, pivoting, and aggregation techniques using enterprise-style transactions from a solar panel manufacturer (RVN Company, UK). The analytical workflow covers multi-level grouping (`groupby`), hierarchical aggregations (`agg` with `sum`, `mean`, `min`, `max`), flexible cross-tabulations using `pivot_table`, and time-series/sequential rate-of-change analysis using `.pct_change()`.

---

## Technical Stack & Environment

- **Language:** Python 3.9+
- **Libraries:** `pandas`, `NumPy`
- **Environment:** Jupyter Notebook (`.ipynb`) & Reproducible Python Scripts
- **Reference Curriculum:** CIS 2267 / Murach's Python for Data Analysis (Sinclair Community College)

---

## Dataset Overview

- **Context:** Synthetic enterprise ERP sales records for solar panel installations in the United Kingdom, recorded in British Pounds Sterling (GBP, £)
- **Dataset:** `sales.csv` (64 records)
- **Independent Variables (Dimensions):**
  - `Year`: 2026, 2027
  - `Region`: North, South, East, West
  - `Type`: Residential, Commercial
  - `Product`: Economy, Good, Better, Best
- **Value Variables (Metrics):**
  - `Quantity_Sold`: Volume of solar panel units sold.
  - `Price_GBP`: Unit price per panel installation in British Pounds (£).
  - `Total_Sales_GBP`: Total revenue generated (`Quantity_Sold × Price_GBP`).

---

## Analytical Methods & Highlights

1. **Categorical Groupings (`groupby`):** Evaluating mean sales values across operational dimensions (`Year`, `Region`, `Product`).
2. **Multi-Index Aggregations (`agg`):** Applying multi-metric functions (`sum`, `mean`, `min`, `max`) across hierarchical levels (`Year` × `Region` × `Product`).
3. **Cross-Tabulation & Multi-Dimensional Pivoting (`pivot_table`):**
   - Pivoting time periods against geographic territories with multi-column values.
   - Comparative evaluation of product classes across residential and commercial sectors.
   - Multi-level index and column pivots tracking metric boundaries (`min` vs. `max`).
4. **Growth Analysis (`pct_change`):** Computing period-over-period and sequential percentage change of total revenue grouped by operational year and market territory.

---

## Repository Structure

```text
Assignment_09_AnalyzingData/
├── data/
│   └── sales.csv                           # Raw enterprise solar panel sales dataset
├── docs/
│   └── 09_Assignment_AnalyzingData.pdf     # Exported assignment worksheet report
├── notebooks/
│   └── 09_Assignment_AnalyzingData.ipynb   # Executed Jupyter notebook workflow
└── README.md
```
---

### Workflow Summary & Key Learnings

- **Data Inspection & Integrity:** Loaded synthetic enterprise ERP sales records for solar panel installations, verified dimensions across 64 individual observations, and confirmed dataset consistency across operational variables.

- **Dimensional Categorization:** Structured sales metrics across independent categorical dimensions, separating temporal variables (`Year`), geographical territories (`Region`), operational sectors (`Type`), and tiers (`Product`).

- **Multi-Level Aggregation:** Implemented hierarchical groupings using `sales.groupby(['Year', 'Region', 'Product'])` and applied multiple simultaneous aggregate functions (`sum`, `mean`, `min`, `max`) to extract performance boundaries across transaction volumes and revenues.

- **Cross-Tabulation & Multi-Dimensional Pivoting:** Built versatile cross-tabulations using `pivot_table` to reshape multi-dimensional metrics, evaluating average price points and units sold across regions and sectors with multi-index row and column hierarchies.

- **Sequential Rate-of-Change Analysis:** Calculated period-over-period and sequential percentage changes using `.pct_change()` on aggregated revenue to track performance fluctuations across operating years and geographic markets.
---

### How to Run

1. Open **Anaconda Prompt** (or your standard terminal/Command Prompt).

2. Navigate to the assignment directory:
   ```bash
   cd Assignment_09_AnalyzingData
   ```
3. Launch Jupyter Notebook:
   ```bash
   jupyter notebook
   ```
4. In the browser window that opens automatically, navigate to the `notebooks/` folder and open `09_Assignment_AnalyzingData.ipynb`.

5. Run all cells sequentially to execute the data cleaning pipeline, generate feature percentages, and view the aggregated summary table.
