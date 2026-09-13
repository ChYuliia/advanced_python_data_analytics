\# Assignment 03: The Pandas Essentials for Data Visualization



This assignment demonstrates foundational and exploratory data visualization techniques using the built-in plotting capabilities of \*\*pandas\*\* (backed by Matplotlib)\[cite: 1]. The analysis evaluates historical US demographic trends across 50 states and jurisdictions from 1900 to 2020 based on USAFacts population data.



\---



\## Technical Stack \& Environment



\* \*\*Language:\*\* Python 3.9+

\* \*\*Libraries:\*\* `pandas`, `openpyxl`, `matplotlib`

\* \*\*Environment:\*\* Jupyter Notebook (`.ipynb`)\[cite: 2]

\* \*\*Reference Curriculum:\*\* CIS 2267 / Murach's Python for Data Analysis (Sinclair Community College)



\---



\## Dataset Overview



\* \*\*Source:\*\* USAFacts Population \& Demographics (Creative Commons Attribution-ShareAlike 4.0)

\* \*\*File:\*\* `data/population\_usafacts.xlsx`

\* \*\*Dimensions:\*\* 121 rows × 53 columns (1900–2020 annual metrics across states and territories)

\* \*\*Indexing:\*\* Timeseries indexed on `Year`



\---



\## Repository Structure



```text

Assignment\_03\_Pandas\_Visualizations/

├── data/

│   └── population\_usafacts.xlsx           # Source demographic dataset

├── docs/

│   └── 03\_Assignment\_Ch3\_Pandas.pdf       # Exported assignment worksheet report

├── notebooks/

│   └── 03\_Assignment\_Pandas.ipynb         # Executed notebook workflow

└── README.md



\---



\## Visualizations \& Workflow Summary



\* \*\*Data Ingestion \& Timeseries Indexing:\*\*  

&#x20; Loaded the demographic Excel dataset via `pd.read\_excel("population\_usafacts.xlsx")` and set the `Year` column as the index with `pop.set\_index('Year')`\[cite: 1, 2].



\* \*\*Default Multi-Series Line Plotting:\*\*  

&#x20; Created an initial baseline chart using `pop.reset\_index().plot()` to inspect full-table series trends across all jurisdictions\[cite: 1, 2].



\* \*\*Targeted Regional Timeseries Comparison:\*\*  

&#x20; Filtered specific Midwestern states using `pop\[\['Ohio', 'Indiana', 'Kentucky']].plot.line()` to generate a readable longitudinal line chart\[cite: 1, 2].



\* \*\*Filtered Discrete Bar Chart:\*\*  

&#x20; Queried post-2000 records using `.query('Year > 2000')` to render recent Ohio population trends via a vertical bar chart (`.Ohio.plot.bar()`)\[cite: 1, 2].



\* \*\*Decennial Modulo Sampling (Horizontal Bar Chart):\*\*  

&#x20; Isolated ten-year census milestones using arithmetic modulo filtering (`Year % 10 == 0`) and rendered historical national totals with a horizontal bar plot (`.Total.plot.barh()`)\[cite: 1, 2].



\* \*\*Kernel Density Estimation (KDE):\*\*  

&#x20; Generated univariate density distributions for Ohio's population using `pop.Ohio.plot.density()` to visualize data clustering over time\[cite: 1, 2].



\* \*\*Proportional Categorical Composition:\*\*  

&#x20; Extracted cross-sectional 2020 counts with `pop.loc\[2020, \['Ohio', 'Indiana', 'Kentucky']]` to display regional distribution using a pie chart (`.plot.pie()`)\[cite: 1, 2].



\* \*\*Multi-Panel Comparative Subplots:\*\*  

&#x20; Produced side-by-side subplots with a 1×3 layout (`subplots=True`, `layout=(1, 3)`), locked value scaling (`sharey=True`), rotated tick labels (`rot=45`), and a custom range (`xlim=(1990, 2020)`) to contrast modern regional growth\[cite: 1, 2].



\---



\## How to Run



1\. Open your terminal (Git Bash or Command Prompt) and navigate to the assignment directory:

&#x20;  cd Assignment\_03\_Pandas\_Visualizations



2\. Launch Jupyter Notebook:

&#x20;  jupyter notebook notebooks/03\_Assignment\_Pandas.ipynb



3\. Run all cells sequentially to load the dataset and generate the plots.

