# Level 1 - Task 3: Data Cleaning

This project focuses on cleaning and validating a customer churn dataset before it is used for analysis or modeling.

## Project Objective
The goal is to transform a messy raw dataset into a structured, analysis-ready dataset by handling:
- duplicate rows
- missing values
- inconsistent text formatting
- invalid date values
- out-of-range numeric values
- incorrect data types

## Files in this folder
- `Data Cleaning.ipynb` — Jupyter notebook containing the full cleaning workflow and validation steps
- `bank_churn_dirty.csv` — original raw dataset with data quality issues
- `bank_churn_cleaned.csv` — cleaned dataset produced by the notebook

## Summary of the cleaning process
The notebook performs the following steps:
1. Loads the raw dataset
2. Assesses quality and identifies issues
3. Reviews missing values and duplicate records
4. Removes exact duplicate rows
5. Standardizes text fields such as names and cities
6. Parses and standardizes date values from multiple formats
7. Detects and corrects invalid age, credit score, and balance values
8. Imputes missing numeric values using median-based strategies where appropriate
9. Converts data types to match the expected schema
10. Validates the final quality of the dataset

## Quality improvements observed
The notebook reports the following before-and-after results:
- Row count: 10,150 -> 10,001
- Duplicate rows: 149 -> 0
- Null values: 608 -> 603
- Correct dtypes: 6/8 -> 8/8
- Placeholder/invalid values: 0 -> 0

These results show that the dataset was cleaned effectively and became more consistent for analysis.

## Notes
- This is a learning-focused data-cleaning exercise for churn analysis.
- The notebook intentionally keeps some missing values where they represent legitimate business conditions, such as missing customer IDs or emails.
- The cleaned output is saved as `bank_churn_cleaned.csv`.

## Suggested next steps
- Explore the cleaned dataset with summary statistics
- Visualize churn behavior by customer segment
- Build a predictive model using the cleaned features

## Author
Project prepared as part of the OIBSIP Data Analytics portfolio tasks.
