# Retail Sales Dataset — Exploratory Data Analysis (EDA)

Exploratory data analysis of a 1,000-row retail transactions dataset, aimed at uncovering
sales trends, category performance, and customer behaviour patterns to support business
decisions.

## 📁 Project files

| File | Description |
|---|---|
| `Retail_Sales_EDA.ipynb` | Main analysis notebook (Python / Jupyter) |
| `retail_sales_dataset.csv` | Source data (must sit in the same folder as the notebook) |

## 🎯 Business questions answered

1. What does the dataset look like, and is it suitable for analysis?
2. What are the sales and revenue trends over time?
3. Which product categories generate the most revenue and sales volume?
4. How do purchasing patterns differ by gender and age?
5. What factors are most strongly associated with transaction value?
6. What recommendations can management act on?

## 🧰 Tech stack

- Python 3
- pandas, numpy
- matplotlib, seaborn
- Jupyter Notebook

## ▶️ How to run

```bash
pip install pandas numpy matplotlib seaborn jupyter
jupyter notebook Retail_Sales_EDA.ipynb
```

Make sure `retail_sales_dataset.csv` is in the same directory as the notebook — the first
cell reads it with a relative path.

## 🗂️ Dataset schema

| Column | Type | Notes |
|---|---|---|
| Transaction ID | int | Unique per row |
| Date | date | Nov 2023 – Jan 2024 |
| Customer ID | string | Each customer appears only once (no repeat-purchase data) |
| Gender | string | Male / Female |
| Age | int | 18–64 |
| Product Category | string | Beauty, Clothing, Electronics |
| Quantity | int | Units purchased (1–4) |
| Price per Unit | int | Unit price ($) |
| Total Amount | int | `Quantity × Price per Unit` |

## 🔍 Notebook structure

1. **Data Understanding & Quality Check** – shape, dtypes, missing values, duplicates,
   uniqueness.
2. **Data Preparation** – parses `Date`, derives `Year`/`Month`/`Quarter`/`Day_of_Week`,
   and verifies `Total Amount = Quantity × Price per Unit`.
3. **Descriptive Statistics** – mean, median, mode, std for all numeric columns.
4. **Univariate Analysis** – distributions of Age, Total Amount, Gender, Category,
   Quantity.
5. **Time-Series Analysis** – monthly and quarterly revenue trends.
6. **Product Category Analysis** – revenue, units sold, and average order value by
   category.
7. **Customer Behaviour Analysis** – breakdowns by gender and by age group.
8. **Product × Gender Analysis** – category preference split by gender.
9. **Correlation & Relationship Analysis** – correlation matrix and scatter plots against
   `Total Amount`.
10. **Age Group × Category Analysis** – pivot table/heatmap of average order value.
11. **Key Business Metrics** – headline KPIs (total revenue, transactions, units, etc.).
12. **Outlier Review** – IQR-based check on `Total Amount`.
13. **Key Observations & Business Recommendations** – summary and next steps.

## 📊 Key findings

- **Data quality:** No missing values, no duplicates, 1,000 clean rows; `Total Amount`
  matches `Quantity × Price per Unit` for every transaction.
- **Category performance:** Fairly balanced — Electronics ($156,905), Clothing
  ($155,580), and Beauty ($143,515) are all close. Beauty has the fewest transactions but
  the highest average order value.
- **Gender:** Has almost no effect on spending — revenue and average transaction value
  are nearly identical between Male and Female customers.
- **Price vs. quantity:** `Price per Unit` correlates strongly with `Total Amount`
  (r = 0.85); `Quantity` is a much weaker driver (r = 0.37).
- **Age × category interaction:** The most actionable pattern in the data — 25–34
  year‑olds spend the most on Clothing, 35–44 on Beauty, and 55–64 on Electronics. This
  pattern is invisible when age and category are analyzed separately.
- **Seasonality:** Revenue fluctuates month to month with no clear trend (May 2023
  highest, September 2023 lowest); the swing between the best and worst quarter is only
  ~24%, and there's just one year of data, so a seasonal plan is premature.
- **Outliers:** None — the IQR upper threshold ($2,160) exceeds the maximum transaction
  value in the data ($2,000).

## 💡 Business recommendations

1. Target promotions by **age group + category combination**, not age alone (25–34 →
   Clothing, 35–44 → Beauty, 55–64 → Electronics).
2. Favor **price/premium strategies over quantity-based deals**, since price drives
   revenue far more than quantity.
3. Investigate why **Beauty has fewer transactions** rather than discounting it — its
   high average order value is worth protecting; grow the customer base instead (samples,
   first-purchase offers).
4. **Hold off on committing budget to a seasonal plan** around May/September until a
   second year of data confirms the pattern.

## ⚠️ Limitations

- Every `Customer ID` appears only once, so repeat-purchase, retention, or loyalty
  analysis isn't possible with this dataset.
- Only one year of data — any seasonal read should be treated as provisional.

## 🔜 Next steps

1. Add product name/SKU, store location, discount, and cost data to move from revenue to
   actual profitability.
2. Build a live dashboard tracking revenue, transactions, units sold, average transaction
   value, category performance, and monthly trend.
3. Once product-level and repeat-customer data exist, run proper basket analysis and
   customer segmentation.
