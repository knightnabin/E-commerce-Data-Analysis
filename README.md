# E-Commerce Inventory Analysis Portfolio Project

A hands-on data analyst project leveraging an end-to-end workflow on a real-world inventory dataset scraped from Zepto.com, one of India’s fastest growing quick-commerce startups. 

Key highlights:
- Data acquisition & ETL using Python, pandas, NumPy  
- Robust data cleaning, validation & feature engineering  
- Exploratory data analysis with SQL, Jupyter notebooks & descriptive statistics  
- Interactive visualizations with matplotlib, seaborn & Plotly  
- Dashboard prototyping in Power BI/Tableau for stakeholder reporting  
- Actionable business insights & recommendations to optimize inventory turnover  

Skills demonstrated: Python, SQL, data wrangling, EDA, data visualization, BI tools, statistical analysis, storytelling.

# SQL-Focused E-Commerce Inventory Analysis Project

A hands-on simulation of an end-to-end data analyst workflow in retail/e-commerce, built entirely with SQL. This project transforms a raw Zepto inventory dataset into a structured database, uncovers key business metrics, and drives data-backed recommendations.

## Core SQL Deliverables

- Design and populate a messy, real-world inventory **database** schema  
- Execute exploratory queries to inspect product categories, stock statuses, and pricing anomalies  
- Clean and standardize data: handle NULLs, remove invalid rows, and convert pricing from paise to rupees  
- Develop business-driven SQL statements to analyze pricing trends, monitor inventory levels, calculate revenue, and more  

## Skills & Techniques

- Database design & ETL pipelines  
- Complex joins, CTEs, window functions, and aggregations  
- Data cleansing with conditional expressions and error filtering  
- Query performance tuning and indexing  
- Translating SQL results into actionable business insights

## Dataset Overview

This dataset, sourced from Kaggle and originally scraped from Zepto’s official product listings, mirrors the complexity of a live e-commerce inventory system.The dataset was sourced from [Kaggle](https://www.kaggle.com/datasets/palvinder2006/zepto-inventory-dataset/data?select=zepto_v2.csv)

Each record corresponds to a unique SKU. Repeated product names arise because the same item is listed in various package sizes, weights, discount tiers, or categories to maximize visibility—just like a real catalog..

🧾 Columns:
- **sku_id:** Unique identifier for each product entry (Synthetic Primary Key)

- **name:** Product name as it appears on the app

- **category:** Product category like Fruits, Snacks, Beverages, etc.

- **mrp:** Maximum Retail Price (originally in paise, converted to ₹)

- **discountPercent:** Discount applied on MRP

- **discountedSellingPrice:** Final price after discount (also converted to ₹)

- **availableQuantity:** Units available in inventory

- **weightInGms:** Product weight in grams

- **outOfStock:** Boolean flag indicating stock availability

- **quantity:** Number of units per package (mixed with grams for loose produce)

#  Project Workflow

## 1. Database & Table Creation

```sql
CREATE TABLE zepto (
  sku_id SERIAL PRIMARY KEY,
  category VARCHAR(120),
  name VARCHAR(150) NOT NULL,
  mrp NUMERIC(8,2),
  discountPercent NUMERIC(5,2),
  availableQuantity INTEGER,
  discountedSellingPrice NUMERIC(8,2),
  weightInGms INTEGER,
  outOfStock BOOLEAN,
  quantity INTEGER
);
```

## 2. Data Import
- Loaded CSV using pgAdmin's import feature.

 - If you're not able to use the import feature, write this code instead:
```sql
   \copy zepto(category,name,mrp,discountPercent,availableQuantity,
            discountedSellingPrice,weightInGms,outOfStock,quantity)
  FROM 'data/zepto_v2.csv' WITH (FORMAT csv, HEADER true, DELIMITER ',', QUOTE '"', ENCODING 'UTF8');
```
- Faced encoding issues (UTF-8 error), which were fixed by saving the CSV file using CSV UTF-8 format.

## 3. 🔍 Data Exploration
- Counted the total number of records in the dataset

- Viewed a sample of the dataset to understand structure and content

- Checked for null values across all columns

- Identified distinct product categories available in the dataset

- Compared in-stock vs out-of-stock product counts

- Detected products present multiple times, representing different SKUs

## 4. 🧹 Data Cleaning
- Identified and removed rows where MRP or discounted selling price was zero

- Converted mrp and discountedSellingPrice from paise to rupees for consistency and readability
  
## 5. 📊 Business Insights
- Found top 10 best-value products based on discount percentage

- Identified high-MRP products that are currently out of stock

- Estimated potential revenue for each product category

- Filtered expensive products (MRP > ₹500) with minimal discount

- Ranked top 5 categories offering highest average discounts

- Calculated price per gram to identify value-for-money products

- Grouped products based on weight into Low, Medium, and Bulk categories

- Measured total inventory weight per product category




MIT — feel free to fork, star, and use in your portfolio.


LinkedIn: [Nabin Pradhan](https://www.linkedin.com/in/nabin-pradhan-9945011b0/)
- Let’s connect professionally 


