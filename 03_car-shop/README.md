# Car Shop

## Create a new database
Create a new database for this exercise.
```
CREATE DATABASE exercise_car_shop
use exercise_car_shop
```

## Setup the table 
Create a table named `cars` for a dealership with the following columns:
   - `car_id` (integer, primary key)
   - `make` (varchar, maximum length 50)
   - `model` (varchar, maximum length 50)
   - `year` (integer)
   - `price` (decimal, 2 decimal places)

> ANSWER
```SQL
CREATE TABLE cars
    -> (car_id INT PRIMARY KEY,
    -> make VARCHAR(50),
    -> model VARCHAR(50),
    -> year INT,
    -> price DECIMAL(10,2));

+--------+---------------+------+-----+---------+-------+
| Field  | Type          | Null | Key | Default | Extra |
+--------+---------------+------+-----+---------+-------+
| car_id | int           | NO   | PRI | NULL    |       |
| make   | varchar(50)   | YES  |     | NULL    |       |
| model  | varchar(50)   | YES  |     | NULL    |       |
| year   | int           | YES  |     | NULL    |       |
| price  | decimal(10,2) | YES  |     | NULL    |       |
+--------+---------------+------+-----+---------+-------+
```

## Add the car data
Insert at least five records into the `cars` table with the following data:
   - (1, 'Toyota', 'Camry', 2022, 25000.00)
   - (2, 'Honda', 'Accord', 2021, 27000.50)
   - (3, 'Ford', 'Mustang', 2023, 35000.75)
   - (4, 'Chevrolet', 'Equinox', 2022, 30000.25)
   - (5, 'Nissan', 'Altima', 2023, 28000.90)
   - (6, 'Tesla', 'Model 3', 2022, 48000.00)
   - (7, 'BMW', 'X5', 2023, 62000.50)
   - (8, 'Mercedes-Benz', 'C-Class', 2022, 55000.75)
   - (9, 'Audi', 'Q7', 2023, 59000.25)
   - (10, 'Lexus', 'RX', 2021, 48000.90)

> ANSWER
```SQL
INSERT INTO cars VALUES
    -> (1, 'Toyota', 'Camry', 2022, 25000.00),
    -> (2, 'Honda', 'Accord', 2021, 27000.50),
    -> (3, 'Ford', 'Mustang', 2023, 35000.75),
    -> (4, 'Chevrolet', 'Equinox', 2022, 30000.25),
    -> (5, 'Nissan', 'Altima', 2023, 28000.90),
    -> (6, 'Tesla', 'Model 3', 2022, 48000.00),
    -> (7, 'BMW', 'X5', 2023, 62000.50),
    -> (8, 'Mercedes-Benz', 'C-Class', 2022, 55000.75),
    -> (9, 'Audi', 'Q7', 2023, 59000.25),
    -> (10, 'Lexus', 'RX', 2021, 48000.90);

+--------+---------------+---------+------+----------+
| car_id | make          | model   | year | price    |
+--------+---------------+---------+------+----------+
|      1 | Toyota        | Camry   | 2022 | 25000.00 |
|      2 | Honda         | Accord  | 2021 | 27000.50 |
|      3 | Ford          | Mustang | 2023 | 35000.75 |
|      4 | Chevrolet     | Equinox | 2022 | 30000.25 |
|      5 | Nissan        | Altima  | 2023 | 28000.90 |
|      6 | Tesla         | Model 3 | 2022 | 48000.00 |
|      7 | BMW           | X5      | 2023 | 62000.50 |
|      8 | Mercedes-Benz | C-Class | 2022 | 55000.75 |
|      9 | Audi          | Q7      | 2023 | 59000.25 |
|     10 | Lexus         | RX      | 2021 | 48000.90 |
+--------+---------------+---------+------+----------+
```
## Updating records 
### 1. **Update Data**
Update the price of the 'Ford Mustang' to $38000.00.

> ANSWER
```SQL
UPDATE cars SET price = 30000.00 WHERE make = "Ford" AND model = "Mustang";

+--------+---------------+---------+------+----------+
| car_id | make          | model   | year | price    |
+--------+---------------+---------+------+----------+
|      1 | Toyota        | Camry   | 2022 | 25000.00 |
|      2 | Honda         | Accord  | 2021 | 27000.50 |
|      3 | Ford          | Mustang | 2023 | 30000.00 | <-
|      4 | Chevrolet     | Equinox | 2022 | 30000.25 |
|      5 | Nissan        | Altima  | 2023 | 28000.90 |
|      6 | Tesla         | Model 3 | 2022 | 48000.00 |
|      7 | BMW           | X5      | 2023 | 62000.50 |
|      8 | Mercedes-Benz | C-Class | 2022 | 55000.75 |
|      9 | Audi          | Q7      | 2023 | 59000.25 |
|     10 | Lexus         | RX      | 2021 | 48000.90 |
+--------+---------------+---------+------+----------+
```
### 2. **Conditional Update**
Increase the price of all cars made in 2022 by 5%.

> ANSWER
```SQL
UPDATE cars SET price = price + (price * 0.05) WHERE year = 2022;

+--------+---------------+---------+------+----------+
| car_id | make          | model   | year | price    |
+--------+---------------+---------+------+----------+
|      1 | Toyota        | Camry   | 2022 | 26250.00 |
|      2 | Honda         | Accord  | 2021 | 27000.50 |
|      3 | Ford          | Mustang | 2023 | 30000.00 |
|      4 | Chevrolet     | Equinox | 2022 | 31500.26 |
|      5 | Nissan        | Altima  | 2023 | 28000.90 |
|      6 | Tesla         | Model 3 | 2022 | 50400.00 |
|      7 | BMW           | X5      | 2023 | 62000.50 |
|      8 | Mercedes-Benz | C-Class | 2022 | 57750.79 |
|      9 | Audi          | Q7      | 2023 | 59000.25 |
|     10 | Lexus         | RX      | 2021 | 48000.90 |
+--------+---------------+---------+------+----------+
```
## Deleting records
### 1. **Delete Data:**
Delete the record of the car with `car_id` 3 from the `cars` table.

> ANSWER
 ```SQL
DELETE FROM cars WHERE car_id = 3;

+--------+---------------+---------+------+----------+
| car_id | make          | model   | year | price    |
+--------+---------------+---------+------+----------+
|      1 | Toyota        | Camry   | 2022 | 26250.00 |
|      2 | Honda         | Accord  | 2021 | 27000.50 |
|      4 | Chevrolet     | Equinox | 2022 | 31500.26 |
|      5 | Nissan        | Altima  | 2023 | 28000.90 |
|      6 | Tesla         | Model 3 | 2022 | 50400.00 |
|      7 | BMW           | X5      | 2023 | 62000.50 |
|      8 | Mercedes-Benz | C-Class | 2022 | 57750.79 |
|      9 | Audi          | Q7      | 2023 | 59000.25 |
|     10 | Lexus         | RX      | 2021 | 48000.90 |
+--------+---------------+---------+------+----------+
```
### 1. **Conditional Delete:**
Delete all cars with a price lower than $26000.00.

> ANSWER
```SQL
DELETE FROM cars WHERE price < 26000;
>> 0 <<
Query OK, 0 rows affected (0.00 sec)

+--------+---------------+---------+------+----------+
| car_id | make          | model   | year | price    |
+--------+---------------+---------+------+----------+
|      1 | Toyota        | Camry   | 2022 | 26250.00 |
|      2 | Honda         | Accord  | 2021 | 27000.50 |
|      4 | Chevrolet     | Equinox | 2022 | 31500.26 |
|      5 | Nissan        | Altima  | 2023 | 28000.90 |
|      6 | Tesla         | Model 3 | 2022 | 50400.00 |
|      7 | BMW           | X5      | 2023 | 62000.50 |
|      8 | Mercedes-Benz | C-Class | 2022 | 57750.79 |
|      9 | Audi          | Q7      | 2023 | 59000.25 |
|     10 | Lexus         | RX      | 2021 | 48000.90 |
+--------+---------------+---------+------+----------+
```
## Update and Delete more records
### 7. **Bulk Update:**
Update the prices of all 'Honda' cars to $28000.00.

> ANSWER
```SQL
UPDATE cars SET price = 28000.00 WHERE make = "Honda";

+--------+---------------+---------+------+----------+
| car_id | make          | model   | year | price    |
+--------+---------------+---------+------+----------+
|      1 | Toyota        | Camry   | 2022 | 26250.00 |
|      2 | Honda         | Accord  | 2021 | 28000.00 |
|      4 | Chevrolet     | Equinox | 2022 | 31500.26 |
|      5 | Nissan        | Altima  | 2023 | 28000.90 |
|      6 | Tesla         | Model 3 | 2022 | 50400.00 |
|      7 | BMW           | X5      | 2023 | 62000.50 |
|      8 | Mercedes-Benz | C-Class | 2022 | 57750.79 |
|      9 | Audi          | Q7      | 2023 | 59000.25 |
|     10 | Lexus         | RX      | 2021 | 48000.90 |
+--------+---------------+---------+------+----------+
```
### 8. **Bulk Delete:**
Delete all cars made in 2021.

> ANSWER
```SQL
DELETE FROM cars WHERE year = 2021;

+--------+---------------+---------+------+----------+
| car_id | make          | model   | year | price    |
+--------+---------------+---------+------+----------+
|      1 | Toyota        | Camry   | 2022 | 26250.00 |
|      4 | Chevrolet     | Equinox | 2022 | 31500.26 |
|      5 | Nissan        | Altima  | 2023 | 28000.90 |
|      6 | Tesla         | Model 3 | 2022 | 50400.00 |
|      7 | BMW           | X5      | 2023 | 62000.50 |
|      8 | Mercedes-Benz | C-Class | 2022 | 57750.79 |
|      9 | Audi          | Q7      | 2023 | 59000.25 |
+--------+---------------+---------+------+----------+
```

