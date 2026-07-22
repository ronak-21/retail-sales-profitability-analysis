# retail-sales-profitability-analysis
End-to-end retail sales and profitability analysis using Python and Google Colab, exploring discount impact, product performance, regional profitability, delivery efficiency, and holiday sales trends.


# 🛒 Retail Sales & Profitability Analysis

An end-to-end retail analytics project using Python and Google Colab to analyze sales performance, profitability, discounting behavior, delivery operations, regional performance, and holiday effects using the Superstore dataset.

---

## 📌 Project Overview

This project performs a comprehensive analysis of retail sales and profitability using transactional data from a US-based Superstore dataset.

The analysis focuses on identifying the key business factors that influence profitability, including:

* Discounting strategy
* Product category and sub-category performance
* Sales and profit relationships
* Delivery performance
* Regional profitability
* Holiday versus non-holiday performance
* Loss-making transactions
* High-performing products and segments

The project combines **data cleaning, feature engineering, exploratory data analysis, statistical analysis, data visualization, and business interpretation** to generate actionable insights for management.

---

## 🎯 Business Problem

Retail businesses can generate high sales revenue while still experiencing low profitability due to excessive discounting, poor product pricing, and underperforming product categories.

This project aims to answer the following business questions:

* Which products and categories generate the highest profit margins?
* How does discounting affect profitability?
* Which sub-categories are financially weak?
* Which regions and states generate the highest profits?
* How efficiently are orders being delivered?
* Do holidays significantly affect sales and profit?
* Which business strategies can help increase profit and reduce losses?

---

## 📊 Dataset

The project uses the **Superstore retail dataset**, containing **9,994 transaction records** covering sales from **2014 to 2017**.

### Original Dataset Features

| Feature       | Description                     |
| ------------- | ------------------------------- |
| Row ID        | Unique row identifier           |
| Order ID      | Unique order identifier         |
| Order Date    | Date when the order was placed  |
| Ship Date     | Date when the order was shipped |
| Ship Mode     | Shipping method                 |
| Customer ID   | Unique customer identifier      |
| Customer Name | Customer name                   |
| Segment       | Customer segment                |
| Country       | Country                         |
| City          | City                            |
| State         | State                           |
| Postal Code   | Postal code                     |
| Region        | Sales region                    |
| Product ID    | Product identifier              |
| Category      | Product category                |
| Sub-Category  | Product sub-category            |
| Product Name  | Product name                    |
| Sales         | Sales revenue                   |
| Quantity      | Quantity sold                   |
| Discount      | Discount percentage             |
| Profit        | Profit generated                |

A separate US holiday dataset was merged with the retail data to analyze the impact of holidays on sales and profitability.

---

## 🧰 Tools & Technologies

### Programming Language

* Python

### Development Environment

* Google Colab
* Jupyter Notebook

### Python Libraries

* Pandas
* NumPy
* Matplotlib
* Seaborn
* Plotly

### Analytics Techniques

* Data Cleaning
* Feature Engineering
* Exploratory Data Analysis
* Aggregation and Grouping
* Correlation Analysis
* Business KPI Analysis
* Comparative Analysis
* Data Visualization
* Business Recommendations

---

## 🔄 Project Workflow

```text
Data Loading
     ↓
Data Cleaning
     ↓
Date Transformation
     ↓
Feature Engineering
     ↓
Exploratory Data Analysis
     ↓
Sales & Profitability Analysis
     ↓
Discount Impact Analysis
     ↓
Delivery Performance Analysis
     ↓
Regional Profitability Analysis
     ↓
Holiday Data Integration
     ↓
Visualization
     ↓
Business Insights
     ↓
Management Recommendations
```

---

# 🧹 1. Data Preparation

The dataset was loaded into Pandas and inspected using:

* `head()`
* `tail()`
* `info()`
* `describe()`

### Dataset Summary

* **Total rows:** 9,994
* **Total original columns:** 21
* **Time period:** 2014–2017
* **Missing values:** None found
* **Duplicate rows:** None found

The `Order Date` and `Ship Date` columns were converted to datetime format for time-based analysis.

---

# ⚙️ 2. Feature Engineering

Several new analytical features were created.

### 📅 OrderYear

Extracted the year from the order date.

### 📅 OrderMonth

Extracted the month from the order date.

### 📅 OrderWeekday

Extracted the day of the week from the order date.

### 👤 TotalOrdersPerCustomer

Calculated the number of distinct orders placed by each customer.

### 🚚 DeliveryTime

Calculated the number of days between order date and ship date.

```text
DeliveryTime = Ship Date - Order Date
```

### 💰 ProfitMargin

Calculated the profit margin for each transaction.

```text
ProfitMargin = Profit / Sales
```

### ⚠️ LossFlag

Created a Boolean flag to identify loss-making transactions.

```text
LossFlag = True when Profit < 0
```

### 🚚 DeliveryLabel

Orders were categorized into:

* Fast
* Normal
* Slow

Distribution:

| Delivery Label | Orders |
| -------------- | -----: |
| Normal         |  5,948 |
| Fast           |  2,222 |
| Slow           |  1,824 |

---

# 📦 3. Data Quality Analysis

The dataset was checked for:

* Duplicate rows
* Missing values
* Data type consistency

### Results

* **Rows before cleaning:** 9,994
* **Rows after duplicate removal:** 9,994
* **Duplicates removed:** 0
* **Missing values:** None

The dataset was therefore considered clean and ready for analysis.

---

# 🚚 4. Delivery Performance Analysis

The average delivery time across all orders was:

```text
3.96 days
```

### Average Delivery Time by Category

| Category        | Average Delivery Time |
| --------------- | --------------------: |
| Furniture       |             3.92 days |
| Office Supplies |             3.98 days |
| Technology      |             3.92 days |

**Office Supplies** had the highest average delivery time at approximately **3.98 days**.

However, the difference between categories was very small, suggesting that product category has limited practical influence on delivery time.

---

# 📦 5. Most Frequently Sold Sub-Categories

The three most frequently sold sub-categories were:

1. **Binders**
2. **Paper**
3. **Furnishings**

These categories had relatively low average unit prices compared with the overall dataset average.

### Average Unit Price

| Sub-Category    | Average Unit Price |
| --------------- | -----------------: |
| Binders         |             $34.05 |
| Paper           |             $15.16 |
| Furnishings     |             $25.74 |
| Dataset Average |             $60.66 |

This suggests that lower-priced products are purchased more frequently and across a larger number of transactions.

---

# ⚠️ 6. High Discount and Loss Analysis

A major profitability risk was identified in heavily discounted transactions.

### Key Finding

**856 orders** had:

```text
Discount > 50%
AND
Negative Profit
```

This highlights excessive discounting as a major contributor to financial losses.

---

# 💰 7. Highest Profit Margin Transactions

The maximum observed transaction-level profit margin was:

```text
50%
```

A total of **140 orders** were tied at this maximum margin.

All of these orders had:

```text
Discount = 0%
```

The five highest-value orders among these tied transactions were selected using absolute profit as a secondary ranking criterion.

### Key Pattern

* 5 out of 5 top-margin transactions had zero discount.
* 4 out of 5 belonged to the Office Supplies category.

This reinforces the negative relationship between discounting and profitability.

---

# 📈 8. Correlation Analysis

A correlation matrix was created for:

* Sales
* Quantity
* Discount
* Profit
* Profit Margin

### Key Correlations

| Variable Relationship    | Correlation |
| ------------------------ | ----------: |
| Discount vs ProfitMargin |  **-0.864** |
| Sales vs Profit          |   **0.479** |
| Sales vs ProfitMargin    |   **0.003** |
| Discount vs Profit       |  **-0.219** |

### Main Insight

The strongest relationship in the dataset was:

```text
Discount vs ProfitMargin = -0.864
```

This represents a strong negative relationship.

As discounts increase, profit margins tend to decrease substantially.

The analysis also showed that:

> High sales volume does not necessarily result in high profitability.

Sales and profit had a moderate positive relationship, but sales and profit margin were almost completely unrelated.

Therefore, businesses should evaluate **profitability efficiency**, not just revenue volume.

---

# 📉 9. Lowest Profit Margin Sub-Category

The analysis compared two different margin calculation methods:

### Mean of Individual Transaction Margins

```text
Lowest: Binders
Margin: -19.96%
```

### Aggregate Margin

```text
Total Profit / Total Sales
```

Using the more financially meaningful aggregate approach:

### Lowest-performing sub-category:

## ❌ Tables

```text
Aggregate Profit Margin: -8.56%
```

### Evidence

* **203 of 319 Table orders were loss-making**
* Average discount: **26.1%**
* Dataset average discount: **15.6%**
* Average order size: **$648.79**

This indicates that Tables represent a significant profitability risk because losses are concentrated in relatively high-value transactions.

---

# 🚚 10. Shipping & Customer Segment Analysis

The project identified:

```text
114 orders
```

that were simultaneously:

* Shipped using **Same Day** shipping
* Purchased by customers in the **Corporate** segment

---

# 🌎 11. Regional Profitability Analysis

The most profitable state in the Central region was:

## 🥇 Michigan

```text
Total Profit: $24,463.19
```

### Central Region Profitability

| State        |      Profit |
| ------------ | ----------: |
| Michigan     |  $24,463.19 |
| Indiana      |  $18,382.94 |
| Minnesota    |  $10,823.19 |
| Wisconsin    |   $8,401.80 |
| Missouri     |   $6,436.21 |
| Oklahoma     |   $4,853.96 |
| Nebraska     |   $2,037.09 |
| Iowa         |   $1,183.81 |
| Kansas       |     $836.44 |
| South Dakota |     $394.83 |
| North Dakota |     $230.15 |
| Illinois     | -$12,607.89 |
| Texas        | -$25,729.36 |

---

# 🎉 12. Holiday Sales & Profitability Analysis

A separate US holiday dataset was merged with the Superstore dataset.

### Data Integration

* Original holiday rows: 342
* Unique holiday dates after deduplication: 336
* Dataset rows before merge: 9,994
* Dataset rows after merge: 9,994

The merge preserved the original row count and did not introduce duplicate transactions.

### Holiday Transactions

| Transaction Type | Number of Orders |
| ---------------- | ---------------: |
| Non-Holiday      |            9,300 |
| Holiday          |              694 |

Holiday transactions represented approximately:

```text
6.9% of all transactions
```

### Average Performance

| Transaction Type | Average Sales | Average Profit |
| ---------------- | ------------: | -------------: |
| Non-Holiday      |       $231.15 |         $28.53 |
| Holiday          |       $212.50 |         $30.38 |

### Conclusion

Holiday transactions had:

* Slightly lower average sales
* Slightly higher average profit

Overall, holidays appeared to have limited impact on sales and profitability.

This conclusion is descriptive because no formal statistical significance test was performed.

---

# 📊 13. Discount Impact Dashboard

A two-part dashboard was created to compare:

1. Average discount by category
2. Aggregate profit margin by category

### Average Discount

| Category        | Average Discount |
| --------------- | ---------------: |
| Furniture       |           17.39% |
| Office Supplies |           15.73% |
| Technology      |           13.23% |

### Aggregate Profit Margin

| Category        | Profit Margin |
| --------------- | ------------: |
| Technology      |    **17.40%** |
| Office Supplies |    **17.04%** |
| Furniture       |     **2.49%** |

### Key Insight

Furniture had:

* The highest average discount
* The lowest aggregate profit margin

Technology had:

* The lowest average discount
* The highest aggregate profit margin

This demonstrates the importance of controlling discount levels.

---

# 🚛 14. Delivery Performance by Ship Mode

### Delivery Time Summary

| Ship Mode      | Average Days | Median Days |
| -------------- | -----------: | ----------: |
| Same Day       |         0.04 |           0 |
| First Class    |         2.18 |           2 |
| Second Class   |         3.24 |           3 |
| Standard Class |         5.01 |           5 |

The delivery time hierarchy was consistent with expectations:

```text
Same Day
    ↓
First Class
    ↓
Second Class
    ↓
Standard Class
```

Standard Class had the longest delivery time, while Same Day shipping had the shortest.

---

# 📈 15. Interactive Sales vs Profit Analysis

An interactive Plotly scatter plot was created to analyze the relationship between:

* Sales
* Profit
* Quantity
* Ship Mode

The visualization allows users to identify:

* High-sales/high-profit transactions
* High-sales/loss-making transactions
* The relationship between order quantity and financial performance
* Differences across shipping methods

---

# 💡 16. Key Business Insights

### Insight 1: Technology is the Most Profitable Category

Technology achieved the highest aggregate profit margin:

```text
17.40%
```

This makes it the strongest category in terms of profitability efficiency.

---

### Insight 2: The West Region Generated the Highest Profit

The West region generated:

```text
$108,418.45
```

in total profit.

This indicates strong regional performance and potential opportunities for expanding successful strategies to other regions.

---

### Insight 3: November Was the Strongest Sales Month

November generated the highest total sales:

```text
$352,461.07
```

This included:

* 753 distinct orders
* 5,775 units sold

This confirms that the high sales volume was supported by substantial transaction activity.

---

# 🎯 17. Business Recommendations

## Recommendation 1: Implement a Discount Ceiling Policy

### Evidence

856 transactions had:

```text
Discount > 50%
AND
Negative Profit
```

### Recommended Action

* Establish a discount approval threshold.
* Require management approval for discounts above 50%.
* Use category-specific discount limits.
* Monitor discount impact on profit margin continuously.

The goal is to prevent revenue growth from being achieved at the expense of profitability.

---

## Recommendation 2: Focus More on High-Profit Categories

### Evidence

| Category   | Aggregate Profit Margin |
| ---------- | ----------------------: |
| Technology |                  17.40% |
| Furniture  |                   2.49% |

### Recommended Action

* Increase inventory investment in Technology products.
* Prioritize marketing campaigns for high-margin products.
* Review pricing and discount strategies for Furniture.
* Investigate loss-making Furniture sub-categories, especially Tables.

---

# 📁 Project Structure

```text
retail-sales-profitability-analysis/
│
├── notebooks/
│   └── retail_sales_profitability_analysis.ipynb
│
├── data/
│   ├── Superstore.csv
│   └── US Holiday Dates.csv
│
├── images/
│   ├── q9_correlation_heatmap.png
│   ├── q16_discount_dashboard.png
│   └── q17_delivery_boxplot.png
│
├── README.md
└── requirements.txt
```

---

# ▶️ How to Run the Project

## Option 1: Google Colab

1. Open the notebook in Google Colab.
2. Upload the `Superstore.csv` dataset when prompted.
3. Upload the US holiday dataset when prompted.
4. Run all cells sequentially.
5. Review the generated tables, charts, and insights.

## Option 2: Local Jupyter Notebook

Install the required libraries:

```bash
pip install pandas numpy matplotlib seaborn plotly jupyter
```

Then launch Jupyter Notebook:

```bash
jupyter notebook
```

Open the notebook and ensure that the required CSV files are located in the working directory.

---

# 📦 Requirements

```text
pandas
numpy
matplotlib
seaborn
plotly
```

---

# ⚠️ Project Limitations

* The analysis is descriptive and does not include formal hypothesis testing.
* Correlation does not establish causation.
* The dataset does not include a Cost column, so the exact cost structure behind profit margins cannot be verified.
* Holiday impact was evaluated using descriptive comparisons only.
* The analysis focuses on historical data from 2014–2017.
* External factors such as market conditions, competitor pricing, inventory availability, and customer demographics were not included.

---

# 🚀 Future Improvements

Future versions of this project could include:

* Statistical significance testing for holiday effects.
* Time-series forecasting for future sales and profit.
* Customer segmentation and lifetime value analysis.
* Product-level profitability optimization.
* Predictive modeling for loss-making transactions.
* Interactive Power BI or Tableau dashboard development.
* Automated reporting using Python.
* What-if analysis for discount optimization.
* Profit forecasting by category, region, and sub-category.

---

# 🏆 Executive Summary

The analysis identified several important profitability drivers:

* **Discounting is strongly negatively associated with profit margin.**
* **Furniture has high discount levels and very low aggregate profitability.**
* **Tables are the weakest-performing sub-category based on aggregate profit margin.**
* **Technology is the most profitable category.**
* **Michigan is the most profitable state in the Central region.**
* **The West region generated the highest total profit.**
* **November recorded the highest total sales.**
* **Holiday transactions had limited overall impact on sales and profit.**
* **Shipping performance followed the expected service-level hierarchy.**

The most important management takeaway is that **revenue growth alone does not guarantee profitability**. A successful retail strategy should combine sales growth with disciplined discount management and greater focus on high-margin product categories.

---

## 👤 Author

**Ronak Tasnim Kotha**

Data Analytics | Business Analytics | Python | SQL | Data Visualization

This project was developed as an end-to-end retail analytics project using Python and Google Colab.
