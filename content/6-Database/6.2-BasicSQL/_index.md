---
title : "Basic SQL"
date :  "`r Sys.Date()`" 
weight : 2
chapter : false
pre : " <b> 6.2 </b> "
---

#### Key SQL concepts
- **Table**: A table is a collection of related data organized into rows and columns. Each table represents a real-world entity (e.g., customers, orders).

- **Row**: A row (also called a record) is a single, complete set of fields (values) for one entity in the table.

- **Column**: A column (also called a field) is a specific attribute of an entity (e.g., customer name, order date).

#### Basic SQL Command
SQL provides several basic commands to interact with databases, such as retrieving, inserting, updating, and deleting data. Here are the most commonly used ones:

1. **SELECT** – Retrieve Data from a Database

   - **Syntax**:
        ```sql
        SELECT column1, column2, ...
        FROM table_name;
        ```
   - **Example**:
        ```sql
        SELECT first_name, last_name
        FROM customers;
        ```

2. **INSERT** – Insert Data into a Table

   - **Syntax**:
        ```sql
        INSERT INTO table_name (column1, column2, ...)
        VALUES (value1, value2, ...);
        ```
   - **Example**:
        ```sql
        INSERT INTO customers (first_name, last_name, email)
        VALUES ('Dung', 'Tran', 'dungtn@gmail.com');
        ```

3. **UPDATE** – Update Existing Data in a Table

   - **Syntax**:
        ```sql
        UPDATE table_name
        SET column1 = value1, column2 = value2, ...
        WHERE condition;
        ```
   - **Example**:
        ```sql
        UPDATE customers
        SET email = 'dungtn@example.com'
        WHERE customer_id = 1;
        ```

4. **DELETE** – Delete Data from a Table

   - **Syntax**:
        ```sql
        DELETE FROM table_name
        WHERE condition;
        ```
   - **Example**:
        ```sql
        DELETE FROM customers
        WHERE customer_id = 1;
        ```