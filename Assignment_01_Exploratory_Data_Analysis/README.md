\# Assignment 01: Introduction to Python for Data Analysis



This assignment reviews foundational Python programming concepts, interactive user-input control loops, custom statistical functions, and structured markdown documentation. It establishes core scripting competencies required for subsequent data analytics coursework based on Murach's Python curriculum.



\---



\## Technical Stack \& Environment



\* \*\*Language:\*\* Python 3.9+

\* \*\*Environment:\*\* Jupyter Notebook (`.ipynb`)

\* \*\*Reference Curriculum:\*\* CIS 2267 / Murach's Python for Data Analysis (Sinclair Community College)



\---



\## Repository Structure



```text

Assignment\_01\_Python\_Review/

├── docs/

│   └── 01\_Assignment\_Introduction\_to\_Python.pdf    # Exported assignment worksheet report

├── notebooks/

│   └── 01\_Assignment\_Introduction\_to\_Python.ipynb  # Executed assignment notebook

└── README.md



\---



\## Workflow \& Analysis Summary



\* \*\*Interactive Menu \& Control Flow:\*\*  

&#x20; Implemented a continuous `while` loop paired with a custom `display\_menu()` function to present users with interactive options (Enter a value, Display statistics, Exit), handling termination seamlessly upon choice `3`.



\* \*\*Custom Statistical Aggregation Function:\*\*  

&#x20; Developed a robust `stats()` function that processes an input list of numeric values, safely handles division-by-zero edge cases for empty sets, and returns a 4-element tuple containing minimum, maximum, total, and average values formatted to one decimal place (`{:.1f}`).



\* \*\*Data Analysis Process Summary:\*\*  

&#x20; Authored a structured Markdown documentation guide detailing pre-analysis planning (goals and target audience) and outlining the five core phases of a data analytics project: Data Ingestion, Cleaning, Preparation, Analysis, and Visualization, complete with external resource references.



\---



\## How to Run



1\. Open your terminal (Git Bash or Command Prompt) and navigate to the assignment directory:

&#x20;  cd Assignment\_01\_Python\_Review



2\. Launch Jupyter Notebook:

&#x20;  jupyter notebook notebooks/01\_Assignment\_Introduction\_to\_Python.ipynb



3\. Run all cells sequentially to interact with the statistics menu program and review the markdown process summary.

