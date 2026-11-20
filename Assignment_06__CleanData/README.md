# Assignment 06: Income Inequality vs GDP per Capita

This assignment investigates global economic disparities by analyzing the relationship between a country's economic output (**GDP per capita**) and its income inequality (**Gini index**) for the year 2019. The workflow covers data wrangling, handling missing values through temporal propagation, target year snapshot filtering, logarithmic scale data visualization using Seaborn and Matplotlib, and analytical interpretation of wealth distribution.

---

## Technical Stack & Environment

* **Language:** Python 3.9+
* **Libraries:** `pandas`, `NumPy`, `seaborn`, `matplotlib`
* **Environment:** Jupyter Notebook (`.ipynb`) & Reproducible Python Scripts
* **Reference Curriculum:** CIS 2267 / Murach's Python for Data Analysis (Sinclair Community College)

---

## Dataset Overview

* **Source:** Our World in Data / Global Economic Inequality Database
* **Dataset:** `gini-vs-gdp-per-capita.csv`
* **Key Variables:**
  * `Entity`: Country or regional entity name.
  * `Year`: Observation year.
  * `Gini_ind`: Gini index measuring income inequality (higher values indicate greater inequality).
  * `GDP_per_capita`: Gross Domestic Product per capita, PPP (constant 2017 international \$).

---

## Repository Structure

```text
Assignment_06_Income_Inequality_GDP/
├── data/
│   └── gini-vs-gdp-per-capita.csv        # Raw dataset containing historical GDP and Gini metrics
├── docs/
│   └── 06_Assignment_CleanData.pdf       # Exported assignment worksheet report
├── notebooks/
│   └── 06_Assignment_CleanData.ipynb     # Executed notebook workflow, data pipeline & visualizations
└── README.md
```
---

### Workflow Summary & Key Learnings

* **Data Wrangling & Imputation:** Processed global socio-economic datasets, standardizing variable names and removing non-country aggregate regions to isolate sovereign entities. Applied entity-level chronological forward and backward filling (`ffill`/`bfill`) to bridge temporal gaps in historical Gini index and GDP data.
* **Target Year Snapshot:** Filtered structured time-series data strictly for the target year (**2019**) and performed a complete-case analysis (`dropna`) to ensure data integrity for cross-sectional comparison.
* **Exploratory Data Analysis (EDA):** Inspected memory usage, dataframe shapes, and generated transposed statistical summaries (`describe().T`) to evaluate the distribution of global income inequality and economic output.
* **Advanced Visualization:** 
  * **Logarithmic Scale Scatter Plot:** Constructed a professional relational plot using `seaborn` and `matplotlib` with a logarithmic scale on the X-axis for GDP per capita to effectively visualize non-linear relationships across diverse economies.
  * **Custom Formatting & Annotation:** Configured major-tick gridlines, currency formatting (`$`), and programmatically highlighted key benchmark countries (**Gabon** and the **United States**) with custom bounding boxes and annotations.
* **Analytical Interpretation:** Concluded the study with a formal evaluation of the weak negative relationship between economic development and income distribution, noting the high variance among wealthy nations and the necessity of structural government policies.

---

### How to Run

1. Open **Anaconda Prompt** (or your standard terminal/Command Prompt).
2. Navigate to the assignment directory:
   ```bash
   cd Assignment_06_CleanData
   ```
3. Launch Jupyter Notebook:
   ```bash
   jupyter notebook
   ```
4. In the browser window that opens automatically, navigate to the 'notebooks/' folder and open `06_Assignment_CleanData.ipynb`.
5. Run all cells sequentially to execute the data cleaning pipeline, generate the log-scale visualization, and view the analysis.
