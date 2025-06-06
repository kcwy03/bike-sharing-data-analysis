# bike-sharing-data-analysis
Data analysis project on bike-sharing data using SQL and Power BI

The project is an data analysis workflow that transforms raw Excel data into actionable business insights for Tone Bike, specifically focusing on their next year's pricing strategy.

The main goal was to answer a core business question: "Please provide recommendations on raising prices next year". To achieve this, a dashboard showing key performance metrics was requested, including hourly revenue, profit and revenue trends, seasonal revenue, and rider demographics

SQL Query:
WITH cte AS 
(SELECT * 
    FROM bike_share_yr_0
UNION ALL
SELECT * 
    FROM bike_share_yr_1)

SELECT 
dteday,
season,
cte.yr,
weekday,
hr,
rider_type,
riders,
price,
COGS,
riders*price as revenue,
riders*price - COGS*riders as profit
    FROM cte
LEFT JOIN cost_table
ON cte.yr = cost_table.yr
