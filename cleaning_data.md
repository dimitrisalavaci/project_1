What issues will you address by cleaning the data?


1. Unit price needs to be divided by 1,000,000

2. Check if there are any duplicates

3. Check to see if there are unknown values and replace them

4. Check if there are any null values that would be a problem


Queries:
Below, provide the SQL queries you used to clean your data.

1. 

--Dividing unit price by 1,000,000 to get the correct value of the price and replacing the incorrect price with the correct one


SELECT unit_price :: decimal / 1000000 AS updated_unit_price
FROM analytics;

UPDATE analytics
SET unit_price = unit_price :: decimal / 1000000;


2. 

--Making sure there are no duplicates in the products sku table
 
SELECT sku, count(*)
FROM products
GROUP BY sku
HAVING COUNT(*) > 1;



3. 

--Check to see how many values have "not availble in demo dataset"
 
SELECT country, city
FROM all_sessions
WHERE city LIKE lower('%not available in demo dataset');

--Replace missing values with "null"

UPDATE all_sessions
SET city = 'null'
WHERE city LIKE lower ('%not available in demo dataset%');

--Check to see how many values have "not set"

SELECT country, city
FROM all_sessions
WHERE city LIKE lower('%not set%');

--Replace missing values with "null"

UPDATE all_sessions
SET city = 'null'
WHERE city LIKE lower ('%not set%');


4. 

--Check if there are any null values

SELECT COUNT(*)
FROM all_sessions
WHERE fullvisitorid IS null;



