# olist-customer-analysis
SQL analysis of 100K real e-commerce orders: repeat purchases, top categories, late deliveries and customer value

## Business Problem
The Marketing Manager suspected that most customers buy once and never come back, which would mean that a large part of the advertising budget is wasted. She asked four questions:

1. Do customers come back?
2. What do customers buy?
3. Are late deliveries hurting customer satisfaction?
4. Who are our best customers?

## Data
[Brazilian E-Commerce Public Dataset by Olist](https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce) (Kaggle). Six related tables were used: customers, orders, order items, payments, reviews and products.

## Process
- Loaded the CSV files into a SQLite database in Google Colab.
- Explored the tables and their relationships.
- Identified a key data trap: `customer_id` changes with every order, so unique customers were counted with `customer_unique_id`.
- Answered each question with SQL: JOINs across up to three tables, subqueries, CASE WHEN and aggregations.

## Key Findings

**1. Do customers come back?**
97% of customers (93,099 out of 96,096) made only one purchase. Only 3 out of 100 customers buy again.

**2. What do customers buy?**
- Most items sold: Bed, Bath & Table (home textiles), followed by Health & Beauty and Sports & Leisure.
- Most revenue: Health & Beauty (~R$ 1.26M). Watches & Gifts ranks 7th in units but 2nd in revenue because its products are more expensive.

**3. Are late deliveries hurting us?**
- About 8% of delivered orders (7,700) arrived after the promised date.
- Late orders have an average review score of 2.57 vs. 4.29 for on-time orders.
- 54% of late orders received a bad review (1–2 stars), compared to 9.2% of on-time orders: about 6 times more.
- This shows a strong relationship between delays and dissatisfaction. Confirming that delays are the direct cause would require further analysis.

**4. Who are our best customers?**
- The top spenders made a single large purchase; they are not loyal customers.
- Repeat customers (2+ orders) spend R$ 309 on average vs. R$ 161 for one-time customers: almost double.

## Recommendations
1. **Invest in retention**, not only in acquisition: repeat customers are worth almost twice as much.
2. **Fix late deliveries**, since they are strongly linked to bad reviews and may stop customers from coming back.
3. **Focus retention campaigns on high-revenue categories** such as Health & Beauty and Watches & Gifts.
4. **Next step:** compare the cost of retention campaigns with the cost of acquiring new customers.

## Files
- `olist_customer_analysis.ipynb`: SQL queries and results.

## Tools
SQL (SQLite) · Python (pandas) · Google Colab

*Power BI dashboard coming soon.*
