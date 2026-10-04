# Assignment 05: Obtaining Data & Statistics Canada

This assignment investigates data sources, legal and ethical restrictions on data use, and practical methods for obtaining and analyzing public data using **Statistics Canada**. The workflow covers data governance compliance, automated data downloading via URL, exploratory data analysis (EDA), and professional data visualizations.

---

## Technical Stack & Environment

* **Language:** Python 3.9+
* **Libraries:** `pandas`, `requests`, `zipfile`, `seaborn`, `matplotlib`
* **Environment:** Jupyter Notebook (`.ipynb`)
* **Reference Curriculum:** CIS 2267 / Murach's Python for Data Analysis (Sinclair Community College)

---

## Dataset Overview

* **Source:** Statistics Canada (Open Licence Agreement)
* **Dataset:** Table 11-10-0125-01 (*Detailed food spending, Canada, regions and provinces*)
* **Acquisition Method:** Programmatic download of a ZIP archive via direct URL request (`urllib.request`), followed by automated extraction and CSV ingestion.

---

## Repository Structure

```text
Assignment_05_GetData/
├── docs/
│   └── 05_Assignment_Yuliia_GetData.pdf      # Exported assignment worksheet report
├── notebooks/
│   └── 05_Assignment_Yuliia_GetData.ipynb    # Executed notebook workflow & code pipeline
└── README.md
```
---

### Workflow Summary & Key Learnings

* **Data Governance & Ethics:** Researched Canadian legislative frameworks (The Statistics Act, Privacy Act) ensuring data privacy, confidentiality, and proper IP attribution under the StatCan Open Licence Agreement.
* **Automated Data Pipeline:** Implemented robust code to retrieve, extract, and load large statistical tables directly into a pandas `DataFrame` without manual pre-downloads.
* **Exploratory Data Analysis (EDA):** Performed structural checks (`shape`, `info()`) and statistical summaries (`describe()`) to inspect memory usage, handle missing values, and clean numerical data types (`pd.to_numeric` with `errors='coerce'`).
* **Visualizations:**
  * **Relational Line Plot:** Filtered metrics for Canada to visualize long-term trends across key summary-level food expenditure categories over time using `sns.lineplot()`.
  * **Categorical Bar Plot:** Generated a clean single-year snapshot comparing major expenditure categories to improve readability and avoid visual clutter.
* **Academic Citation:** Concluded the analysis with a properly formatted formal citation including the official StatCan DOI.

---
### Official Data Citation

Statistics Canada. Table 11-10-0125-01 *Detailed food spending, Canada, regions and provinces*.  
DOI: https://doi.org/10.25318/1110012501-eng

---
### How to Run

1. Open **Anaconda Prompt** (or your standard terminal/Command Prompt).
2. Navigate to the assignment directory:
   ```bash
   cd Assignment_05_GetData
   ```
3. Launch Jupyter Notebook:
   ```bash
   jupyter notebook
   ```
4. In the browser window that opens automatically, navigate to the `notebooks/ folder` and open `05_Assignment_Yuliia_GetData.ipynb`.
5. Run all cells sequentially to execute the data pipeline, generate the plots, and view the analysis.
