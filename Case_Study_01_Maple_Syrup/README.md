# Case Study 01: U.S. Maple Syrup Production & Sustainability Analysis

This case study focuses on building and evaluating an end-to-end data wrangling, exploratory visualization, correlation, and linear regression workflow using Python's `pandas`, `seaborn`, `matplotlib`, and `scikit-learn` libraries. Aligned with **UN Sustainable Development Goal 15 (Life on Land)**, the analysis investigates U.S. Department of Agriculture (USDA) National Agricultural Statistics Service (NASS) data across the top ten maple syrup producing states for the 2012 and 2017 agricultural census years. The workflow covers multi-file ingestion, state-level `TOTAL` aggregate filtering, missing/suppressed value handling (`(D)`), temporal proxy alignment (using 2013 season length records for 2012), wide-to-long data reshaping (`.merge()`, `.melt()`, `.pivot()`), multi-chart exploratory visualization, correlation and $R^2$ evaluation, simple linear regression modeling with `train_test_split` and `LinearRegression`, and environmental policy recommendations.

---

## Technical Stack & Environment

- **Language:** Python 3.9+
- **Libraries:** `pandas`, `matplotlib`, `seaborn`, `scikit-learn`
- **Environment:** Jupyter Notebook (`.ipynb`) & Reproducible Python Scripts
- **Reference Curriculum:** CIS 2267 / Murach's Python for Data Analysis (Sinclair Community College)

---

## Dataset Overview

- **Source:** U.S. Department of Agriculture (USDA), National Agricultural Statistics Service (NASS) Quick Stats Database (`https://quickstats.nass.usda.gov/`) and United Nations Sustainable Development Goal 15 (`https://sdgs.un.org/goals/goal15`)
- **Datasets:** Four raw USDA NASS CSV extracts (`MapleSyrup_Farms.csv`, `MapleSyrup_Days.csv`, `MapleSyrup_Taps.csv`, `MapleSyrup_Gallons.csv`) consolidated into a clean wide-format table (`maple_syrup`: 20 state-year observations across 10 states and 2 census years, totaling 80 data points) and a reshaped long-format table (`maple_syrup_long`: 80 rows)
- **Target Variable (Metric):**
  - `Gallons`: Total maple syrup production measured in gallons (Census data for 2012 and 2017)
- **Predictor Variables (Operational & Seasonal Dimensions):**
  - `Taps`: Number of active tree taps installed to drain sap (Census data for 2012 and 2017)
  - `Farms`: Number of maple syrup operations with production (Census data for 2012 and 2017)
  - `Days`: Average length of the sap-harvesting season in days (Survey data for 2013 and 2017, with 2013 reassigned as a proxy for 2012)

---

## Analytical Methods & Highlights

1. **Data Inspection & Domain Filtering:**
   - Inspected column schemas, row counts, and data types across all four raw USDA NASS exports using `.info()` and `.head()`.
   - Filtered records strictly for state-level aggregate rows (`Domain == 'TOTAL'`) and constrained observations to the top ten producing states (`CONNECTICUT`, `MAINE`, `MASSACHUSETTS`, `MICHIGAN`, `NEW HAMPSHIRE`, `NEW YORK`, `OHIO`, `PENNSYLVANIA`, `VERMONT`, `WISCONSIN`) to prevent double-counting size-bracket subcategories (`Domain == 'TAPS'`).

2. **Data Cleaning, Proxy Standardization & Type Conversion:**
   - Reassigned 2013 `Days` survey records to `2012` using `.replace(2013, 2012)` so all four metrics align across both five-year agricultural census periods.
   - Stripped thousand-separator commas from string values, coerced suppressed `(D)` disclosure entries into `NaN` via `pd.to_numeric(..., errors='coerce')`, dropped invalid records, and renamed generic `Value` columns to `Farms`, `Days`, `Taps`, and `Gallons`.

3. **Data Integration & Reshaping (Wide & Long Forms):**
   - Aggregated state-year pairs with `.groupby(['State', 'Year'], as_index=False).sum()` and combined all four tables via chained outer `.merge()` operations into a sorted 20-row wide DataFrame (`maple_syrup`).
   - Reshaped the wide dataset into an 80-row long DataFrame (`maple_syrup_long`) using `.melt()` for flexible categorical grouping.
   - Generated multi-metric descriptive statistics (`count`, `sum`, `mean`, `min`, `max`, `std`) grouped by census year.

4. **Exploratory Visualization & Pivot Analysis:**
   - Built a 2017 production share Pie Chart showing Vermont leading at **46.1%** (**2,020,159 gallons**), followed by Maine (**16.4%**) and New York (**16.3%**).
   - Constructed Horizontal and Vertical Bar Charts comparing 2012 vs. 2017 output, highlighting a **93.6%** surge in total ten-state syrup production (from **2,261,692** to **4,377,773 gallons**).
   - Generated Scatter Plots, a Seaborn `pairplot`, and a state-by-year `.pivot()` table to compare yield patterns across predictors.

5. **Correlation Analysis & Linear Regression Modeling:**
   - Computed Pearson correlation coefficients ($r$) and $R^2$ values against `Gallons` in descending order, visualized via both a full symmetric heatmap and a consolidated single-column heatmap.
   - Identified `Taps` as the dominant predictor of syrup output ($r = 0.970$, $R^2 = 0.941$), substantially outperforming `Farms` ($r = 0.579$, $R^2 = 0.335$) and `Days` ($r = 0.505$, $R^2 = 0.255$).
   - Split the dataset into training (67%) and testing (33%) subsets (`test_size=0.33`, `random_state=42`) and trained an Ordinary Least Squares `LinearRegression` model predicting `Gallons` from `Taps`, achieving a test-set $R^2$ score of **0.8018** and confirming that expanding tap infrastructure supports forest conservation under **UN SDG 15** (Targets 15.1, 15.2, and 15.5).

---

## Repository Structure

```text
Case_Study_01_Maple_Syrup/
├── data/
│   ├── MapleSyrup_Days.csv                 # USDA NASS average season length survey data (2013, 2017)
│   ├── MapleSyrup_Farms.csv                # USDA NASS maple operations with production census data (2012, 2017)
│   ├── MapleSyrup_Gallons.csv              # USDA NASS maple syrup production in gallons census data (2012, 2017)
│   └── MapleSyrup_Taps.csv                 # USDA NASS number of tree taps census data (2012, 2017)
├── docs/
│   └── maple_syrup_case_study.pdf          # Exported case study report and executive summary
├── notebooks/
│   └── maple_syrup_case_study.ipynb        # Executed Jupyter notebook workflow
└── README.md
```
---

### Workflow Summary & Key Learnings

- **Data Ingestion & Integrity Inspection:** Loaded four raw USDA NASS Quick Stats CSV files (`MapleSyrup_Farms.csv`, `MapleSyrup_Days.csv`, `MapleSyrup_Taps.csv`, and `MapleSyrup_Gallons.csv`), inspected their schemas and data types using `.head()` and `.info()`, and identified state-level aggregate rows (`Domain == 'TOTAL'`) alongside size-bracket subcategories (`Domain == 'TAPS'`) and suppressed `(D)` entries.

- **Domain Filtering & Proxy Alignment:** Filtered strictly for state-level `TOTAL` rows across the top ten maple syrup producing states to avoid double-counting, retained `Year`, `State`, and `Value`, and reassigned 2013 survey records in the `Days` dataset to `2012` using `.replace(2013, 2012)` as a proxy for missing 2012 season length data.

- **Numeric Coercion & Standardization:** Stripped thousand-separator commas via `.str.replace(',', '', regex=False)`, coerced suppressed `(D)` entries into `NaN` using `pd.to_numeric(..., errors='coerce')`, removed missing values with `.dropna()`, and renamed generic `Value` columns to `Farms`, `Days`, `Taps`, and `Gallons`.

- **Data Merging, Reshaping & Aggregation:** Combined all four cleaned tables via outer `.merge()` operations into a 20-row wide DataFrame (`maple_syrup`), reshaped it into an 80-row long DataFrame (`maple_syrup_long`) using `.melt()`, computed annual descriptive statistics with `.groupby('Year').agg(['count', 'sum', 'mean', 'min', 'max', 'std'])`, and built a state-by-year production table via `.pivot()`.

- **Exploratory Visualization & Correlation Analysis:** Created a 2017 share Pie Chart, Horizontal and Vertical Bar Charts, a Scatter Plot, a Seaborn `pairplot`, and both full and condensed correlation heatmaps, revealing that `Taps` has the strongest linear relationship with `Gallons` ($r = 0.970$, $R^2 = 0.941$), far outperforming `Farms` ($R^2 = 0.335$) and `Days` ($R^2 = 0.255$).

- **Dataset Partitioning & Linear Regression Modeling:** Partitioned `maple_syrup` into a 67% training set and a 33% testing set using `train_test_split(..., test_size=0.33, random_state=42)`, trained a `LinearRegression` model predicting `Gallons` from `Taps`, and evaluated test-set performance ($R^2 = 0.8018$).

- **Sustainability Synthesis & Policy Recommendations:** Connected analytical findings to **UN Sustainable Development Goal 15 (Life on Land)**, demonstrating that helping producers expand active tree taps reliably boosts syrup yield and creates an economic incentive to protect mature sugarbush forests from logging and urban sprawl.

---
### How to Run

1. Open **Anaconda Prompt** (or your standard terminal/Command Prompt).

2. Navigate to the case study directory:
   ```bash
   cd Case_Study_01_Maple_Syrup
   ```
3. Launch Jupyter Notebook:
   ```bash
   jupyter notebook
   ```
4. In the browser window that opens automatically, navigate to the `notebooks/` folder and open `maple_syrup_case_study.ipynb`.   

5. Run all cells sequentially to ingest and clean the four USDA NASS datasets, filter for state-level TOTAL rows, apply the 2013 proxy for 2012 season length, reshape the data into wide and long formats, generate exploratory visualizations and correlation heatmaps, and evaluate the `scikit-learn` linear regression model.

---

### Data Source Attribution

- **U.S. Department of Agriculture (USDA), National Agricultural Statistics Service (NASS):** *Quick Stats Agricultural Database* (2012, 2013, and 2017 Maple Syrup Data): https://quickstats.nass.usda.gov/
- **United Nations:** *Goal 15: Life on Land*, Department of Economic and Social Affairs, Sustainable Development: https://sdgs.un.org/goals/goal15
