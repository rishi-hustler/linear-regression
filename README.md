# 🏢 Building Energy Efficiency Prediction

### Multi-Model Regression Analysis for Heating & Cooling Loads

This project provides a deep-dive into predictive modeling using the **Energy Efficiency Dataset**. The goal is to analyze how building parameters (like surface area, height, and glazing) affect energy requirements and to compare the performance of different regression algorithms.

## 📊 Dataset Overview

The analysis uses the `ENB2012_data.csv`. It contains 768 samples with 8 features and 2 target variables:

* **Predictors (X):** Relative Compactness, Surface Area, Wall Area, Roof Area, Overall Height, Orientation, Glazing Area, Glazing Area Distribution.
* **Targets (Y):** 1. **Heating Load** (Thermal energy required to heat the building).
2. **Cooling Load** (Thermal energy required to cool the building).

## 🚀 Project Workflow

### 1. Data Preprocessing

* **Column Renaming:** Converted raw labels (X1, X2... Y2) into human-readable features for better interpretability.
* **Feature Scaling:** Applied `StandardScaler` to normalize the data. This is critical for **Ridge** and **Lasso** models to ensure regularization penalties are applied fairly across all features.
* **Train/Test Split:** Utilized an 80/20 split with a fixed `random_state` for reproducible results.

### 2. Exploratory Data Analysis (EDA)

* **Distributions:** Visualized feature spreads using Histograms to identify skewness and outliers.
* **Correlation Mapping:** Generated scatter plots for each feature against the targets to determine which relationships were linear and which required non-linear (tree-based) modeling.

### 3. Models Implemented

The notebook compares five distinct algorithms to find the best fit:

* **Linear Regression:** The baseline Ordinary Least Squares (OLS) model.
* **RidgeCV:** Linear regression with L2 regularization (prevents coefficients from becoming too large).
* **LassoCV:** Linear regression with L1 regularization (can perform feature selection by shrinking coefficients to zero).
* **Decision Tree Regressor:** Captures non-linear relationships by partitioning the data.
* **Random Forest Regressor:** An ensemble method that averages multiple trees to reduce variance and improve generalization.

### 4. Evaluation Metrics

Models are evaluated using:

* **Mean Squared Error (MSE):** Measures the average squared difference between estimated and actual values.
* **R² Score:** Indicates the proportion of variance explained by the model (Goal: closer to 1.0).
* **Residual Analysis:** Visual plots to ensure errors are randomly distributed around zero.

## 🛠️ Installation & Usage

1. **Clone the repository:**
```bash
git clone https://github.com/your-username/energy-efficiency-prediction.git

```


2. **Install dependencies:**
```bash
pip install numpy pandas matplotlib scikit-learn

```


3. **Run the Notebook:**
Open `Linear vs Lasso vs Ridge Regression.ipynb` in Jupyter or Google Colab and ensure `ENB2012_data.csv` is in the same directory.

## 🔍 Key Insights from the Notebook

* **Feature Importance:** Building height and surface area are major drivers of energy load.
* **Regularization:** Lasso and Ridge help stabilize the linear models when features are highly correlated (e.g., Surface Area vs. Wall Area).
* **Non-Linearity:** Tree-based models (Random Forest) generally outperform linear models on this dataset due to complex interactions between glazing and orientation.

## 🧪 Advanced Features

* **Manual Prediction:** Includes a pre-built block to input custom building parameters and get instant load estimates.
* **Binned Confusion Matrix:** A unique approach where continuous regression results are binned into "Low," "Medium," and "High" categories to evaluate classification-style accuracy.

---

### 👨‍💻 Technical Summary

| Library | Purpose |
| --- | --- |
| **Pandas** | Data manipulation and cleaning |
| **Matplotlib** | Data visualization and residual plotting |
| **Scikit-Learn** | Model training, scaling, and evaluation |
