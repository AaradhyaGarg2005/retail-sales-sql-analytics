# retail-sales-sql-analytics

**SQL-based exploratory data analysis and reporting on a retail sales data warehouse (customers, products, and sales facts) — built and tested in MySQL Workbench.**

## 📌 Description

This project performs end-to-end SQL analytics on a small retail "gold layer" data warehouse consisting of one fact table (`fact_sales`) and two dimension tables (`dim_customers`, `dim_products`). It walks through database/schema exploration, key business metrics, magnitude and ranking analysis, time-based trend and cumulative analysis, year-over-year performance, customer/product segmentation, part-to-whole contribution analysis, and finishes with two production-style reporting views: a **Customer Report** and a **Product Report**.

## 🗂️ Repository Structure

```
retail-sales-sql-analytics/
│
├── datasets/
│   ├── dim_customers.csv        -- Customer dimension (names, gender, birthdate, country, etc.)
│   ├── dim_products.csv         -- Product dimension (category, subcategory, cost, product line, etc.)
│   └── fact_sales.csv           -- Sales fact table (orders, quantities, sales amount, dates)
│
├── scripts/
│   ├── 01_database_exploration.sql       -- Explore tables/columns via INFORMATION_SCHEMA
│   ├── 02_dimensions_exploration.sql     -- Unique countries, categories, subcategories, products
│   ├── 03_date_range_exploration.sql     -- Order date range & customer age range
│   ├── 04_measures_exploration.sql       -- Core KPIs: total sales, quantity, avg price, orders
│   ├── 05_magnitude_analysis.sql         -- Breakdown by country, gender, category
│   ├── 06_ranking_analysis.sql           -- Top/bottom products & customers (RANK, TOP)
│   ├── 07_change_over_time_analysis.sql  -- Monthly/yearly sales trends
│   ├── 08_cumulative_analysis.sql        -- Running totals & moving averages
│   ├── 09_performance_analysis.sql       -- YoY performance vs. average (LAG, window functions)
│   ├── 10_data_segmentation.sql          -- Cost-range and customer-spending segments
│   ├── 11_part_to_whole_analysis.sql     -- Category contribution to overall sales
│   ├── 12_report_customers.sql           -- gold.report_customers view
│   └── 13_report_products.sql            -- gold.report_products view
│
└── README.md
```

## 📊 Data Model

| Table | Description |
|---|---|
| `dim_customers` | One row per customer: name, country, marital status, gender, birthdate, create date |
| `dim_products` | One row per product: category, subcategory, cost, maintenance flag, product line |
| `fact_sales` | One row per order line: order/shipping/due dates, sales amount, quantity, price |

## 🔍 Analysis Covered

- **Exploratory analysis** – schema discovery, dimension values, date ranges
- **Measures & KPIs** – total sales, total quantity, average price, total orders, total products/customers
- **Magnitude analysis** – customers by country/gender, products by category, revenue by category/customer/country
- **Ranking analysis** – top 5 best/worst products, top 10 customers by revenue, customers with fewest orders
- **Change over time** – monthly/yearly sales trends using `DATEPART`, `DATETRUNC`, `FORMAT`
- **Cumulative analysis** – running totals and moving averages with window functions
- **Performance analysis** – year-over-year growth and comparison to product average using `LAG()`
- **Segmentation** – product cost bands and customer VIP/Regular/New tiers
- **Part-to-whole analysis** – category contribution to total revenue
- **Reporting views** – `gold.report_customers` and `gold.report_products` consolidating customer/product KPIs (recency, average order value, average monthly spend/revenue, segments)

## 🛠️ Tools & Environment

This project was developed and tested using **MySQL Workbench**.

## 📄 License

This project is licensed under the **MIT License** — see below.

```
MIT License

Copyright (c) 2026

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
```
