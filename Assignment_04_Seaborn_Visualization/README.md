# Assignment 04: The Seaborn Essentials for Data Visualization

This assignment explores advanced data visualization techniques using the **Seaborn** library (built on top of Matplotlib). The workflow focuses on importing demographic data, reshaping it into long form using pandas `.melt()`, and generating structured relational, categorical, and distribution plots to analyze historical US population trends from 1900 to 2020.

---

## Technical Stack & Environment

* **Language:** Python 3.9+
* **Libraries:** `pandas`, `seaborn`, `matplotlib`, `openpyxl`
* **Environment:** Jupyter Notebook (`.ipynb`)
* **Reference Curriculum:** CIS 2267 / Murach's Python for Data Analysis (Sinclair Community College)

---

## Dataset Overview

* **Source:** USAFacts Population & Demographics (Creative Commons Attribution-ShareAlike 4.0)
* **File:** `data/population_usafacts.xlsx`
* **Dimensions:** 121 rows × 53 columns (1900–2020 annual metrics across states and territories)

---

## Repository Structure

```text
Assignment_04_Seaborn_Visualizations/
├── data/
│   └── population_usafacts.xlsx             # Source demographic dataset
├── docs/
│   └── 04_Assignment_Seaborn.pdf            # Exported assignment worksheet report
├── notebooks/
│   └── 04_Assignment_Seaborn.ipynb          # Executed notebook workflow
└── README.md

```
---

## Visualizations & Workflow Summary

* **Data Ingestion:** Loaded the demographic Excel dataset via `pd.read_excel("population_usafacts.xlsx")` to inspect national and state-level historical populations.
* **Data Reshaping (Melt Operation):** Transformed wide-form data into long format using `pop.melt()` for specific states of interest (Ohio, Kentucky, Indiana), preparing an optimal structure for Seaborn's categorical and relational functions.
* **Relational Line Plots (Seaborn):** Utilized `sns.relplot()` with `kind='line'` to visualize long-term population growth trajectories mapped by state (`hue='State'`).
* **Palette Customization:** Enhanced visual aesthetics by applying built-in Seaborn color palettes (`palette='flare'`).
* **Multi-Panel Comparative Subplots:** Created faceted grid subplots (`col='State'`, `col_wrap=3`) to break down individual state trajectories into clean, independent panels.
* **Advanced Formatting & Customization:** Configured `Axes` objects to add descriptive titles, adjust tick intervals, remove scientific notation (`1e7`) on axes via `ticklabel_format(style='plain')`, and rotate tick labels for improved readability.
* **Categorical Bar Plots:** Rendered structured comparison charts using `sns.catplot()` with `kind='bar'` filtered for milestone years (1920, 1970, 2020).
* **Kernel Density Estimation (KDE):** Generated univariate probability distributions using `sns.displot()` with `kind='kde'` to analyze data clustering and population pacing over time for Ohio.
s
---

## How to Run

1. Open **Anaconda Prompt** (or your standard terminal/Command Prompt).

2. Navigate to the assignment directory:
   ```bash
   cd Assignment_04_Seaborn_Visualizations
   ```

3. Launch Jupyter Notebook:
   ```bash
   jupyter notebook
   ```

4. In the browser window that opens automatically, navigate to the `notebooks/` folder and open `04_Assignment_Seaborn.ipynb`.

5. Run all cells sequentially to load the dataset and generate the plots.
