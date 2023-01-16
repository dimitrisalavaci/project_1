Answer the following questions and provide the SQL queries used to find the answer.

    
**Question 1: Which cities and countries have the highest level of transaction revenues on the site?**


SQL Queries:

SELECT country, city,
SUM(totaltransactionrevenue::REAL) AS totaltransactionrevenue
FROM all_sessions
WHERE totaltransactionrevenue IS NOT null
GROUP BY country, city
ORDER BY totaltransactionrevenue DESC



Answer:

The United States have the highest level of transaction revenues on the sites, and the top cities are between San Francisco, Sunnyvale, Atlanta, and Palo Alto. 


**Question 2: What is the average number of products ordered from visitors in each city and country?**


SQL Queries:

SELECT country, city,
AVG(sr.total_ordered::REAL) AS total_ordered
FROM all_sessions s
JOIN sales_report sr
ON s.productsku = sr.productsku
GROUP BY s.country, s.city
ORDER BY total_ordered DESC



Answer:

Saudia Arabia and Czechia have an average of 319 total products ordered, United States have 250.5 from the city Rexburg, Portugal has an average of 189 in Lisbon along with Sacramento in the US. Those are the top 5 highest averages. 



**Question 3: Is there any pattern in the types (product categories) of products ordered from visitors in each city and country?**


SQL Queries:

SELECT country, city, v2productcategory,
AVG(sr.total_ordered::REAL) AS total_ordered
FROM all_sessions s
JOIN sales_report sr
ON s.productsku = sr.productsku
GROUP BY s.country, s.city, v2productcategory
ORDER BY total_ordered DESC


Answer:

Majority of the orders are home/office purchases all around the world, and it's very consistent.



**Question 4: What is the top-selling product from each city/country? Can we find any pattern worthy of noting in the products sold?**


SQL Queries:


SELECT country, city, v2productname,
AVG(sr.total_ordered::REAL) AS total_ordered
FROM all_sessions s
JOIN sales_report sr
ON s.productsku = sr.productsku
GROUP BY s.country, s.city, v2productname
ORDER BY total_ordered DESC


Answer:

The top-selling product, especially in the United States is the Ballpoint LED Light Pen. The next top-selling product would be the stainless steel water bottle and after the water bottle is a journal. Based on this information, you can say this company sells products for people that are working full time and most likely from home.



**Question 5: Can we summarize the impact of revenue generated from each city/country?**

SQL Queries:

SELECT revenue, s.country, s.city
FROM analytics r
JOIN all_sessions s
ON r.fullvisitorid = s.fullvisitorid
WHERE revenue IS NOT null
GROUP BY revenue, s.country, s.city
ORDER BY revenue DESC

Answer:


The biggest impact of revenue generated is in the United States, New York, Atlanta, Sunnyvale, and Salem are near the top of the list. Panama also made it close to the top of the list, seems the revenue they have generated also made a big impact for their country.




