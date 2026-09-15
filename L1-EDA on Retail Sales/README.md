# Retail Sales — Exploratory Data Analysis

Oasis Infobyte (OIBSIP) Level 1 task: exploratory analysis of a retail sales dataset to describe data quality, sales over time, category mix, customer behaviour, and practical recommendations.

## Contents

| File | Description |
| --- | --- |
| `retail_sales_dataset.csv` | Source data (1,000 transactions, 9 columns) |
| `Retail_Sales_EDA.ipynb` | Analysis notebook (pandas, matplotlib, seaborn) |

## Dataset

Each row is one transaction. Columns:

- `Transaction ID`, `Date`, `Customer ID`
- `Gender`, `Age`
- `Product Category` (Beauty, Clothing, Electronics)
- `Quantity`, `Price per Unit`, `Total Amount`

Coverage is 1 January 2023 through 1 January 2024. There are no missing values or duplicate transaction IDs. `Total Amount` matches `Quantity × Price per Unit` on every row. Each `Customer ID` appears once, so repeat purchase and loyalty cannot be measured from this file.

## Setup

Python 3.10+ is enough. From this folder:

```bash
python -m venv .venv
.venv\Scripts\activate
pip install pandas matplotlib seaborn jupyter
jupyter notebook Retail_Sales_EDA.ipynb
```

On macOS or Linux, activate with `source .venv/bin/activate`.

The notebook reads `retail_sales_dataset.csv` from the same directory. Keep both files together when you run it.

## Notebook outline

1. Data understanding and quality checks  
2. Descriptive statistics (mean, median, mode, standard deviation)  
3. Univariate distributions  
4. Time-series (monthly and quarterly revenue)  
5. Product category performance  
6. Customer behaviour (gender, age group)  
7. Category × gender and correlation  
8. Age group × category average order value  
9. Key metrics, outlier review, observations, and recommendations  

Two transactions fall on 1 January 2024. Treat that month as incomplete; do not read it as a demand drop.

## Business questions

1. Is the dataset suitable for analysis?  
2. How do sales and revenue move over time?  
3. Which product categories drive revenue and volume?  
4. How do patterns differ by gender and age?  
5. What is most strongly associated with transaction value?  
6. What should management take from the findings?
