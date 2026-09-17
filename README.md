# Customer Behaviour Analysis

This project analyzes customer shopping behavior using SQL and a retail customer dataset. It explores purchasing patterns, customer segments, product performance, discounts, subscriptions, shipping preferences, and revenue trends.

## Project Overview

The analysis answers business questions such as:

- How does revenue compare between male and female customers?
- Do customers who use discounts still spend above average?
- Which products receive the highest average ratings?
- How do Standard and Express shipping customers compare in spending?
- Do subscribed customers generate more revenue?
- Which products are most frequently purchased with discounts?
- How can customers be segmented into New, Returning, and Loyal groups?
- What are the most popular products within each category?
- Are repeat buyers more likely to subscribe?
- Which age groups contribute the most revenue?

## Repository Contents

| File | Description |
|---|---|
| [`customer_behaviour.sql`](customer_behaviour.sql) | SQL queries used to analyze customer behavior |
| [`customer_shopping_behavior-checkpoint.csv`](customer_shopping_behavior-checkpoint.csv) | Customer shopping behavior dataset |
| [`Customer_behaviour_analysis-checkpoint.ipynb`](Customer_behaviour_analysis-checkpoint.ipynb) | Jupyter Notebook checkpoint file |

## Dataset Features

The dataset contains customer and purchase information, including:

- Customer ID
- Age
- Gender
- Item purchased
- Product category
- Purchase amount
- Location
- Product size and color
- Season
- Review rating
- Subscription status
- Shipping type
- Discount and promo code usage
- Number of previous purchases
- Payment method
- Purchase frequency

## Analysis Areas

### Revenue Analysis

The SQL queries calculate revenue by:

- Gender
- Subscription status
- Age group

### Product Analysis

The project identifies:

- Top-rated products
- Most frequently purchased products by category
- Products with the highest discount usage

### Customer Segmentation

Customers are categorized according to their number of previous purchases:

| Segment | Previous Purchases |
|---|---:|
| New | 1 |
| Returning | 2–10 |
| Loyal | More than 10 |

### Subscription Analysis

The project compares subscribers and non-subscribers using:

- Number of customers
- Average purchase amount
- Total revenue

It also investigates whether customers with more than five previous purchases are more likely to subscribe.

## Requirements

To run the SQL analysis, use a PostgreSQL-compatible database because the queries use PostgreSQL syntax such as `::numeric`.

Recommended tools:

- PostgreSQL
- pgAdmin or another SQL client
- Python with Jupyter Notebook, if notebook-based analysis is extended

## Getting Started

### 1. Clone the repository

```bash
git clone https://github.com/aadinathr001/Customer_Behaviour_Analysis.git
cd Customer_Behaviour_Analysis
```

### 2. Load the CSV data

Create a table named `customer` with columns matching the dataset. For example:

```sql
CREATE TABLE customer (
    customer_id INTEGER,
    age INTEGER,
    gender VARCHAR(20),
    item_purchased VARCHAR(100),
    category VARCHAR(100),
    purchase_amount NUMERIC,
    location VARCHAR(100),
    size VARCHAR(10),
    color VARCHAR(50),
    season VARCHAR(20),
    review_rating NUMERIC,
    subscription_status VARCHAR(20),
    shipping_type VARCHAR(50),
    discount_applied VARCHAR(10),
    promo_code_used VARCHAR(10),
    previous_purchases INTEGER,
    payment_method VARCHAR(50),
    frequency_of_purchases VARCHAR(50)
);
```

### 3. Import the dataset

Using PostgreSQL's `COPY` command:

```sql
COPY customer
FROM '/path/to/customer_shopping_behavior-checkpoint.csv'
WITH (
    FORMAT csv,
    HEADER true,
    DELIMITER ','
);
```

Alternatively, import the CSV using pgAdmin or another database management tool.

### 4. Run the analysis queries

Execute the queries in [`customer_behaviour.sql`](customer_behaviour.sql) against the `customer` table.

## Example Query

The following query compares total revenue by gender:

```sql
SELECT
    gender,
    SUM(purchase_amount) AS revenue
FROM customer
GROUP BY gender;
```

## Data Quality Notes

Before performing analysis, it is recommended to:

- Check for missing review ratings
- Confirm that purchase amounts are numeric
- Standardize column names
- Verify that categorical values such as `Yes` and `No` are consistent
- Confirm that the CSV header matches the database table definition
- Create age groups if the `age_group` column is not already available

## Potential Improvements

Future improvements could include:

- Adding data-cleaning queries
- Creating visualizations using Python, Matplotlib, or Seaborn
- Building an interactive dashboard with Power BI or Tableau
- Adding customer lifetime value analysis
- Analyzing purchase frequency over time
- Investigating relationships between discounts and customer retention
- Adding automated data-quality checks
- Replacing checkpoint files with a final cleaned notebook

## Author

Created by [aadinathr001](https://github.com/aadinathr001).

## License

No license has been specified for this repository.
