# Online Food Ordering System

## Project Overview

The Online Food Ordering System is a relational database project developed using MySQL. It is designed to store and manage information about restaurants, food menus, customers, orders, and payments.

This project demonstrates important database concepts, including database creation, table creation, primary keys, foreign keys, data insertion, data manipulation, string functions, date functions, aggregate functions, joins, subqueries, views, transactions, stored procedures, and triggers.

## Technologies Used

- Database: MySQL
- Query Language: SQL
- Database Management Tool: MySQL Workbench
- Database Concepts: Relational schema, primary keys, foreign keys, joins, views, transactions, stored procedures, and triggers.

## Database Name

`RESTAURANT_ONLINE_FOOD`

## Database Schema

The database consists of five main tables:

| Table | Purpose | Primary Key |
|---|---|---|
| RESTAURANTS | Stores restaurant names, locations, and cuisine types. | RESTAURANT_ID |
| MENU | Stores food items, prices, availability, and the restaurant offering each item. | MENU_ID |
| CUSTOMERS | Stores customer names, phone numbers, and cities. | CUSTOMER_ID |
| ORDERS | Stores customer orders, selected menu items, quantities, order dates, and order statuses. | ORDER_ID |
| PAYMENTS | Stores payment methods, amounts, statuses, and payment dates for orders. | PAYMENT_ID |

## Relationships

The database contains the following relationships:

1. RESTAURANTS to MENU: One restaurant can offer multiple menu items, but each menu item belongs to only one restaurant.

2. MENU to ORDERS: One menu item can appear in multiple orders, while each order record refers to one menu item.

3. CUSTOMERS to ORDERS: One customer can place multiple orders, but each order belongs to one customer.

4. ORDERS to PAYMENTS: The ER diagram represents a one-to-one relationship. However, the current SQL schema does not define a UNIQUE constraint on PAYMENTS.ORDER_ID, so multiple payment records can be associated with the same order.

## Setup and Execution

Follow these steps to execute the project:

1. Install and open MySQL Workbench or another MySQL client.
2. Open the `PROJECT.sql` file.
3. Connect to the MySQL server.
4. Execute the SQL script.
5. The script creates the database and tables, inserts sample records, and executes the available SQL queries.

To select the database manually, execute:

```sql
USE RESTAURANT_ONLINE_FOOD;
```

## Sample Data

The SQL script contains the following sample records:

- 5 Restaurants
- 10 Menu Items
- 10 Customers
- 12 Orders
- 12 Payment Records

The sample data includes restaurant and customer locations in cities such as Hyderabad, Bengaluru, Chennai, Vijayawada, and Visakhapatnam.

## SQL Concepts Demonstrated

The project demonstrates the following SQL concepts:

1. **DDL (Data Definition Language):** CREATE DATABASE, CREATE TABLE, and CREATE VIEW.

2. **DML (Data Manipulation Language):** INSERT, UPDATE, and DELETE.

3. **String Functions:** UPPER(), LOWER(), LEFT(), CONCAT_WS(), and REPLACE().

4. **Date Functions:** DAYNAME(), DATEDIFF(), and DATE_FORMAT().

5. **Aggregate Functions:** COUNT(), AVG(), SUM(), and MAX().

6. **Joins:** INNER JOIN and LEFT JOIN.

7. **Subqueries:** Nested SELECT statements to retrieve data based on specific conditions.

8. **Views:** CUSTOMER_ORDER_HISTORY and RESTAURANT_REVENUE.

9. **Transactions:** START TRANSACTION, SAVEPOINT, ROLLBACK TO, and COMMIT.

10. **Stored Procedures:** Reusable SQL programs designed to perform specific database operations.

11. **Triggers:** Automatic execution of SQL statements in response to INSERT, UPDATE, or DELETE operations.

## Views

The project includes the following views:

### 1. CUSTOMER_ORDER_HISTORY

This view displays customer order information, including:

- Customer name
- Restaurant name
- Menu item
- Quantity
- Order status

### 2. RESTAURANT_REVENUE

This view displays restaurant revenue information, including:

- Restaurant name
- Total number of orders
- Total payment amount

## Additional Tables for Trigger Exercises

The project includes two additional tables for maintaining order history:

1. ORDERS_ARCHIVE: Intended to store details of deleted orders.

2. ORDER_STATUS_HISTORY: Intended to record the order ID, previous status, new status, and date of status changes.

These tables are designed to support trigger-based auditing and historical record management.

## Notes and Improvements

The current `PROJECT.sql` script contains stored procedure calls and trigger-related tables, but their complete definitions need to be added.

- The statements `CALL ALL_ORDERS(301);` and `CALL TOTAL_SPENT(301);` are included, but their corresponding CREATE PROCEDURE definitions are missing.

- The ORDERS_ARCHIVE and ORDER_STATUS_HISTORY tables are created, but the CREATE TRIGGER statements required to populate them are not included.

- To enforce a one-to-one relationship between ORDERS and PAYMENTS, add a UNIQUE constraint to PAYMENTS.ORDER_ID.

- The script updates orders from PREPARING to DELIVERED before executing later examples. Therefore, execute the script in the correct order.

- For repeated execution, use a fresh database or add appropriate cleanup statements before creating the database and tables again.

## Project Files

The project directory contains the following files:

```text
.
├── PROJECT.sql
├── erd_online_food.png
└── README.md
```

## Conclusion

The Online Food Ordering System provides a practical implementation of relational database concepts using MySQL. It demonstrates how restaurants, menus, customers, orders, and payments can be efficiently organized and managed through SQL.

The project provides hands-on experience with database design, data manipulation, data retrieval, reporting, and database programming concepts. It also helps develop practical SQL skills that are useful in real-world database management applications.
