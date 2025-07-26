# Used Car Price Prediction & Model Comparison

This repository contains an end-to-end machine learning project focused on predicting the selling price of used cars. The analysis includes data cleaning, exploratory data analysis (EDA), feature engineering, and a rigorous comparison of three different regression models.

---

### Project Goal

The objective was to develop a reliable model to predict used car prices based on their features. This project showcases a structured approach to solving a regression problem, from initial data exploration to final model evaluation and selection, keeping business applications in mind.

---

### Methodology

1.  **Data Cleaning & EDA:** The dataset was cleaned by removing duplicates. Exploratory analysis revealed a heavily right-skewed price distribution, which was handled using a log transformation to improve model performance.

2.  **Feature Engineering:** To create more predictive signals for the models, the following features were engineered:
    * **Vehicle Age:** The `year` of manufacture was converted into `vehicle_age`.
    * **Brand Grouping:** Rare car brands (with few listings) were grouped into a single 'Other' category to reduce noise.
    * **Ordinal Encoding:** The `owner` feature was numerically encoded to preserve its natural order (e.g., First Owner < Second Owner).

3.  **Modeling & Evaluation:**
    Three regression models were trained and compared:
    * **Linear Regression (Baseline):** A simple, interpretable model to establish a baseline performance.
    * **Random Forest Regressor:** An ensemble model capable of capturing non-linear relationships.
    * **XGBoost Regressor:** A powerful gradient-boosting model known for high accuracy.

    A **5-fold cross-validation** strategy was used to ensure the performance of each model was robust and generalizable. Models were evaluated on their R-squared (R²) and Root Mean Squared Error (RMSE) scores.

---

### Results & Key Findings

The cross-validation results showed that the simpler **Linear Regression** model provided the best balance of performance and interpretability for this dataset.

| Model             | R² Score (Mean CV) | RMSE (Mean CV, Log Scale) |
| ----------------- | ------------------ | ------------------------- |
| **Linear Regression** | **0.7724** | **0.3897** |
| XGBoost           | 0.7696             | 0.3920                    |
| Random Forest     | 0.7435             | 0.4136                    |

**Key Insights:**
* **Best Model:** While complex models like XGBoost are powerful, the **Linear Regression model was statistically equivalent and slightly better**, making it the most efficient choice. This highlights the importance of not over-engineering a solution.
* **Top Price Drivers:** Feature importance analysis consistently showed that **`vehicle_age`** is the most significant factor in determining a car's price.
* **Data Quality:** The analysis identified the need for robust outlier detection, as some data points (e.g., a car with >800,000 km) were unrealistic.

---

### Repository Contents
* `car_price_analysis.ipynb`: The main Jupyter Notebook containing the full data analysis and modeling workflow.
* `requirements.txt`: A list of required Python libraries to reproduce the environment.
* `output/`: A folder containing the saved model (`.joblib` file) and the cross-validation results (`.csv` and `.json` files).

---

### How to Run
1.  Clone this repository to your local machine.
2.  Install the required libraries using the command: `pip install -r requirements.txt`
3.  Open and run the `car_price_analysis.ipynb` notebook in a Jupyter environment.
