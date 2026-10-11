# Assignment 07: Preparing Data (Avocado Prices & Sales Volume)

This assignment focuses on data cleaning, transformation, and structural preparation using historical data on avocado prices and sales volume across multiple U.S. markets. The workflow covers inspecting data integrity, checking for missing values, filtering out overlapping regional aggregates, dropping irrelevant columns, standardizing dates and headers, engineering percentage-based features for bag sizes, and performing multi-level data aggregation with `groupby` and `unstack`.

---

## Technical Stack & Environment

- **Language:** Python 3.9+

- **Libraries:** `pandas`, `NumPy`

- **Environment:** Jupyter Notebook (`.ipynb`) & Reproducible Python Scripts

- **Reference Curriculum:** CIS 2267 / Murach's Python for Data Analysis (Sinclair Community College)

---

## Dataset Overview

- **Source:** Student projects for Murach’s Python for Data Analysis / Avocado historical market dataset

- **Dataset:** `avocado.csv`

- **Key Variables & Transformations:**
  - `Date`: Observation date (converted to datetime format).
  - `Region`: Geographic market name (filtered to exclude nationwide aggregates like `TotalUS`).
  - `Type`: Avocado cultivation type (`conventional` or `organic`).
  - `TotalBags`: Total volume of bags sold.
  - *Engineered Features:* `PctSmallBags`, `PctLargeBags`, `PctXLargeBags` (calculated percentage proportions relative to `TotalBags`).

---

## Repository Structure

```text
Assignment_07_PreparingData/
├── data/
│   └── avocado.csv                        # Raw historical avocado pricing and sales dataset
├── docs/
│   └── 07_Assignment_PreparingData.pdf    # Exported assignment worksheet report
├── notebooks/
│   └── 07_Assignment_PreparingData.ipynb  # Executed notebook workflow & data pipeline
└── README.md
```
---

### Workflow Summary & Key Learnings

- **Data Inspection & Integrity:** Loaded historical avocado market data, verified structural integrity, and computed missing values summaries across all columns to confirm dataset completeness.

- **Geographical Filtering:** Filtered out nationwide aggregate records (`TotalUS`) to prevent data overlap and maintain consistent regional granularity, accurately tracking the count of dropped rows.

- **Schema Transformation & Standardization:** Dropped irrelevant index (`Unnamed: 0`) and PLU volume columns (`4046`, `4225`, `4770`), converted the `Date` field into a standard datetime format for temporal handling, and standardized column headers to title case without spaces.

- **Feature Engineering:** Calculated proportional bag size distributions by deriving percentage metrics for small, large, and extra-large bags relative to total bag volume (`TotalBags`).

- **Multi-Level Aggregation & Pivoting:** Executed multi-level grouping by Region, Year, and Type, summed total bag volumes, and applied `unstack` to pivot cultivation types into separate columns for a structured summary report.
---

### How to Run

1. Open **Anaconda Prompt** (or your standard terminal/Command Prompt).

2. Navigate to the assignment directory:
   ```bash
   cd Assignment_07_PreparingData
   ```
3. Launch Jupyter Notebook:
   ```bash
   jupyter notebook
   ```
4. In the browser window that opens automatically, navigate to the `notebooks/` folder and open `07_Assignment_PreparingData.ipynb`.

5. Run all cells sequentially to execute the data cleaning pipeline, generate feature percentages, and view the aggregated summary table.
