# Assignment 11: Machine Learning & Linear Regression (Diamonds Price Prediction)

This assignment focuses on building and evaluating a simple linear regression workflow using Python's `scikit-learn` and `seaborn` libraries. Based on the Seaborn `diamonds` dataset, the analytical workflow covers correlation matrix evaluation using condensed heatmaps, feature selection, train/test dataset partitioning (`train_test_split`), model fitting and performance scoring ($R^2$), array-to-DataFrame prediction structuring, data reshaping with `.melt()`, and regression line visualization.

---

## Technical Stack & Environment

- **Language:** Python 3.9+
- **Libraries:** `pandas`, `NumPy`, `matplotlib`, `seaborn`, `scikit-learn`
- **Environment:** Jupyter Notebook (`.ipynb`) & Reproducible Python Scripts
- **Reference Curriculum:** CIS 2267 / Murach's Python for Data Analysis (Sinclair Community College)

---

## Dataset Overview

- **Source:** Seaborn built-in library dataset (`sns.load_dataset('diamonds')`)
- **Dataset:** `diamonds` (53,940 records, 10 attributes)
- **Target Variable (Metric):**
  - `price`: Price in US dollars ($326–$18,823)
- **Feature Variables (Dimensions & Physical Attributes):**
  - `carat`: Weight of the diamond (0.2–5.01 ct)
  - `cut`: Cut quality (Fair, Good, Very Good, Premium, Ideal)
  - `color`: Diamond color grade from J (worst) to D (best)
  - `clarity`: Clarity measurement (I1, SI2, SI1, VS2, VS1, VVS2, VVS1, IF)
  - `x`, `y`, `z`: Diamond dimensions (length, width, depth in mm)
  - `depth`: Total depth percentage (`z / mean(x, y) = 2 * z / (x + y)`)
  - `table`: Width of top of diamond relative to widest point

---

## Analytical Methods & Highlights

1. **Correlation Matrix & Condensed Heatmap:**
   - Computing pairwise linear correlations across numeric variables against `price`.
   - Visualizing correlations with a condensed, sorted Seaborn heatmap formatted to 3 decimal places without a colorbar.
   - Identifying `carat` as the strongest predictive feature ($r \approx 0.922$).

2. **Data Partitioning (`train_test_split`):**
   - Splitting feature (`carat`) and target (`price`) into 70% training and 30% testing subsets with fixed random state (`random_state=42`) for reproducibility.

3. **Model Architecture & Performance Evaluation:**
   - Initializing and fitting an Ordinary Least Squares `LinearRegression` model on training data.
   - Scoring goodness-of-fit via the coefficient of determination on unseen test data ($R^2 \approx 0.849$).

4. **Prediction Transformation & Alignment:**
   - Generating price predictions from test features and storing results in a pandas DataFrame (`price_predicted`).
   - Merging predicted prices with test features and actual prices using aligned index resets (`.reset_index(drop=True)`).

5. **Data Reshaping & Model Visualization:**
   - Transforming wide tabular predictions into long-form format using `pd.melt()` with `price_type` and `price_value`.
   - Plotting the regression trend line against actual price scatter across carat weights using `sns.lineplot()` with disabled confidence intervals (`errorbar=None`).

---

## Repository Structure

```text
Assignment_11_Linear_Regression/
├── docs/
│   ├── Assignment_Guide.pdf                   # Course assignment requirements and tasks
│   └── 11_Assignment_Linear_Regression.pdf    # Exported assignment worksheet report
├── notebooks/
│   └── 11_Assignment_Linear_Regression.ipynb  # Executed Jupyter notebook workflow
└── README.md
```
---

### Workflow Summary & Key Learnings

- **Data Inspection & Integrity:** Loaded the Seaborn `diamonds` dataset containing 53,940 records and 10 features, inspected the DataFrame structure using `.head()` and confirmed column attributes.

- **Exploratory Correlation Analysis:** Filtered numerical features explicitly (`carat`, `depth`, `table`, `price`, `x`, `y`, `z`) to compute linear correlations with the target variable (`price`) using `data[['carat','depth','table','price','x','y','z']].corr()[['price']]`, sorted results in descending order, and rendered a condensed Seaborn heatmap annotated to 3 decimal places without a colorbar to isolate `carat` ($r \approx 0.922$) as the strongest predictor.

- **Dataset Partitioning & Reproducibility:** Separated the selected predictor (`carat`) and target (`price`), then partitioned them into a 70% training set and a 30% testing set using `train_test_split(..., test_size=0.3, random_state=42)`.

- **Model Fitting & Goodness-of-Fit Evaluation:** Initialized and trained an Ordinary Least Squares `LinearRegression` model from `scikit-learn` on the training subset, followed by calculating the coefficient of determination on unseen test data ($R^2 \approx 0.849$) via `.score(x_test, y_test)`.

- **Prediction Formatting & Data Alignment:** Generated target predictions via `.predict(x_test)`, wrapped the resulting NumPy array into a structured DataFrame (`price_predicted`), and merged it with `x_test` and `y_test` using `.reset_index(drop=True)` to prevent NaN mismatches during index alignment.

- **Data Reshaping & Regression Visualization:** Restructured wide-format data into a tidy long-form representation using `pd.melt(..., id_vars=['carat'], value_vars=['price', 'price_predicted'])` and visualized the fitted regression line against actual diamond prices across carat weights using `sns.lineplot(..., errorbar=None)`.

---

### How to Run

1. Open **Anaconda Prompt** (or your standard terminal/Command Prompt).

2. Navigate to the assignment directory:
   ```bash
   cd Assignment_11_Linear_Regression
   ```
3. Launch Jupyter Notebook:
   ```bash
   jupyter notebook
   ```
4. In the browser window that opens automatically, navigate to the `notebooks/` folder and open `11_Assignment_Linear_Regression.ipynb`.
   
5. Run all cells sequentially to load the dataset, compute the correlation heatmap, train the linear regression model, and visualize the predicted versus actual regression line.   
