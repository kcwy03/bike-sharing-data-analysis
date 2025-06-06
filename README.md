# bike-sharing-data-analysis
Data analysis project on bike-sharing data using SQL and Power BI

The project is an data analysis workflow that transforms raw Excel data into actionable business insights for Tone Bike, specifically focusing on their next year's pricing strategy.

The main goal was to answer a core business question: "Please provide recommendations on raising prices next year". To achieve this, a dashboard showing key performance metrics was requested, including hourly revenue, profit and revenue trends, seasonal revenue, and rider demographics

SQL Query:
```sql
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
```

Power BI Dashboard: ![Screenshot 2025-06-06 111150](https://github.com/user-attachments/assets/bf289761-cc61-4a40-88a9-da1df43a80c7)

Key visualizations included:
▪
A matrix for hourly revenue analysis, showing average revenue by hour and weekday.
▪
A combined chart showing monthly trends for riders (as bars), revenue, and profit (as lines).
▪
A bar chart for seasonal revenue.
▪
A donut chart for rider demographics (casual vs. registered).
▪
Key performance indicator (KPI) cards at the top displaying total riders, total revenue, total profit, and a calculated profit marginulated profit margin




Comparing 2021 and 2022:

![Screenshot 2025-06-06 113356](https://github.com/user-attachments/assets/b28f13f3-41f7-4238-855c-d63ef8f9b17d)



The price per ride increased by about 25% ($3.99 to $4.99) from 2021 to 2022.

Despite this price increase, the number of riders (demand) surprisingly increased by 64%.

The Price Elasticity of Demand was calculated as 2.56 (64% demand increase / 25% price increase). This is an unusual positive number, indicating that demand was very tolerant to the price increase, or that other strong market factors were boosting demand

The final recommendation was a conservative price increase of 10% to 15% for the next year, which would set the price between $5.49 and $5.74 per ride. It was suggested to start at the lower end (10%) to test the market

Other external market factors (like bikes becoming more popular or marketing efforts) might be influencing demand, which were not explored in this specific analysis.


