## 📊 Sales Trend Analysis with SQL Aggregations
A comprehensive collection of SQL queries designed to analyze e-commerce sales data using time-based aggregations and key business performance metrics.

## 📚 Features

Monthly Revenue Analysis: Monitor revenue trends across months and years.

Order Volume Trends: Identify peak sales periods and seasonal demand.

Top Products and Cities: Uncover best-selling products and high-performing regions.

Discount Impact: Evaluate the effectiveness of promotional strategies.

Profit Tracking: Analyze profitability and operational efficiency.

## 🛠️ Setup Instructions

1. Database Schema

sql
Copy
Edit
CREATE TABLE orders (
    order_id INT PRIMARY KEY,
    order_date DATE,
    list_price DECIMAL(10,2),
    product_id INT,
    city VARCHAR(50),
    category VARCHAR(50),
    discount_percent DECIMAL(5,2),
    profit DECIMAL(10,2)
);
2. Importing Data

Create the database:
CREATE DATABASE online_sales;

Import CSV data using your DBMS tool (e.g., \copy in PostgreSQL or import utility in MySQL/SQL Server).

## 🧩 Key SQL Queries

1. Monthly Revenue and Order Volume

sql
Copy
Edit
SELECT 
  EXTRACT(YEAR FROM order_date) AS year,
  EXTRACT(MONTH FROM order_date) AS month,
  SUM(list_price) AS revenue,
  COUNT(DISTINCT order_id) AS orders
FROM orders
GROUP BY year, month
ORDER BY year, month;
2. Top 5 Best-Selling Products

sql
Copy
Edit
SELECT
  product_id,
  SUM(list_price) AS total_sales,
  AVG(profit) AS avg_profit
FROM orders
GROUP BY product_id
ORDER BY total_sales DESC
LIMIT 5;
## 📈 Sample Output Format (Monthly Trends)


Year	Month	Revenue	Orders
2023	1	15000.00	120
2023	2	16500.00	135
## 🔍 Query Filters

Apply custom date ranges to any query:

sql
Copy
Edit
WHERE order_date BETWEEN '2023-01-01' AND '2023-12-31'
