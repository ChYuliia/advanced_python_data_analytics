\# Assignment 02: The Pandas Essentials for Data Analysis



This assignment explores fundamental data wrangling, cleaning, transformation, and statistical aggregation techniques in \*\*pandas\*\* using historical macroeconomic data from the U.S. Bureau of Labor Statistics (BLS). The workflow processes 79 years of monthly Civilian Labor Force metrics (1948–2026), cleans text and footnote artifacts, normalizes units, calculates annual and decennial trends, and exports both tabular serializations and visualizations.



\---



\## Technical Stack \& Environment



\* \*\*Language:\*\* Python 3.9+

\* \*\*Libraries:\*\* `pandas`, `matplotlib`

\* \*\*Environment:\*\* Jupyter Notebook (`.ipynb`)

\* \*\*Reference Curriculum:\*\* CIS 2267 / Murach's Python for Data Analysis (Sinclair Community College)



\---



\## Dataset Overview



\* \*\*Source:\*\* U.S. Bureau of Labor Statistics (BLS) — Unemployment \& Civilian Labor Force Level

\* \*\*File:\*\* `data/CivilianLaborForce.csv` (exported serial backup: `data/CivilianLaborForce.pkl`)

\* \*\*Timespan:\*\* 1948–2026 (79 annual observation records across 12 monthly features)

\* \*\*Scale \& Units:\*\* Original records reported in thousands; converted to actual headcounts ($1\\text{ unit} = 1{,}000\\text{ individuals}$) during preprocessing.



\---



\## Repository Structure



```text

Assignment\_02\_Pandas\_Essentials/

├── data/

│   ├── CivilianLaborForce.csv                  # Source BLS timeseries data

│   └── CivilianLaborForce.pkl                  # Serialized cleaned DataFrame

├── docs/

│   └── 02\_Assignment\_Pandas\_Essentials.pdf    # Exported assignment worksheet report

├── notebooks/

│   └── 02\_Assignment\_Pandas\_Essentials.ipynb  # Executed analysis notebook

└── README.md



\---



\## Workflow \& Analysis Summary



\* \*\*Data Ingestion \& Attribute Inspection:\*\*  

&#x20; Imported `CivilianLaborForce.csv` using `pd.read\_csv()` and inspected dataset characteristics via `.info()`, `.index`, `.columns`, and `.shape` (79 rows × 13 columns).



\* \*\*Regex Data Cleaning \& Type Casting:\*\*  

&#x20; Addressed non-numeric data types across monthly columns caused by BLS footnote annotations (e.g., `(1)`, `(9)`, `(12)`), whitespace, and missing data dashes (`-`). Cleared footnote markers using regex pattern `replace(r'\\(\\d+\\)', '', regex=True)` and converted columns to numeric floats using `pd.to\_numeric(..., errors='coerce')`.



\* \*\*Unit Normalization:\*\*  

&#x20; Scaled all monthly macroeconomic workforce numbers by multiplying by $1{,}000$ to represent actual headcounts instead of values reported in thousands.



\* \*\*Targeted Historical Comparisons:\*\*  

&#x20; Queried historical benchmarks (`Year in (1961, 2021)`) to compute monthly means across annual rows (`axis=1`), demonstrating that the U.S. labor force more than doubled from \*\*70,449,917\*\* in 1961 to \*\*161,212,000\*\* in 2021.



\* \*\*Interactive Query Loop:\*\*  

&#x20; Constructed a dynamic user-input loop with input validation against dataset bounds (`min\_year` to `max\_year`), outputting filtered annual records and calculating corresponding annual workforce averages.



\* \*\*Row-Wise Feature Engineering:\*\*  

&#x20; Engineered an `Annual` feature column by computing the rounded mean across all twelve calendar months (`axis=1`).



\* \*\*Index Configuration \& Serialization:\*\*  

&#x20; Assigned `Year` as the primary DataFrame index using `set\_index('Year', verify\_integrity=True)` and exported the processed data to disk via `.to\_pickle('CivilianLaborForce.pkl')`.



\* \*\*Visualizations \& Decennial Aggregations:\*\*  

&#x20; \* \*\*Longitudinal Timeseries Plot:\*\* Visualized national workforce expansion from 1948 to 2026 scaled in millions (`Annual / 1e6`) using Matplotlib.

&#x20; \* \*\*Decade Grouping \& Summary Statistics:\*\* Reset the index to engineer a `Decade` feature (`(Year // 10) \* 10`), calculated decennial aggregation metrics (`mean`, `median`, `std`), and rendered long-term workforce evolution via a grouped bar chart.



\---



\## How to Run



1\. Open your terminal (Git Bash or Command Prompt) and navigate to the assignment directory:

&#x20;  cd Assignment\_02\_Pandas\_Essentials



2\. Launch Jupyter Notebook:

&#x20;  jupyter notebook notebooks/02\_Assignment\_Pandas\_Essentials.ipynb



3\. Run all cells sequentially to reproduce data cleaning, queries, calculations, and plots.

