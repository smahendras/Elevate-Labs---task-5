# Elevate-Labs---task-5

# 🍽️ Restaurant Database Project

This project sets up a relational database for managing customer and order data in a restaurant. It uses MySQL and demonstrates table creation, data population, and SQL joins.

## 📦 Tables Overview

### 1. `customer`
Stores customer details.

| Field Name      | Type           | Description                          |
|-----------------|----------------|--------------------------------------|
| `customerId`    | INT (PK, AI)   | Unique customer ID                   |
| `content`       | TEXT           | Notes/preferences                    |
| `mobileNumber`  | VARCHAR(15)    | Phone number                         |
| `customerName`  | VARCHAR(100)   | Full name                            |
| `email`         | VARCHAR(30)    | Email address                        |
| `createdAt`     | TIMESTAMP      | Record creation time                 |
| `address`       | TEXT           | Full address                         |

### 2. `orders`
Stores order details linked to customers.

| Field Name      | Type           | Description                          |
|-----------------|----------------|--------------------------------------|
| `order_id`      | INT (PK, AI)   | Unique order ID                      |
| `customerId`    | INT (FK)       | References `customer.customerId`     |
| `order_date`    | DATE           | Date of the order                    |
| `total_amount`  | DECIMAL(10,2)  | Total bill amount                    |
| `status`        | VARCHAR(50)    | Order status (Pending, Completed…)   |
| `paymentMode`   | VARCHAR(30)    | Payment method (Cash, Card, UPI…)    |
| `Note`          | VARCHAR(30)    | Optional notes                       |

## 🧪 Sample Data

### Customers
11 sample customers inserted, including one with no orders to demonstrate joins.

### Orders
11 sample orders inserted, all linked to valid customers.

## 🔗 SQL Joins

### INNER JOIN
```sql
SELECT customer.customerId, customer.customerName, orders.order_id, orders.total_amount
FROM customer
INNER JOIN orders ON customer.customerId = orders.customerId;
```

### LEFT JOIN
```sql
SELECT customer.customerId, customer.customerName, orders.order_id, orders.total_amount
FROM customer
LEFT JOIN orders ON customer.customerId = orders.customerId;
```

### RIGHT JOIN
```sql
SELECT customer.customerId, customer.customerName, orders.order_id, orders.total_amount
FROM customer
RIGHT JOIN orders ON customer.customerId = orders.customerId;
```

### FULL JOIN (MySQL workaround using UNION)
```sql
SELECT customer.customerId, customer.customerName, orders.order_id, orders.total_amount
FROM customer
LEFT JOIN orders ON customer.customerId = orders.customerId
UNION
SELECT customer.customerId, customer.customerName, orders.order_id, orders.total_amount
FROM customer
RIGHT JOIN orders ON customer.customerId = orders.customerId;
```

## 🚀 How to Run

1. Create the database:
   ```sql
   CREATE DATABASE restaurent;
   USE restaurent;
   ```

2. Create tables and insert data as shown above.

3. Run join queries to explore relations.
