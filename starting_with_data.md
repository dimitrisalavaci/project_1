Question 1: 


Which countries had the most expensive products?


SQL Queries:


SELECT productprice, country
FROM all_sessions
ORDER BY productprice DESC


Answer: 


Top 5 countries with most expensive products would be United States, India and Japan.



Question 2: 


What were the 5 most ordered products?


SQL Queries:


SELECT orderedquantity, productname
FROM products
ORDER BY orderedquantity DESC



Answer:



The top 5 most ordered products were:
-the 22oz water bottle
-sunglasses
-journal with a pen 
-custom decals
-slim & slender lip balm



Question 3: 


How many unique full visitors are there?



SQL Queries:


SELECT COUNT(DISTINCT fullvisitorid) AS uniquevisitors
FROM analytics


Answer:


There are 34533 unique full visitors.


Question 4: 


Are there any products that are out of stock?


SQL Queries:


SELECT DISTINCT stocklevel, products
FROM products
WHERE stocklevel LIKE '0%'


Answer:

Yes, currently there are 190 products that are out of stock.


