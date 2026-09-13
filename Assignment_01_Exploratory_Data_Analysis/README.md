# Assignment 01: Introduction to Python for Data Analysis

This assignment reviews foundational Python programming concepts, interactive user-input control loops, custom statistical functions, and structured markdown documentation. It establishes core scripting competencies required for subsequent data analytics coursework based on Murach's Python curriculum.

---

## Technical Stack & Environment

* **Language:** Python 3.9+
* **Environment:** Jupyter Notebook (`.ipynb`)
* **Reference Curriculum:** CIS 2267 / Murach's Python for Data Analysis (Sinclair Community College)

---

## Repository Structure

```text
Assignment_01_Exploratory_Data_Analysis/
├── docs/
│   └── 01_Assignment_Introduction_to_Python.pdf    # Exported assignment worksheet report
├── notebooks/
│   └── 01_Assignment_Introduction_to_Python.ipynb  # Executed assignment notebook
└── README.md
```
---

## Workflow & Analysis Summary

* **Interactive Menu & Control Flow:**  
  Implemented a continuous `while` loop paired with a custom `display_menu()` function to present users with interactive options (Enter a value, Display statistics, Exit), handling termination seamlessly upon choice `3`.

* **Custom Statistical Aggregation Function:**  
  Developed a robust `stats()` function that processes an input list of numeric values, safely handles division-by-zero edge cases for empty sets, and returns a 4-element tuple containing minimum, maximum, total, and average values formatted to one decimal place (`{:.1f}`).

* **Data Analysis Process Summary:**  
  Authored a structured Markdown documentation guide detailing pre-analysis planning (goals and target audience) and outlining the five core phases of a data analytics project: Data Ingestion, Cleaning, Preparation, Analysis, and Visualization, complete with external resource references.

--- 

## How to Run

1. Open **Anaconda Prompt** (or your standard terminal/Command Prompt).

2. Navigate to the project directory:
   ```bash
   cd path_to/Assignment_01_Exploratory_Data_Analysis   
   ```
3. Launch Jupyter Notebook:
   ```bash
   jupyter notebook
   ```  
4. In the browser window that opens automatically, navigate to the `notebooks/` folder and open `01_Assignment_Introduction_to_Python.ipynb`.
   
5. Run all cells sequentially to review the code and documentation.
