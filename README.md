##🔍 Project Title:
BlinkIT Grocery Sales Analysis Dashboard Using Excel, SQL & Power BI
________________________________________
##Project Overview:
This project focuses on uncovering key business insights from BlinkIT’s grocery retail data using a combination of Excel, SQL, and Power BI. The objective was to analyze sales performance, customer behavior, and outlet efficiency to support data-driven decision-making.
________________________________________
⚙️ Tools & Techniques Used:
•	Excel Power Query:
Used for data cleaning, handling missing values, and transforming raw data into an analysis-ready format.
•	SQL (PostgreSQL/MySQL):
Used for writing queries to extract meaningful insights such as:
o	Total sales by outlet and item type
o	Sales comparison based on item fat content
o	Outlet performance by size and location
o	Average ratings and item visibility patterns
•	Power BI:
Used to design a dynamic and interactive dashboard with slicers and visuals to explore:
o	📦 Total Sales, Average Sales, Total Items, and Average Rating
o	🏪 Outlet Performance by Type, Size, and Location
o	🧃 Sales by Product Category and Fat Content
o	📈 Sales Trends by Establishment Year
o	🎯 Custom filtering using outlet size, location, and item type
________________________________________
📊 Key Insights:
•	Tier 3 outlets generated the highest sales.
•	Low Fat items outperformed Regular items in total sales.
•	Fruits & Vegetables were the top-selling item category.
•	Medium-sized outlets contributed over 50% of total sales.
•	Supermarket Type1 outlets had the highest item visibility but lower average sales per item.
________________________________________
✅ Outcome:
The final Power BI dashboard provides a user-friendly interface for stakeholders to interactively explore sales metrics, compare outlet performance, and make informed business decisions.

SQL Query:-
BlinkIT Grocery Sales Analysis
Q1.find the top 5 highest-selling item types in Tier 3 locations
SELECT 
           item_type,
           ROUND(SUM(sales)::numeric,0) AS total_sales
FROM blinkit_grocery
WHERE outlet_location_type = 'Tier 3'
GROUP BY  1
ORDER BY 2 DESC
LIMIT 5;
----------------------------------------------------------------------------------------------------------------
Q2.Compare Average Sales Across Different Outlet Types Over the Years
SELECT
            outlet_type,
            outlet_establishment_year,
            ROUND(AVG(sales)::numeric,0) AS avg_sales
FROM blinkit_grocery
GROUP BY 1,2
ORDER BY 1,2 DESC;
----------------------------------------------------------------------------------------------------------------
Q3.Identify the Most Profitable Items by Average Sales
SELECT
             item_type,
	ROUND(AVG(sales)::numeric,0) AS avg_sales
FROM blinkit_grocery
GROUP BY 1
ORDER BY 2 DESC;
----------------------------------------------------------------------------------------------------------------

🔹 Sales Analysis

Q4.What are the total sales per outlet?
SELECT 
               outlet_identifier,
	  ROUND(SUM(sales)::numeric,0) AS total_sales
FROM blinkit_grocery
GROUP BY 1
ORDER BY 2 DESC;
-----------------------------------------------------------------------------------------------------------------
Q5. What is the average sales per item type?

SELECT 
               item_type,
	  ROUND(AVG(sales)::numeric,0) AS avg_sales
FROM blinkit_grocery
GROUP BY 1
ORDER BY 2 DESC;
-----------------------------------------------------------------------------------------------------------------
Q6. Which outlet type has the highest average sales?
SELECT 
               outlet_type,
	  ROUND(AVG(sales)::numeric,2) AS avg_sale
FROM blinkit_grocery
GROUP BY 1
ORDER BY 2 DESC
LIMIT 1;
----------------------------------------------------------------------------------------------------------------

🔹 Customer Behavior & Product Insights

Q7.What is the total sales for 'Low Fat' vs 'Regular' items?
SELECT
               item_fat_content,
	  SUM(sales) AS total_sales
FROM blinkit_grocery
GROUP BY 1;
----------------------------------------------------------------------------------------------------------------

Q8. Which item types are most visible on shelves (average visibility)?
SELECT
               item_type,
	  ROUND(AVG(item_visibility)::numeric,2) AS avg_visibility
FROM blinkit_grocery
GROUP BY 1
ORDER BY 2 DESC;
----------------------------------------------------------------------------------------------------------------


🔹 Outlet Performance
Q9. Which outlet location types generate the highest sales on average?
SELECT
               outlet_location_type,
	  ROUND(AVG(sales)::numeric,2) AS avg_sales
FROM blinkit_grocery
GROUP BY 1
ORDER BY 2 DESC;
----------------------------------------------------------------------------------------------------------------
Q10. Compare sales trends by establishment year.
SELECT
               outlet_establishment_year,
	  ROUND(SUM(sales)::numeric,2) AS total_sales
FROM blinkit_grocery
GROUP BY 1
ORDER BY 1 DESC;
---------------------------------------------------------------------------------------------------------------
🔹 Advanced / Scenario-Based
Q11. Which top 5 item identifiers had the highest sales overall?
SELECT
               item_identifier,
	  SUM(sales) AS total_sales
FROM blinkit_grocery
GROUP BY 1
ORDER BY 2 DESC
LIMIT 5;
---------------------------------------------------------------------------------------------------------------
Q12. What is the average rating for each outlet?
SELECT
               outlet_identifier,
	  ROUND(AVG(rating)::numeric,2) AS avg_rating
FROM blinkit_grocery
GROUP BY 1
ORDER BY 2 DESC;

Q13. Which outlets size contributed over 50% of total sales.
SELECT
               outlet_size,
	  SUM(sales) AS total_sales
FROM blinkit_grocery
GROUP BY 1
ORDER BY 2 DESC;
---------------------------------------------------------------------------------------------------------------
Q14.Which outlets type had the highest item visibility?
SELECT
               outlet_type,
	  SUM(item_visibility) AS total_item_visibility
FROM blinkit_grocery
GROUP BY 1
ORDER BY 2 DESC
LIMIT 1;

