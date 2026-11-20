# Midterm Project: US Farmland Data Analysis (2012 vs 2017)

This project focuses on data loading, cleaning, manipulation, and structural integration using historical agricultural census data on U.S. farm acreage alongside official state landmass measurements. The workflow covers standardizing data formats, calculating absolute and relative acreage changes, merging datasets with strict validation checks, computing agricultural density proportions relative to state land areas, and synthesizing findings into a structured policy and data analysis report.

---

## Technical Stack & Environment

- **Language:** Python 3.9+

- **Libraries:** `pandas`, `matplotlib`, `seaborn`

- **Environment:** Jupyter Notebook (`.ipynb`) & Reproducible Python Scripts

- **Reference Curriculum:** CIS 2267 Advanced Python for Data Analytics / Murach's Python for Data Analysis (Sinclair Community College)

---

## Dataset Overview

- **Primary Source:** U.S. Department of Agriculture (USDA) National Agricultural Statistics Service (NASS) Census of Agriculture (compiled via American Farmland Trust / Farmland Information Center).
- **Secondary Source:** U.S. Census Bureau Geography Division State Gazetteer Files.
- **Datasets:** 
  - `Farmland.csv`: Historical state-level farm acreage for 2012 and 2017.
  - `2026_Gaz_state_national.csv`: Official U.S. state land area benchmarks.

- **Key Variables & Transformations:**
  - `state`: Normalized state name (Title Case).
  - `farmland_2012` & `farmland_2017`: Total agricultural acreage converted to integer format.
  - `diff_abs` & `diff_pct`: Engineered absolute net change in acres and relative percentage change.
  - `aland_acres`: Total state land area converted from square miles to acres (1 sq mi = 640 acres).
  - `pct_landmass_2017`: Proportion of state land dedicated to farming.

---

## Repository Structure

```text
Midterm_Project_Farmland/
├── data/
│   ├── Farmland.csv                  # Raw USDA farmland acreage dataset
│   └── 2026_Gaz_state_national.csv   # U.S. Census Bureau state land area file
├── docs/
│   └── 08_Midterm_Project.pdf        # Exported assignment report & policy synthesis
│   └── Project_Guide.pdf             # Course project guidelines, instructions, and evaluation criteria
├── notebooks/
│   └── 08_Midterm_Project.ipynb      # Executed analysis pipeline & visualizations
└── README.md
```
---

### Workflow Summary & Key Learnings

- **Data Inspection & Integrity:** Loaded historical U.S. farmland census data from CSV, verified structural integrity, and confirmed dataset completeness across all 50 states without missing values.

- **Data Cleaning & Standardization:** Standardized column headers to standard snake_case, normalized state names to Title Case to ensure clean string matching, and converted acreage strings into precise integer values.

- **Quantitative Metric Engineering:** Computed absolute net changes in acreage (`diff_abs`) and relative percentage changes (`diff_pct`) between the 2012 and 2017 agricultural censuses to evaluate nationwide and state-level trends.

- **Dataset Merging & Spatial Integration:** Merged the farmland dataset with official U.S. Census Bureau Gazetteer state land area benchmarks, converting square miles to exact acreage (1 sq mi = 640 acres) with strict validation checks.

- **Proportional & Comparative Analysis:** Calculated each state's agricultural land proportion relative to its total landmass for both 2012 and 2017, identifying leading agricultural densities and regions experiencing the most severe relative declines.

- **Visual & Policy Synthesis:** Generated ranked horizontal bar charts to visualize state-level totals and change metrics, and synthesized empirical findings into a structured policy report addressing urban sprawl and UN Sustainable Development Goal #2 (Zero Hunger).

---

### How to Run

1. Open **Anaconda Prompt** (or your standard terminal/Command Prompt).

2. Navigate to the project directory:
   ```bash
   cd Midterm_Project_Farmland
   ```
3. Launch Jupyter Notebook:
   ```bash
   jupyter notebook
   ```
4. In the browser window that opens automatically, navigate to the `notebooks/` folder and open `08_Midterm_Project_Yulia_Chernysheva.ipynb`.

5. Run all cells sequentially to execute the data cleaning and merging pipeline, generate comparative rankings, render the visualizations, and review the policy synthesis report.
