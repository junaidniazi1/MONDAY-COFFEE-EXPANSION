

---

# MONDAY COFFEE EXPANSION

![Monday Coffee Expansion](https://github.com/junaidniazi1/MONDAY-COFFEE-EXPANSION/blob/main/1.png)

---

## Project Overview

This project provides a comprehensive SQL-based data analysis for Monday Coffee’s business expansion strategy. It includes database schemas for storing city, customer, product, and sales data, as well as detailed SQL queries for insights into coffee consumption, sales performance, and market potential.

---

## Database Schemas

The database is designed with the following tables:

1. **city** — Stores city details like population, estimated rent, and ranking.
2. **products** — Lists coffee products available for sale.
3. **customers** — Contains customer information linked to cities.
4. **sales** — Records individual sales transactions with product, customer, date, amount, and rating.

### Import Order for Data

1. Import city data first
2. Import product data
3. Import customer data
4. Import sales data

```sql
CREATE DATABASE MONDAY_COFFEE;
USE MONDAY_COFFEE;

CREATE TABLE city (
  city_id INT PRIMARY KEY,
  city_name VARCHAR(15),
  population BIGINT,
  estimated_rent FLOAT,
  city_rank INT
);

CREATE TABLE customers (
  customer_id INT PRIMARY KEY,
  customer_name VARCHAR(25),
  city_id INT,
  CONSTRAINT fk_city FOREIGN KEY (city_id) REFERENCES city(city_id)
);

CREATE TABLE products (
  product_id INT PRIMARY KEY,
  product_name VARCHAR(35),
  price FLOAT
);

CREATE TABLE sales (
  sale_id INT PRIMARY KEY,
  sale_date DATE,
  product_id INT,
  customer_id INT,
  total FLOAT,
  rating INT,
  CONSTRAINT fk_products FOREIGN KEY (product_id) REFERENCES products(product_id),
  CONSTRAINT fk_customers FOREIGN KEY (customer_id) REFERENCES customers(customer_id)
);
```

---

## Main SQL Queries and Reports

This section contains key SQL queries for analyzing sales and customer behavior, including:

* Estimating coffee consumers in each city (25% of population)
* Total and city-wise revenue for Q4 2023
* Product-wise sales counts
* Average sales per customer by city
* Customer segmentation and unique customer counts by city
* Top 3 selling products per city
* Comparison of average sales vs rent per customer
* Monthly sales growth analysis
* Market potential analysis identifying top 3 cities for expansion

**Example: Estimating coffee consumers in millions per city**

```sql
SELECT 
  city_name,
  ROUND((population * 0.25) / 1000000, 2) AS coffee_consumers_in_millions,
  city_rank
FROM city
ORDER BY coffee_consumers_in_millions DESC;
```

(See full queries in the `main.sql` file.)

---

## Recommendations

Based on data insights:

* **Pune** is the top city for expansion due to highest total revenue and low rent per customer.
* **Delhi** has the largest estimated coffee consumer base and a high number of customers.
* **Jaipur** shows a strong customer base and good sales per customer with affordable rent.

---

## Repository Structure

* `schemas.sql` — Database creation and table schema definitions
* `main.sql` — Main SQL queries and reports for analysis
* `1.png` — Visual summary of Monday Coffee expansion analysis

---

## How to Use

1. Create the database and tables using `schemas.sql`.
2. Import data in the correct order: city → products → customers → sales.
3. Run queries from `main.sql` to generate reports and insights.

---

Feel free to explore and contribute!

---

If you want me to generate the actual `README.md` file content you can copy-paste, just say so!
