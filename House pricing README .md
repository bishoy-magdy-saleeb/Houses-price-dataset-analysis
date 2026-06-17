# 🏠 House Price Prediction — Exploratory Data Analysis & Feature Engineering

A data science project that explores the classic [Kaggle House Prices dataset](https://www.kaggle.com/competitions/house-prices-advanced-regression-techniques) to predict residential property sale prices using exploratory analysis and feature engineering techniques.

---

## 📋 Project Description

This notebook walks through the full pre-modeling pipeline for a house price prediction task. It covers loading and inspecting the raw data, handling missing values, dropping low-signal features, engineering new predictive features, and analyzing correlations with the target variable (`SalePrice`).

The goal is to transform a messy, high-dimensional real estate dataset into a clean, feature-rich table ready for regression modeling.

---

## 📁 Project Structure

```
├── House_pricing.ipynb   # Main analysis notebook
├── train.csv             # Training dataset (from Kaggle)
└── README.md             # Project documentation
```

---

## 🔍 Notebook Walkthrough

### 1. Data Loading & Initial Inspection
- Loads `train.csv` into a Pandas DataFrame
- Previews data with `.head()`, `.tail()`, `.info()`, and `.describe()`
- Checks dataset dimensions and sets `Id` as the index

### 2. Missing Value Analysis
- Uses `missingno` to visualize the missing data matrix and bar chart
- Identifies columns with high rates of missingness

### 3. Data Cleaning
- Drops irrelevant or heavily missing columns: `PoolQC`, `MiscFeature`, `Alley`, `Fence`, `Street`, `Utilities`, `Condition2`, `RoofMatl`, `Heating`, `LowQualFinSF`, `3SsnPorch`, `ScreenPorch`, `PoolArea`, `MiscVal`
- Imputes missing **numerical** values with column medians
- Imputes missing **categorical** values with `'None'`

### 4. Feature Engineering
New features created to capture composite information:

| Feature | Description |
|---|---|
| `TotalSF` | Total square footage (basement + 1st floor + 2nd floor) |
| `TotalBath` | Weighted bathroom count (full + 0.5 × half baths, above and below grade) |
| `GarageQualCap` | Garage quality score × number of garage car spaces |
| `Age` | Years since last remodel (relative to 2010) |
| `HouseAge` | Years since original construction (relative to 2010) |
| `GarageAge` | Years since garage was built (relative to 2010) |

### 5. Correlation Analysis
- Computes Pearson correlations of all numeric features with `SalePrice`
- Prints the top 10 most correlated features
- Plots a horizontal bar chart of the top 8 features

---

## 🛠️ Requirements

```bash
pip install pandas numpy matplotlib missingno
```

| Library | Purpose |
|---|---|
| `pandas` | Data loading and manipulation |
| `numpy` | Numerical operations |
| `matplotlib` | Plotting |
| `missingno` | Missing data visualization |

---

## 🚀 Getting Started

1. Clone this repository
2. Download `train.csv` from the [Kaggle competition page](https://www.kaggle.com/competitions/house-prices-advanced-regression-techniques/data) and place it in the project root
3. Install dependencies: `pip install pandas numpy matplotlib missingno`
4. Open and run `House_pricing.ipynb` in Jupyter Notebook or JupyterLab

---

## 📊 Dataset

The dataset is sourced from the **Kaggle House Prices: Advanced Regression Techniques** competition. It contains 79 explanatory variables describing almost every aspect of residential homes in Ames, Iowa.

- **Target variable:** `SalePrice` — the sale price of each home in USD
- **Training set:** 1,460 records

---

## 🔮 Next Steps

- Apply one-hot encoding or label encoding to categorical features
- Train regression models (Linear Regression, Ridge, Lasso, XGBoost, etc.)
- Evaluate performance using RMSE on a validation split
- Submit predictions to Kaggle

---

## 📄 License

This project is for educational purposes. The dataset is provided by Kaggle under their competition terms.
