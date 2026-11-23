# Assignment 12: Multiple Linear Regression & Feature Selection (Auto MPG Prediction)

This assignment focuses on building and evaluating an end-to-end multiple linear regression and automated feature selection workflow using Python's `scikit-learn`, `pandas`, and `seaborn` libraries. Based on the Seaborn `mpg` dataset, the workflow covers data extraction via lambda expressions, categorical data cleaning and standardization, missing value handling, one-hot dummy encoding (`pd.get_dummies()`), feature standardization with `StandardScaler`, correlation analysis, iterative feature selection using `SelectKBest` with `mutual_info_regression`, model fitting and performance scoring ($R^2$), and optimal model complexity evaluation.

---

## Technical Stack & Environment

- **Language:** Python 3.9+
- **Libraries:** `pandas`, `NumPy`, `matplotlib`, `seaborn`, `scikit-learn`
- **Environment:** Jupyter Notebook (`.ipynb`) & Reproducible Python Scripts
- **Reference Curriculum:** CIS 2267 / Murach's Python for Data Analysis (Sinclair Community College)

---

## Dataset Overview

- **Source:** Seaborn built-in repository dataset (`sns.load_dataset('mpg')`)
- **Dataset:** `mpg` (398 records, 9 attributes initially; 392 records post-cleaning)
- **Target Variable (Metric):**
  - `mpg`: Fuel efficiency in miles per gallon (continuous float)
- **Predictor Variables (Dimensions & Technical Attributes):**
  - `cylinders`: Number of engine cylinders (discrete numeric)
  - `displacement`: Engine displacement in cubic inches (continuous numeric)
  - `horsepower`: Engine horsepower output (continuous numeric; contained 6 missing values)
  - `weight`: Total vehicle weight in pounds (discrete/continuous numeric)
  - `acceleration`: Time to accelerate from 0 to 60 mph in seconds (continuous numeric)
  - `model_year`: Vehicle manufacture year relative to 1900 (e.g., 70 for 1970)
  - `origin`: Geographical manufacturing origin (`usa`, `japan`, `europe`)
  - `brand`: Isolated vehicle brand/manufacturer extracted from the original `name` attribute

---

## Analytical Methods & Highlights

1. **Feature Extraction & Data Hygiene:**
   - Isolated the manufacturer name from composite vehicle model strings into a dedicated `brand` column using `.apply(lambda x: x['name'].split()[0], axis=1)`.
   - Dropped redundant high-cardinality `name` strings to prevent dimensional inflation.
   - Inspected unique brand tokens and standardized 7 typo variations (`chevy`/`chevroelt` $\rightarrow$ `chevrolet`, `toyouta` $\rightarrow$ `toyota`, `maxda` $\rightarrow$ `mazda`, `vw`/`vokswagen` $\rightarrow$ `volkswagen`, `mercedes-benz` $\rightarrow$ `mercedes`).
   - Filtered out 6 records containing null `horsepower` entries (`.dropna()`), establishing an intact working dataset of 392 records.

2. **Categorical Dummy Encoding:**
   - Isolated discrete categorical features (`origin`, `brand`) into a dedicated feature list.
   - Transformed categorical columns into 33 binary dummy variables via `pd.get_dummies()`.
   - Dropped original object columns and joined dummy arrays back to numeric predictors, producing a structured dataset of 40 columns (`dataDummies`).

3. **Feature Rescaling & Target Correlation Analysis:**
   - Standardized all 6 numeric independent attributes (`cylinders`, `displacement`, `horsepower`, `weight`, `acceleration`, `model_year`) to zero mean and unit variance using `StandardScaler`.
   - Preserved unscaled dummy indicators and the dependent variable (`mpg`) to maintain target interpretability.
   - Computed Pearson correlation coefficients against `mpg`, identifying strong inverse relationships with physical engine mass (`weight`: $r = -0.832$; `displacement`: $r = -0.805$; `horsepower`: $r = -0.778$) and positive relationships with technological vintage (`model_year`: $r = 0.581$).

4. **Data Partitioning & Automated Feature Selection:**
   - Split the complete dataset into an 80% training partition (313 samples) and a 20% validation partition (79 samples) with a deterministic seed (`random_state=20`).
   - Iterated over dynamic feature set sizes $k \in [1, 39]$ using `SelectKBest` with non-parametric `mutual_info_regression`.
   - Transformed both training and test feature matrices at each step without target leakage.
   - Trained an Ordinary Least Squares `LinearRegression` model per feature subset and recorded coefficient of determination ($R^2$) scores across both train and test partitions.

5. **Performance Tracking & Complexity Trade-off:**
   - Structured evaluated performance metrics into a dedicated DataFrame with an adjusted 1-based feature counter (`num_features`).
   - Visualized comparative test vs. train learning curves with Pandas/Matplotlib line plots.
   - Observed an inflection point at **5 features**, where test $R^2$ performance surges from ~0.74 to over **0.84** and train $R^2$ reaches **0.80**, followed by a plateau where additional features introduce diminishing returns and model complexity.

---

## Repository Structure

```text
Assignment_12_Multiple_Regression/
├── docs/
│   └── 12_Assignment_Multiple_Regression.pdf    # Exported assignment worksheet report
├── notebooks/
│   └── 12_Assignment_Multiple_Regression.ipynb  # Executed Jupyter notebook workflow
└── README.md
```
---

### Workflow Summary & Key Learnings

- **Data Ingestion & Integrity Inspection:** Loaded the Seaborn `mpg` dataset containing 398 records and 9 features, inspected the DataFrame structure using `data.head()` and `data.info()`, and identified 6 missing values in the `horsepower` column.

- **String Extraction & Data Cleaning:** Extracted the vehicle brand from the `name` column using `data.apply(lambda x: x['name'].split()[0], axis=1)`, dropped the original `name` column, corrected 7 misspelled brand names (`chevy`/`chevroelt` -> `chevrolet`, `toyouta` -> `toyota`, `maxda` -> `mazda`, `vw`/`vokswagen` -> `volkswagen`, `mercedes-benz` -> `mercedes`), and removed missing values via `.dropna()` to establish a clean dataset of 392 records.

- **Categorical Dummy Encoding:** Stored categorical columns (`origin`, `brand`) in a list, transformed them into 33 dummy variables using `pd.get_dummies()`, dropped the original categorical features, and joined the dummy variables back to create `dataDummies` with 40 total columns.

- **Feature Standardization & Correlation Analysis:** Standardized all 6 numeric predictors (`cylinders`, `displacement`, `horsepower`, `weight`, `acceleration`, `model_year`) using `StandardScaler` while preserving `mpg` and dummy variables, then computed Pearson correlations with `mpg` sorted in descending order to identify the strongest positive and negative linear relationships.

- **Dataset Partitioning & Reproducibility:** Partitioned the preprocessed `dataDummies` into an 80% training set and a 20% testing set using `train_test_split(dataDummies, test_size=0.2, random_state=20)`.

- **Feature Selection & Iterative Modeling:** Implemented a `for` loop testing feature subsets from 1 to 38 variables using `SelectKBest(score_func=mutual_info_regression, k=i)`, trained a `LinearRegression` model at each iteration, and recorded the R2 scores for both training and testing datasets.

- **Performance Tracking & Complexity Trade-off:** Assembled the scores into a DataFrame with an adjusted 1-based index (`num_features`) and generated a line plot using `df.plot(x='num_features', y=['test_scores', 'train_scores'])`, identifying an inflection point at **5 features** where the test score jumps to >0.84 before plateauing.

---

### How to Run

1. Open **Anaconda Prompt** (or your standard terminal/Command Prompt).

2. Navigate to the assignment directory:
   ```bash
   cd Assignment_12_Multiple_Regression
   ```
3. Launch Jupyter Notebook:
   ```bash
   jupyter notebook
   ```
4. In the browser window that opens automatically, navigate to the `notebooks/` folder and open `12_Assignment_Multiple_Regression.ipynb`.
   
5. Run all cells sequentially to load and clean the dataset, generate dummy variables, scale numeric features, perform iterative feature selection with mutual_info_regression, and evaluate the $R^2$ performance curves.  
