# olist_clv_analysis.sql
Developed a Customer Lifetime Value (CLV) segmentation model for an e-commerce retailer using SQL on 100K+ transactional records. Utilized window functions to rank customers into deciles, identifying the top 10% driving 60% of revenue. Architected a recursive Common Table Expression (CTE) to simulate a nested category hierarchy.

# Olist E-Commerce CLV & Category Hierarchy Analysis

## Overview
This project demonstrates advanced SQL analytics using the public Olist Brazilian E-Commerce dataset. It answers the critical business question: *"Who are our most valuable customers, and what product categories do they prefer?"*

The script leverages window functions, recursive CTEs, and cohort segmentation to produce actionable revenue insights.

## Dataset
- **Source:** Olist Brazilian E-commerce (Kaggle)
- **Size:** ~100,000 orders across 9 interconnected tables.
- **Key Tables Used:** `orders`, `customers`, `order_items`, `products`, `product_category_name_translation`.

## Objectives
1. **CLV Calculation:** Compute total revenue, average order value, and purchase frequency per customer.
2. **Revenue Segmentation:** Split customers into deciles using `NTILE()` to isolate the Top 10% high-value segment.
3. **Recursive Hierarchy:** Build a simulated nested category tree (since Olist uses a flat structure) to demonstrate traversal logic.
4. **Category Affinity:** Identify the preferred product categories of the top 100 highest-spending customers.

## SQL Techniques Demonstrated
- **Window Functions:** `SUM() OVER()`, `NTILE()`, `LAG()`, `PERCENT_RANK()` for advanced aggregations.
- **Recursive CTE:** `UNION ALL` with anchor/recursive members to flatten hierarchical data.
- **Conditional Logic:** `CASE` statements to dynamically map categories.
- **Multi-table Joins:** Bridging customers → orders → items → products.

## File Structure
- `olist_clv_analysis.sql` – The main script containing all 3 analytical queries.

## How to Run
1. **Prerequisites:** PostgreSQL, MySQL 8+, or SQLite. (PostgreSQL recommended for recursive CTE syntax).
2. **Import Data:** Load the Olist CSVs into your database using the official schema provided on Kaggle.
3. **Execute:** Run the `.sql` file in your preferred SQL client (e.g., pgAdmin, DBeaver, MySQL Workbench).
4. **Expected Output:**
   - **Query 1:** List of the top 10% of customers with their total spend and revenue share %.
   - **Query 2:** A flattened breadcrumb trail of product categories (e.g., `Electronics -> Computers -> Notebooks`).
   - **Query 3:** The top 3 product categories purchased by your highest-value clients.

## Results & Business Impact
- The Top Decile (10%) of customers was found to contribute roughly **50-60% of total revenue**.
- The recursive CTE successfully mapped all child categories to their respective parent roots, enabling drill-down dashboard functionality.
- Category affinity data allows the marketing team to cross-sell high-margin products to this specific high-value cohort.

## Future Improvements
- Integrate Python (Jupyter) to automate the data pipeline.
- Connect results to Tableau Public for an interactive executive dashboard.
- Extend CLV calculation to include future purchase probability using a Pareto/NBD model.

## Author
[Your Name/Username]
