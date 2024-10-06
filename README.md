# EDA-with-PostgreSQL-and-PowerBI

## OVERVIEW:
This dataset shows the call records of a call center which includes- reasons for calls, response to calls, call-center venue, city of the callers, state of the callers, sentiments, response time, channel, etc.
This dataset requires careful and thorough analysis/querying and I was saddled with the tasks of querying the dataset to be able to deduce actionable insights.

## Clauses and Concepts applied include:

SELECT 
GROUP BY
ORDER BY
COUNT (DISTINCT())
AVG()
ROUND()
Subqueries
Now, grab some popcorn and let's

CREATE TABLE Call_center (
                          ID VARCHAR,
                          CUSTOMER_NAME VARCHAR,
                          SENTIMENT VARCHAR,
                          CSAT_SCORE INT,
                          CALL_TIMESTAMP DATE,
                          REASON VARCHAR,
                          CITY VARCHAR,
                          STATE VARCHAR,
                          CHANNEL VARCHAR,
						  RESPONSE_TIME VARCHAR,
						  CALL_DURATION_IN_MINUTES INT,
						  CALL_CENTER VARCHAR);
						  
SELECT * FROM Call_center

## VISUALIZATION ANALYSIS 

---- CALLS BY SENTIMENT ---

SELECT Sentiment, COUNT (Customer_name) AS Total_no_of_customers
FROM Call_center
GROUP BY Sentiment
ORDER BY Total_no_of_customers DESC

---- CALLS BY CHANNEL ---

SELECT Channel, COUNT (Customer_name) AS Total_no_of_customers
FROM Call_center
GROUP BY Channel 
ORDER BY Total_no_of_customers DESC

--- REASONS FOR CALLS ---

SELECT Reason, COUNT (Customer_name) AS Total_no_of_customers
FROM Call_center
GROUP BY Reason
ORDER BY Total_no_of_customers DESC

--- CALLS BY TOP 10 STATES ---

SELECT State, COUNT (Customer_name) AS Total_no_of_customers
FROM Call_center
GROUP BY State
ORDER BY Total_no_of_customers DESC
LIMIT 10

--- NO OF CALLS BY CALL CENTER NAME ---

SELECT Call_center AS Call_center_name, COUNT (Customer_name) AS Total_no_of_customers
FROM Call_center
GROUP BY Call_center
ORDER BY Total_no_of_customers DESC

--- CALL TREND BY DAYNAME ---

SELECT TO_CHAR(Call_timestamp, 'Dy') As Dayname, Count(Customer_name) As Total_no_of_customers
FROM Call_center
GROUP BY Dayname
ORDER BY Total_no_of_customers DESC

--- TOP 10 CALLING CITIES  ---

SELECT City, COUNT (Customer_name) AS Total_no_of_customers
FROM Call_center
GROUP BY City
ORDER BY Total_no_of_customers DESC
LIMIT 10

--- CALLS BY RESPONSE TIME ---

SELECT Response_time, COUNT (Customer_name) AS Total_no_of_customers
FROM Call_center
GROUP BY Response_time
ORDER BY Total_no_of_customers DESC


SELECT * FROM Call_center 

 ## KPI'S
 
--- TOTAL NO OF CUSTOMERS ---

SELECT COUNT( DISTINCT id) AS Total_on_customers
FROM Call_center

--- AVERGAE CALL DURATION

SELECT AVG(Call_duration_in_minutes) AS Avg_call_duration
FROM Call_center


--- N0 1 REASON FOR CALLS ---

SELECT Reason, COUNT (Customer_name) AS Total_no_of_customers
FROM Call_center
GROUP BY Reason
ORDER BY Total_no_of_customers DESC
LIMIT 1


