# Case Study 02: Strategic KPI Dashboard: Apple Inc. vs. Alphabet & Meta (2019–2021)

This case study focuses on designing and implementing an executive financial benchmarking workflow and visual KPI dashboard using Python's `pandas`, `seaborn`, and `matplotlib` libraries. Prepared from the perspective of the Chief Information Officer (CIO) of Apple, Inc., the analysis evaluates Apple's three-year financial performance (2019–2021) against primary industry competitors Alphabet, Inc. (Google) and Meta Platforms, Inc. (Facebook). Using publicly available U.S. Securities and Exchange Commission (SEC) EDGAR Form 10-K filings, the workflow transforms 36 core financial observations into efficiency ratios (ROS, ROA, ROE), three-year growth indicators, a PDF-safe executive summary table, and standardized 2×2 trend and market-share visualizations.

---

## Technical Stack & Environment

- **Language:** Python 3.9+
- **Libraries:** `pandas`, `seaborn`, `matplotlib`
- **Environment:** Jupyter Notebook (`.ipynb`) & Exported PDF Executive Report
- **Reference Curriculum:** CIS 2267 / Murach's Python for Data Analysis (Sinclair Community College)

---

## Dataset Overview

- **Source:** U.S. Securities and Exchange Commission (SEC) EDGAR Database — Corporate Form 10-K Annual Reports (six Form 10-K filings total, two per company, accessed June 2022)
- **Dataset:** `Dataset KPI Long.csv` — normalized long-format table containing **36 baseline observations** (3 companies × 3 years × 4 financial attributes) with zero missing values
- **Dimensions & Metrics:**
  - `Who`: Company identifier (`Apple`, `Alpha`, `Meta`)
  - `What`: Core financial statement attribute measured in millions of USD (`Profit`, `Sales`, `Assets`, `Equity`)
  - `Year`: Fiscal reporting year (`2019`, `2020`, `2021`)
  - `Data`: Reported dollar figure (USD millions)

---

## Analytical Methods & Highlights

1. **Data Inspection & Brand Styling Standardization:**
   - Verified data completeness, schema types, and observation counts (`36` non-null entries) via `.info()` and `display()`.
   - Established consistent brand color constants (`#00B050` green for Apple, `#2F75B5` blue for Alphabet, `#C55A11` brown for Meta) and categorical ordering (`pd.Categorical`) across all tables and charts.

2. **Efficiency Ratio Engineering (`Return on`):**
   - Computed three core profitability-to-resource efficiency KPIs for 2019–2021 using vectorized index alignment (`(Profit / Attribute) * 100`, rounded to whole percentages):
     - **Return on Sales (ROS):** Net income generated per dollar of revenue.
     - **Return on Assets (ROA):** Net income generated per dollar of total assets.
     - **Return on Equity (ROE):** Net income generated per dollar of shareholders' equity.

3. **Three-Year Growth Analysis (2019 to 2021):**
   - Calculated **Dollar Growth** (`2021 - 2019`), **Percent Growth** (`(2021 - 2019) / 2019 * 100`), and **Return Growth** in percentage points (`2021 Return % - 2019 Return %`) across all attributes.
   - Consolidated baseline dollar figures and derived KPIs into a unified long-format table (`kpi_enriched`) and reshaped it via `.pivot()` with flattened single-level column headers for clean LaTeX/PDF rendering.

4. **Executive Trend & Market-Share Visualizations (2×2 Grids):**
   - **Profit & Efficiency Trend Dashboard:** Built a 2×2 Seaborn/Matplotlib line grid (`Profit ($mils)`, `Return on Assets`, `Return on Sales`, `Return on Equity`) featuring custom y-axis tick intervals (`20,000`, `10%`, `10%`, `50%`), solid vs. dashed competitor line styling, a highlighted green border around `Return on Equity`, and a shared legend.
   - **Market Share Comparison Dashboard:** Built a 2×2 pie chart grid comparing 2019 vs. 2021 combined three-company shares of `Sales` and `Profit`, with Apple's wedge exploded (`explode=[0.08, 0, 0]`) for visual emphasis.

5. **Key Strategic Findings:**
   - **Capital Efficiency Leadership:** Apple generated the highest absolute profit (**$94,680M** in 2021, up **+71%** from **$55,256M** in 2019) and dominated peer efficiency in **ROA** (**27%** vs. **24%** for Meta and **21%** for Alphabet) and **ROE**, which more than doubled from **61%** in 2019 to **150%** in 2021 (compared to **32%** for Meta and **30%** for Alphabet).
   - **Market Share Dynamics:** While Apple expanded total sales by **+41%** (**$105,643M**), its share of combined three-company sales shifted from **53%** in 2019 to **49%** in 2021, and its combined profit share moved from **51%** to **45%** as Alphabet (**+121%** profit growth) and Meta (**+113%** profit growth) grew at faster percentage rates.

---

## Repository Structure

```text
Case_Study_02_KPI_Dashboard/
├── data/
│   └── Dataset KPI Long.csv                # SEC EDGAR 10-K financial dataset (36 observations, 2019–2021)
├── docs/
│   └── KPI_Case_Study.pdf                  # Exported executive KPI dashboard report
├── notebooks/
│   └── KPI_Case_Study.ipynb                # Executed Jupyter notebook workflow
└── README.md
```
---

### Workflow Summary & Key Learnings

- **Data Ingestion & Schema Verification:** Loaded the SEC EDGAR 10-K dataset (`Dataset KPI Long.csv`, 36 baseline observations across 3 companies, 3 years, and 4 attributes), verified data types and completeness with `.info()` and `display()`, and established consistent brand color constants (`#00B050`, `#2F75B5`, `#C55A11`) and categorical ordering (`pd.Categorical`).

- **Efficiency Ratio Engineering (`Return on`):** Extracted `Profit` series via `.query()` and `.set_index()` to compute Return on Sales (ROS), Return on Assets (ROA), and Return on Equity (ROE) as `(Profit / Attribute) * 100`, rounding results to whole percentages across 2019–2021.

- **Three-Year Growth Computation (2019 to 2021):** Sliced 2019 and 2021 baseline figures and efficiency ratios to calculate absolute **Dollar Growth** (`2021 - 2019`), relative **Percent Growth** (`(2021 - 2019) / 2019 * 100`), and **Return Growth** in percentage points (`2021 Return % - 2019 Return %`).

- **Data Consolidation & PDF-Safe Reshaping:** Combined baseline dollar figures and derived KPIs with `pd.concat()`, reshaped the dataset into an executive summary table using `.pivot()`, flattened MultiIndex column headers (`f"{metric}_{year}"`), and formatted numeric values with thousand commas and `%` signs while preserving blank cells for non-applicable profit return rows.

- **2×2 Trend & Market-Share Visualizations:** Built a 2×2 Seaborn/Matplotlib line grid (`Profit ($mils)`, `Return on Assets`, `Return on Sales`, `Return on Equity`) with custom y-axis tick steps (`20,000`, `10%`, `10%`, `50%`), dashed competitor lines, and a green highlight border around `Return on Equity`, alongside a 2×2 pie chart grid with Apple's slice exploded (`explode=[0.08, 0, 0]`) and shared legends.

- **Executive Synthesis & Strategic Takeaways:** Translated quantitative findings into actionable CIO-level conclusions, demonstrating Apple's unmatched capital efficiency (ROE rising from **61%** to **150%**, ROA reaching **27%**, and profit growing **+71%** to **$94,680M**) while identifying market-share shifts in combined sales (**53%** to **49%**) and profit (**51%** to **45%**) driven by faster percentage expansion at Alphabet (**+121%** profit growth) and Meta (**+113%** profit growth)

---
### How to Run

1. Open **Anaconda Prompt** (or your standard terminal/Command Prompt).

2. Navigate to the case study directory:
   ```bash
   cd Case_Study_02_KPI_Dashboard
   ```
3. Launch Jupyter Notebook:
   ```bash
   jupyter notebook
   ```
4. In the browser window that opens automatically, navigate to the `notebooks/` folder and open `KPI_Case_Study.ipynb`.

5. Run all cells sequentially to ingest the SEC EDGAR 10-K dataset (Dataset KPI Long.csv), compute efficiency ratios (ROS, ROA, ROE) and three-year growth indicators (Dollar, Percent, and Return Growth), generate the PDF-safe summary table, and render the 2×2 trend and market-share visualizations.
---

### Data Source & Attribution

- **Source:** U.S. Securities and Exchange Commission (SEC) EDGAR Database — Corporate Form 10-K Annual Reports (https://www.sec.gov/edgar/)
- **Scope & Governance:** Publicly available domain financial figures extracted from six corporate Form 10-K filings (two annual reports per company for Apple, Inc., Alphabet, Inc., and Meta Platforms, Inc., covering fiscal years 2019–2021, accessed June 2022).
