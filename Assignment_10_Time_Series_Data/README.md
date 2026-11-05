# Assignment 10: Time-Series Data (BLS Employment Trends & Outlier Treatment)

This assignment explores time-series data wrangling, trendline modeling, and outlier treatment strategies using monthly civilian employment statistics from the US Bureau of Labor Statistics (BLS). The workflow addresses the unprecedented macroeconomic disruption of the COVID-19 pandemic (2020–2021) by implementing, evaluating, and forecasting three comparative scenarios using Ordinary Least Squares (OLS) linear regression and goodness-of-fit ($R^2$) analysis.

---

## Technical Stack & Environment

- **Language:** Python 3.9+
- **Libraries:** `pandas`, `NumPy`, `matplotlib`, `seaborn`
- **Environment:** Jupyter Notebook (`.ipynb`) & Reproducible Python Scripts
- **Reference Curriculum:** CIS 2267 / Murach's Python for Data Analysis (Sinclair Community College)

---

## Dataset Overview

- **Source:** US Bureau of Labor Statistics (Current Population Survey, Public Domain)
- **Dataset:** `Employment long.xlsx` (Series ID: `LNS12000000`, 123 monthly observations from Jan 2012 to Mar 2022)
- **Granularity & Unit:** Monthly non-farm employment figures measured in thousands of persons ($000$ omitted).
- **Core Dimensions & Metrics:**
  - `Series ID`: Survey series identifier (`LNS12000000`).
  - `Year`: Temporal scope (2012–2022).
  - `Period`: Monthly indicators (`M01` through `M12`).
  - `Value`: Total employment level in thousands.

---

## Analytical Scenarios & Methodology

1. **Temporal Aggregation & Annualization:**
   - Full-year annualized figures (2012–2021) computed as the centered 12-month arithmetic mean.
   - Partial year 2022 estimated using the 3-month average (January–March) centered at February.
2. **Scenario-Based Outlier Treatment:**
   - **Base Case 0 (Unadjusted):** Retains raw annualized data, preserving the severe 2020 shock ($y = 1247.7x + 143223$, $R^2 = 0.6165$).
   - **Case 1 (Interpolation):** Smooths the COVID shock using linear interpolation (`interpolate()`) between 2019 and 2022 benchmarks

---

## Repository Structure

```text
Assignment_10_TimeSeries_Data/
├── data/
│   |── Employment long.xlsx
│   └── Employment wide.xlsx
├── docs/
│   ├── Time-Series Data.pdf
│   └── 10_Assignment_Time_Series_Data.pdf
├── notebooks/
│   └── 10_Assignment_Time_Series_Data.ipynb
└── README.md
```
---

### Workflow Summary & Key Learnings

- **Data Ingestion & Chronological Overview:** Ingested monthly non-farm civilian employment records (Series ID: `LNS12000000`) spanning 123 observations from the US Bureau of Labor Statistics (BLS), validating completeness across temporal indices.

- **Temporal Aggregation & Centered Annualization:** Formulated full-year annualized metrics (2012–2021) using 12-month arithmetic means centered at mid-year (July), and established a centered 3-month February baseline to extrapolate incomplete quarterly data for 2022.

- **Outlier Assessment & Scenario Engineering:** Evaluated structural macroeconomic shocks introduced by the COVID-19 pandemic across three distinct methodological branches:
  - **Base Case 0:** Retained empirical observations unadjusted to quantify residual model distortion.
  - **Case 1:** Mitigated pandemic shock variance by imputing 2020–2021 values via linear interpolation between 2019 baseline and 2022 recovery levels.
  - **Case 2:** Truncated the series to pre-COVID observations (2012–2019) to isolate historical secular momentum.

- **OLS Regression Modeling & Goodness-of-Fit Evaluation:** Standardized temporal features into normalized index coordinates ($x = \text{Year} - 2011$), computed linear trend equations ($y = mx + b$) using `numpy.polyfit`, and quantified explanatory power using the coefficient of determination ($R^2$) via `numpy.corrcoef`.

- **Multi-Horizon Forecasting & Sensitivity Analysis:** Generated employment projections through 2025 ($x = 12, 13, 14$), constructed comparative variance matrices, and evaluated operational trade-offs between model overfitting ($R^2 = 0.9971$ in Case 2 yielding an aggressive $+10.5\text{M}$ variance) and balanced empirical recovery modeling ($R^2 = 0.9308$ in Case 1 yielding a moderate $+3.1\%$ variance).

- **Modular Visualization Architecture:** Encapsulated Matplotlib rendering workflows into a reusable parameterized plotting function (`show_plot`), integrating historical markers, extended trendlines, custom coordinate limits, and dynamic regression annotations.
---

### How to Run

1. Open **Anaconda Prompt** (or your standard terminal/Command Prompt).

2. Navigate to the assignment directory:
   ```bash
   cd Assignment_10_TimeSeries_Data
   ```
3. Launch Jupyter Notebook:
   ```bash
   jupyter notebook
   ```
4. In the browser window that opens automatically, navigate to the `notebooks/` folder and open `10_Assignment_Yuliia_Chernysheva.ipynb`.
   
5. Run all cells sequentially (Cell $\rightarrow$ Run All or Shift + Enter) to execute the monthly-to-annual data cleaning pipeline, generate the three comparative regression scenarios, render the trendline visualizations, and display the 2023–2025 forecast variance tables. 
