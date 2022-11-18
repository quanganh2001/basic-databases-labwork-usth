Before do exercise, please extract zip file `northwind-master.zip`, then import 2 SQL files: `northwind.sql` and `northwind-data.sql`
# 1. Write a query to get discontinued Product list (Product ID and name).

```sql
SHOW DATABASES;
USE northwind;
SHOW TABLES;

-- 1. Write a query to get discontinued Product list (Product ID and name).
SELECT id, product_name
FROM Products
WHERE Discontinued = 1 
ORDER BY product_name;
```

Output:

```
+----+--------------------------------+
| id | product_name                   |
+----+--------------------------------+
| 86 | Northwind Traders Cake Mix     |
|  1 | Northwind Traders Chai         |
| 99 | Northwind Traders Chicken Soup |
| 41 | Northwind Traders Clam Chowder |
|  8 | Northwind Traders Curry Sauce  |
| 56 | Northwind Traders Gnocchi      |
| 92 | Northwind Traders Green Beans  |
| 81 | Northwind Traders Green Tea    |
| 97 | Northwind Traders Hot Cereal   |
+----+--------------------------------+
```

# 2. Retrive the top 4 cheapest products

```sql
-- 2. Retrive the top 4 cheapest products
SELECT id, product_name, list_price
FROM Products
ORDER BY list_price ASC
LIMIT 4;
```

Output:

```
+----+-------------------------------+------------+
| id | product_name                  | list_price |
+----+-------------------------------+------------+
| 92 | Northwind Traders Green Beans |     1.2000 |
| 93 | Northwind Traders Corn        |     1.2000 |
| 88 | Northwind Traders Pears       |     1.3000 |
| 89 | Northwind Traders Peaches     |     1.5000 |
+----+-------------------------------+------------+
```

# 3. Write a query to get Product list (id, name, list_price) whose list_price cost between $15 and $25. Hint: using BETWEEN operator or comparison operators (<>) combined with AND operator.

```sql
-- 3. Write a query to get Product list (id, name, list_price) whose list_price cost between $15 and $25. Hint: using BETWEEN operator or comparison operators (<>) combined with AND operator. 
SELECT id, product_name, list_price
FROM Products
WHERE (list_price>=15) AND (list_price <=25)
ORDER BY list_price DESC;

SELECT id, product_name, list_price
FROM Products
WHERE list_price BETWEEN 15 AND 25;
```

Output:

```
+----+--------------------------------------+------------+
| id | product_name                         | list_price |
+----+--------------------------------------+------------+
|  1 | Northwind Traders Chai               |    18.0000 |
|  4 | Northwind Traders Cajun Seasoning    |    22.0000 |
|  5 | Northwind Traders Olive Oil          |    21.3500 |
|  6 | Northwind Traders Boysenberry Spread |    25.0000 |
| 14 | Northwind Traders Walnuts            |    23.2500 |
| 40 | Northwind Traders Crab Meat          |    18.4000 |
| 57 | Northwind Traders Ravioli            |    19.5000 |
| 65 | Northwind Traders Hot Pepper Sauce   |    21.0500 |
| 66 | Northwind Traders Tomato Sauce       |    17.0000 |
| 86 | Northwind Traders Cake Mix           |    15.9900 |
+----+--------------------------------------+------------+
```

# 4. List employees with two columns: id, full_name which is constructed from first_name and last_name.

```sql
-- 4. List employees with two columns: id, full_name which is constructed from
-- first_name and last_name.
SELECT id, concat(first_name,' ',last_name ) as full_name
FROM Employees;
```

Output:

```
+----+---------------------+
| id | full_name           |
+----+---------------------+
|  1 | Nancy Freehafer     |
|  2 | Andrew Cencini      |
|  3 | Jan Kotas           |
|  4 | Mariya Sergienko    |
|  5 | Steven Thorpe       |
|  6 | Michael Neipper     |
|  7 | Robert Zare         |
|  8 | Laura Giussani      |
|  9 | Anne Hellung-Larsen |
+----+---------------------+
```

# 5. Find employees whose names start with ‘A’.

```sql
-- 5. Find employees whose names start with ‘A’.
SELECT id, last_name, first_name
FROM Employees
WHERE first_name LIKE 'A%' OR last_name LIKE 'A%';
```

Output:

```sql
+----+----------------+------------+
| id | last_name      | first_name |
+----+----------------+------------+
|  2 | Cencini        | Andrew     |
|  9 | Hellung-Larsen | Anne       |
+----+----------------+------------+
```

# 6. Show how many different cities the employees living in.

```sql
-- 6. Show how many different cities the employees living in. 
SELECT DISTINCT city
FROM employees;
```

Output:

```
+----------+
| city     |
+----------+
| Bellevue |
| Kirkland |
| Redmond  |
| Seattle  |
+----------+
```

# 7. Show ship_name of table orders without duplicated values.

```sql
-- 7. Show ship_name of table orders without duplicated values. 
SELECT DISTINCT ship_name
FROM Orders
ORDER BY id;
```

Output:

```sql
+------------------------+
| ship_name              |
+------------------------+
| Karen Toh              |
| Christina Lee          |
| John Edwards           |
| Elizabeth Andersen     |
| Soo Jung Lee           |
| Thomas Axen            |
| Francisco Pérez-Olaeta |
| Amritansh Raghav       |
| Roland Wacker          |
| Ming-Yang Xie          |
| Peter Krschne          |
| Anna Bedecs            |
| Sven Mortensen         |
| John Rodman            |
| Run Liu                |
+------------------------+
```

# 8. Show the minimum, maximum of list price in Products table

```sql
-- 8. Show the minimum, maximum of list price in Products table
SELECT MAX(list_price), MIN(list_price)
FROM products;
```

Output:

```
+-----------------+-----------------+
| MAX(list_price) | MIN(list_price) |
+-----------------+-----------------+
|         81.0000 |          1.2000 |
+-----------------+-----------------+
```

# 9. Display the number of current (mean Discontinued = 0) products.

```sql
-- 9. Display the number of current (mean Discontinued = 0) products. 
SELECT count(*) AS number_products
FROM Products
WHERE Discontinued = 0;
```

Output:

```sql
+-----------------+
| number_products |
+-----------------+
|              36 |
+-----------------+
```

# 10. Show the average and standard deviation of the list_price of products.

```sql
-- 10. Show the average and standard deviation of the list_price of products.
SELECT
	AVG(list_price) as average_price,
    STDDEV(list_price) as standard_deviation
FROM Products;
```

Output:

```
+---------------+--------------------+
| average_price | standard_deviation |
+---------------+--------------------+
|   15.84577778 | 16.555943610664606 |
+---------------+--------------------+
```

# 11. Use subquey, show Product list (name, list_price) expensive than the average price.

```sql
-- 11. Use subquey, show Product list (name, list_price) expensive than the average price. 
SELECT id, product_name, list_price
FROM Products
WHERE list_price > 
	(
		SELECT AVG(list_price)
        FROM products
    )
ORDER BY list_price;
```

Output:

```
+----+--------------------------------------+------------+
| id | product_name                         | list_price |
+----+--------------------------------------+------------+
| 86 | Northwind Traders Cake Mix           |    15.9900 |
| 66 | Northwind Traders Tomato Sauce       |    17.0000 |
|  1 | Northwind Traders Chai               |    18.0000 |
| 40 | Northwind Traders Crab Meat          |    18.4000 |
| 57 | Northwind Traders Ravioli            |    19.5000 |
| 65 | Northwind Traders Hot Pepper Sauce   |    21.0500 |
|  5 | Northwind Traders Olive Oil          |    21.3500 |
|  4 | Northwind Traders Cajun Seasoning    |    22.0000 |
| 14 | Northwind Traders Walnuts            |    23.2500 |
|  6 | Northwind Traders Boysenberry Spread |    25.0000 |
|  7 | Northwind Traders Dried Pears        |    30.0000 |
| 72 | Northwind Traders Mozzarella         |    34.8000 |
| 56 | Northwind Traders Gnocchi            |    38.0000 |
| 17 | Northwind Traders Fruit Cocktail     |    39.0000 |
|  8 | Northwind Traders Curry Sauce        |    40.0000 |
| 43 | Northwind Traders Coffee             |    46.0000 |
| 51 | Northwind Traders Dried Apples       |    53.0000 |
| 20 | Northwind Traders Marmalade          |    81.0000 |
+----+--------------------------------------+------------+
```

# 12. Insert a new row to table Suppliers with the following values: company = ‘Habeco’, last_name = ‘Nguyễn’, first_name = ‘Hồng Linh’ city = ‘Hanoi’, country_region =‘Vietnam’.

```sql
-- 12. Insert a new row to table Suppliers with the following values: company = ‘Habeco’,
-- last_name = ‘Nguyễn’, first_name = ‘Hồng Linh’ city = ‘Hanoi’, country_region =‘Vietnam’.
INSERT INTO Suppliers(company, last_name, first_name, city, country_region) VALUES ('Habeco', 'Nguyễn', 'Hồng Linh', 'Hanoi', 'Vietnam');
```

# 13. Insert a new product into table products with the following values: product_code = ‘TBTruc Bach’, SupplierID = the value corresponding to ‘Habeco’, list_price = 22, discontinued = 0, category = ‘Beverages’

```sql
-- 13. Insert a new product into table products with the following values: 
-- product_code = ‘TBTruc Bach’, SupplierID = the value corresponding to ‘Habeco’, list_price = 22, discontinued = 0, category = ‘Beverages’ 
INSERT INTO products(product_code, supplier_ids, list_price, discontinued, category) 
VALUES('TBTruc Bach', 11, 22, 0, 'Beverages');
```

# 14. Modify the information of ‘Truc Bach’: standard_cost = 18.

```sql
-- 14. Modify the information of ‘Truc Bach’: standard_cost = 18. 
UPDATE products 
SET standard_cost = 18
WHERE product_code = 'TBTruc Bach'; 
SELECT * FROM products;
```

# 15. Try deleting the row which is just inserted in table suppliers.

```sql
-- 15. Try deleting the row which is just inserted in table suppliers.
DELETE FROM Suppliers 
WHERE company = 'Habeco'
	AND last_name = 'Nguyễn'
    AND first_name = 'Hồng Linh'
    AND city = 'Hanoi'
    AND country_region = 'Vietnam';
```

Full source code:

```sql
SHOW DATABASES;
USE northwind;
SHOW TABLES;

-- 1. Write a query to get discontinued Product list (Product ID and name).
SELECT id, product_name
FROM Products
WHERE Discontinued = 1 
ORDER BY product_name;

-- 2. Retrive the top 4 cheapest products
SELECT id, product_name, list_price
FROM Products
ORDER BY list_price ASC
LIMIT 4;

-- 3. Write a query to get Product list (id, name, list_price) whose list_price cost between $15 and $25. Hint: using BETWEEN operator or comparison operators (<>) combined with AND operator. 
SELECT id, product_name, list_price
FROM Products
WHERE (list_price>=15) AND (list_price <=25)
ORDER BY list_price DESC;

SELECT id, product_name, list_price
FROM Products
WHERE list_price BETWEEN 15 AND 25;

-- 4. List employees with two columns: id, full_name which is constructed from
-- first_name and last_name.
SELECT id, concat(first_name,' ',last_name ) as full_name
FROM Employees;

-- 5. Find employees whose names start with ‘A’.
SELECT id, last_name, first_name
FROM Employees
WHERE first_name LIKE 'A%' OR last_name LIKE 'A%';

-- 6. Show how many different cities the employees living in. 
SELECT DISTINCT city
FROM employees;

-- 7. Show ship_name of table orders without duplicated values. 
SELECT DISTINCT ship_name
FROM Orders
ORDER BY id;

-- 8. Show the minimum, maximum of list price in Products table
SELECT MAX(list_price), MIN(list_price)
FROM products;

-- 9. Display the number of current (mean Discontinued = 0) products. 
SELECT count(*) AS number_products
FROM Products
WHERE Discontinued = 0;

-- 10. Show the average and standard deviation of the list_price of products.
SELECT
	AVG(list_price) as average_price,
    STDDEV(list_price) as standard_deviation
FROM Products;

-- 11. Use subquey, show Product list (name, list_price) expensive than the average price. 
SELECT id, product_name, list_price
FROM Products
WHERE list_price > 
	(
		SELECT AVG(list_price)
        FROM products
    )
ORDER BY list_price;

-- 12. Insert a new row to table Suppliers with the following values: company = ‘Habeco’,
-- last_name = ‘Nguyễn’, first_name = ‘Hồng Linh’ city = ‘Hanoi’, country_region =‘Vietnam’.
INSERT INTO Suppliers(company, last_name, first_name, city, country_region) VALUES ('Habeco', 'Nguyễn', 'Hồng Linh', 'Hanoi', 'Vietnam');

SELECT * FROM Suppliers;

-- 13. Insert a new product into table products with the following values: 
-- product_code = ‘TBTruc Bach’, SupplierID = the value corresponding to ‘Habeco’, list_price = 22, discontinued = 0, category = ‘Beverages’ 
INSERT INTO products(product_code, supplier_ids, list_price, discontinued, category) 
VALUES('TBTruc Bach', 11, 22, 0, 'Beverages');

SELECT * FROM Products;

-- 14. Modify the information of ‘Truc Bach’: standard_cost = 18. 
UPDATE products 
SET standard_cost = 18
WHERE product_code = 'TBTruc Bach'; 
SELECT * FROM products; 

-- 15. Try deleting the row which is just inserted in table suppliers.
DELETE FROM Suppliers 
WHERE company = 'Habeco'
	AND last_name = 'Nguyen'
    AND first_name = 'Hong Linh'
    AND city = 'Hanoi'
    AND country_region = 'Vietnam';
```