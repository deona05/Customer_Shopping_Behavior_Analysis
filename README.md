# Customer Shopping Behavior Analysis

An exploratory retail analytics project using Python and Pandas, MySQL, and Power BI. It examines customer, product, purchase, subscription, discount, shipping, and review data from a 3,900-row dataset.

## Project contents

| File | Purpose |
|---|---|
| `customer_shopping_behavior.csv` | Source dataset (3,900 records, 18 columns) |
| `CustomerBehavior.ipynb` | Data inspection, cleaning, feature engineering, and loading the prepared data into MySQL |
| `CustomerBehavior.sql` | Six SQL analyses using the `mycustomer` table |
| `custbrhavior.pbix` | Power BI report |
| `LICENSE` | MIT license for this project |

## Dataset

The CSV contains one row per customer and these fields:

- **Customer and demographics:** Customer ID, Age, Gender, Location
- **Product and purchase:** Item Purchased, Category, Purchase Amount (USD), Size, Color, Season
- **Shopping and engagement:** Review Rating, Subscription Status, Shipping Type, Discount Applied, Promo Code Used, Previous Purchases, Payment Method, Frequency of Purchases

The source has 37 missing review ratings; the notebook fills these with the median rating for the corresponding product category. It also standardizes column names, renames the purchase amount column, creates age quartiles, and maps purchase frequency labels to days. The two discount/promo flags are compared and the redundant `promo_code_used` column is dropped when preparing the SQL table.

The dataset does not include transaction dates, order IDs, costs, or discount amounts. Therefore, its summed purchase amounts are sample totals, not time-period revenue or profit, and it cannot support time-series or validated churn analysis.

## Business questions

The SQL file explores:

1. How summed purchase amounts compare by gender.
2. Which discounted purchases are at or above the overall average purchase amount.
3. Which five products have the highest average review rating.
4. How average purchase amount compares between Standard and Express shipping.
5. How customer counts, average purchase amounts, and summed purchase amounts compare by subscription status.
6. Which five products have the highest discount-use rate.

These are descriptive comparisons; they do not establish that a discount, subscription, shipping type, or demographic characteristic causes a change in spending.

## Requirements

- Python 3
- Jupyter Notebook
- Python packages: `pandas`, `SQLAlchemy`, `PyMySQL`, and `python-dotenv`
- MySQL Server
- Power BI Desktop (to open the `.pbix` report)

Install the Python packages in your environment:

```bash
python -m pip install pandas sqlalchemy pymysql python-dotenv jupyter
```

## Run the analysis

### 1. Prepare MySQL

Start MySQL Server and create the database before loading the table:

```sql
CREATE DATABASE custBehavior;
```

### 2. Configure the database connection

Create a local `.env` file in the project directory (do not commit it) with your own MySQL credentials:

```dotenv
DB_USER=root
DB_PASSWORD=your_mysql_password
DB_HOST=localhost
DB_NAME=custBehavior
```

The `.env` file is excluded by `.gitignore`. Do not put credentials in the notebook or share them publicly.

### 3. Run the notebook

Open `CustomerBehavior.ipynb` and set the working directory to the project folder. Run the cells from top to bottom:

1. Load `customer_shopping_behavior.csv` into the `df` DataFrame.
2. Inspect and prepare the data.
3. Run the MySQL loading cell to replace/create the `mycustomer` table in `custBehavior`.
4. Check the purchase-frequency mapping validation output.

The notebook loads the CSV by a relative filename, so it must run with the project directory as its working directory. The MySQL loading cell requires a reachable MySQL server, a valid `.env`, and permission to create or replace tables.

### 4. Run SQL queries

After the notebook has loaded `mycustomer`, open `CustomerBehavior.sql` in a MySQL-compatible SQL client and execute the queries. The SQL file selects the `custBehavior` database and expects the transformed table and normalized column names produced by the notebook; importing the raw CSV directly does not create that schema.

### 5. Open the dashboard

Open `custbrhavior.pbix` in Power BI Desktop. The report contains a single page with KPI cards, category and age-group charts, a subscription chart, and slicers.

## Current scope and limitations

- The notebook performs data inspection, missing-rating imputation, column cleanup, age/frequency feature engineering, and MySQL loading. It does not currently include a plotted EDA section.
- SQL demonstrates filtering, grouping, aggregate functions, sorting, a scalar subquery, and a `CASE` expression. It does not currently demonstrate joins, CTEs, or window functions.
- The dataset is cross-sectional and has no dates or order-level history, limiting trend and retention analysis.
- Review Power BI aggregations and measure definitions in Desktop before relying on dashboard totals. Customer IDs should be counted, not summed, for customer-count visuals.

## License and data

The project code and documentation are licensed under the MIT License; see [`LICENSE`](LICENSE). The dataset may have separate source and reuse terms; verify those terms with the dataset provider before redistributing it.
