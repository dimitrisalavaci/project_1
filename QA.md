What are your risk areas? Identify and describe them.

- fullvisitorid and visitid must not have any null values
- fullvisitorid should not have any duplicates 

QA Process:

--checking to make sure there are no null values

SELECT fullvisitorid AS fullvisitorid
FROM all_sessions
WHERE fullvisitorid IS null 

SELECT visitid AS visitid
FROM all_sessions
WHERE visitid IS null

--checking to make sure there aren't any duplicates

SELECT DISTINCT fullvisitorid
FROM all_Sessions


