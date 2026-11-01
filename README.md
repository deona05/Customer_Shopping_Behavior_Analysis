# Customer Shopping Behavior Analysis

This project explores customer shopping patterns using a retail dataset with demographic, purchase, and behavior attributes. The analysis combines Python-based exploratory data analysis (EDA), SQL reporting queries, and a Power BI dashboard to uncover customer trends and business insights.

## Overview

The dataset contains customer purchase information such as:

- Customer demographics (Age, Gender, Location)
- Product details (Item Purchased, Category, Size, Color, Season)
- Purchase behavior (Purchase Amount, Shipping Type, Promo Code, Discount Applied)
- Customer engagement (Review Rating, Subscription Status, Frequency of Purchases)

The goal is to understand how customers shop, which products perform best, how discounts and subscriptions affect spending, and where business opportunities may exist for marketing and retention.

## Business Questions Explored

- Which gender segment contributes more revenue?
- Which products have the highest average review ratings?
- Do subscribed customers spend more than non-subscribed customers?
- How does shipping type affect average purchase amount?
- Which products have the highest discount usage rate?
- What patterns exist in customer purchasing frequency and spending habits?

## Dataset

The main data source is:

- `customer_shopping_behavior.csv`

This file contains 3,900 customer records and includes both transactional and behavioral variables for retail analytics.

## Project Structure

```text
Customer_Shopping_Behavior_Analysis/
├── customer_shopping_behavior.csv      # Source dataset
├── CustomerBehavior.ipynb              # Python notebook for EDA and analysis
├── CustomerBehavior.sql                # SQL queries for business analysis
├── custbrhavior.pbix                  # Power BI dashboard file
├── LICENSE                            # Project license
├── README.md                          # Project documentation
└── .gitignore                         # (if present in your local setup)
```

## Tools and Technologies

- Python
  - Pandas
  - Jupyter Notebook
- SQL
  - MySQL-compatible queries
- Power BI
  - Data visualization and dashboard reporting

## Workflow

1. Load and inspect the customer dataset in Python.
2. Clean and explore the data using EDA techniques.
3. Derive insights from customer purchasing trends.
4. Write SQL queries to answer specific business questions.
5. Build a Power BI dashboard to visualize key findings.

## How to Use

### Option 1: Explore in Jupyter Notebook

1. Open `CustomerBehavior.ipynb` in VS Code, Jupyter Notebook, or JupyterLab.
2. Ensure Python dependencies are installed.
3. Run the cells to load the dataset and perform analysis.

### Option 2: Run SQL Analysis

1. Open `CustomerBehavior.sql` in MySQL or any compatible SQL editor.
2. Create a database and import the CSV data.
3. Execute the queries to derive business insights.

### Option 3: Review the Dashboard

Open `custbrhavior.pbix` in Power BI Desktop to view the visual dashboard.

## Example SQL Insights Included

The SQL file includes queries for:

- Total revenue by gender
- Customers with discount usage above the average purchase amount
- Top 5 products by average rating
- Average spend by shipping method
- Revenue comparison between subscribers and non-subscribers
- Discount penetration by product category/item

## Suggested Future Enhancements

- Add customer churn and retention analysis
- Build predictive models for purchase probability
- Extend dashboard with KPI cards and filters
- Use clustering to segment customers by buying behavior
- Incorporate time-series analysis for seasonal trends

## License

This project is licensed under the MIT License. See the `LICENSE` file for details.

## Summary

This repository demonstrates a practical end-to-end retail analytics workflow using customer data, Python analysis, SQL querying, and dashboard visualization. It is suitable for learning, portfolio projects, and business intelligence demonstrations.
