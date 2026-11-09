# Online Food Ordering System

## Project Overview

The **Online Food Ordering System** is a relational database project
developed using MySQL. It stores and manages information about
restaurants, their food menus, customers, orders, and payments.

The project demonstrates database concepts such as table creation,
primary and foreign keys, data insertion, data manipulation, string and
date functions, aggregate functions, joins, subqueries, views,
transactions, stored procedures, and triggers.

## Technologies Used

-   **Database:** MySQL
-   **Language:** SQL
-   **Database concepts:** Relational schema, primary keys, foreign
    keys, joins, views, transactions, stored procedures, and triggers

## Database Name

``` sql
RESTAURANT_ONLINE_FOOD
```

## Database Schema

The database contains five main tables:

  -----------------------------------------------------------------------
  Table                   Purpose                 Primary Key
  ----------------------- ----------------------- -----------------------
  `RESTAURANTS`           Stores restaurant       `RESTAURANT_ID`
                          names, locations, and   
                          cuisine types.          

  `MENU`                  Stores food items,      `MENU_ID`
                          prices, availability,   
                          and the restaurant      
                          offering each item.     

  `CUSTOMERS`             Stores customer names,  `CUSTOMER_ID`
                          phone numbers, and      
                          cities.                 

  `ORDERS`                Stores customer orders, `ORDER_ID`
                          selected menu items,    
                          quantities, dates, and  
                          order statuses.         

  `PAYMENTS`              Stores payment methods, `PAYMENT_ID`
                          amounts, statuses, and  
                          payment dates for       
                          orders.                 
  -----------------------------------------------------------------------

### Relationships

-   **RESTAURANTS to MENU:** One restaurant can offer multiple menu
    items. Each menu item belongs to one restaurant.
-   **MENU to ORDERS:** One menu item can appear in multiple orders.
    Each order record refers to one menu item.
-   **CUSTOMERS to ORDERS:** One customer can place multiple orders.
    Each order belongs to one customer.
-   **ORDERS to PAYMENTS:** The ER diagram represents this as a
    one-to-one relationship. The current SQL schema has a foreign key
    from `PAYMENTS.ORDER_ID` to `ORDERS.ORDER_ID`, but does not declare
    it `UNIQUE`; therefore, the SQL schema currently permits multiple
    payment records for one order.

## ER Diagram

The entity-relationship diagram for the project is provided as:

`erd_online_food.png`

It illustrates the five main entities, their attributes, and the
relationships between them.

## Setup and Execution

1.  Install and open MySQL Workbench or another MySQL client.
2.  Open the `PROJECT.sql` file.
3.  Execute the script using a MySQL connection.
4.  The script creates the database and tables, inserts sample records,
    and runs the listed SQL queries.

The database can also be selected manually with:

``` sql
USE RESTAURANT_ONLINE_FOOD;
```

## Sample Data

The SQL script inserts sample records for:

-   5 restaurants
-   10 menu items
-   10 customers
-   12 orders
-   12 payment records

The sample data uses restaurant and customer locations in cities such as
Hyderabad, Bengaluru, Chennai, Vijayawada, and Visakhapatnam.

## SQL Concepts Demonstrated

The script includes examples of the following:

1.  **DDL (Data Definition Language):** `CREATE DATABASE`,
    `CREATE TABLE`, and `CREATE VIEW`.
2.  **DML (Data Manipulation Language):** `INSERT`, `UPDATE`, and
    `DELETE`.
3.  **String functions:** `UPPER()`, `LOWER()`, `LEFT()`, `CONCAT_WS()`,
    and `REPLACE()`.
4.  **Date functions:** `DAYNAME()`, `DATEDIFF()`, and `DATE_FORMAT()`.
5.  **Aggregate functions:** `COUNT()`, `AVG()`, `SUM()`, and `MAX()`.
6.  **Joins:** `INNER JOIN` and `LEFT JOIN`.
7.  **Subqueries:** Queries using nested `SELECT` statements.
8.  **Views:** `CUSTOMER_ORDER_HISTORY` and `RESTAURANT_REVENUE`.
9.  **Transactions:** `START TRANSACTION`, `SAVEPOINT`, `ROLLBACK TO`,
    and `COMMIT`.
10. **Stored procedures and triggers:** These are included as project
    requirements/call examples, but their definitions need to be added
    to the current SQL script (see Notes).

## Views

### `CUSTOMER_ORDER_HISTORY`

Displays: - Customer name - Restaurant name - Menu item - Quantity -
Order status

### `RESTAURANT_REVENUE`

Displays: - Restaurant name - Total number of orders - Total payment
amount

## Additional Tables for Trigger Exercises

The script creates two tables intended for trigger-based history:

-   `ORDERS_ARCHIVE` --- intended to store details of deleted orders.
-   `ORDER_STATUS_HISTORY` --- intended to record an order's previous
    status, new status, order ID, and change date.

## Notes and Improvements

The current `PROJECT.sql` script contains calls and test statements for
stored procedures and triggers, but does not include their complete
definitions:

-   `CALL ALL_ORDERS(301);` and `CALL TOTAL_SPENT(301);` are present,
    but `CREATE PROCEDURE` statements for these procedures are not
    included.
-   The archive and status-history tables are created, but the
    `CREATE TRIGGER` statements that populate them are not included.
-   If the intended relationship between `ORDERS` and `PAYMENTS` is
    one-to-one, add a `UNIQUE` constraint to `PAYMENTS.ORDER_ID`.
-   The script updates orders from `PREPARING` to `DELIVERED` before
    later examples. Run the script in order and be aware that updates
    and deletes change the sample data.
-   For a repeatable setup, use a fresh database or add appropriate
    cleanup statements before re-running the script, because the
    database and table creation statements do not use `IF NOT EXISTS`.

## Project Files

``` text
.
├── PROJECT.sql
├── erd_online_food.png
└── README.md
```

## Conclusion

This project provides a practical example of designing and querying a
relational database for an online food ordering scenario. It connects
restaurants, menus, customers, orders, and payments, while demonstrating
commonly used MySQL operations and database programming concepts.
