# Bike Shop Analysis
### Project Overview

 develop a dashboard for "Toman Bike Shop" that displays our key performance metrics for informed decision-making.
Requirements:
.
Hourly Revenue Analysis
• Profit and Revenue Trends:
• Seasonal Revenue
• Rider Demographics

### Data Source
the primary dataset used for this analysis is the "bike_share_yr_0.csv", "bike_share_yr_1.csv", "cost_table.csv", containing detailed information about each sale made by company.

### Tools
- Excel
- Microsoft SQL Server Managemen Studio
- Microsoft Power BI

### Data Cleaning/Preparation
- Data loading and inspection.
- Handling missing values.
- Data cleaning and formatting.

### Exploratoty Data Analysis

- Peak Hours and the Most Profitable Seasons:
  -Identifying the times of day and seasons that generate the highest revenue and profits.
  
- Which Type of Users Are More Profitable (Casual vs. Registered):
Determining whether casual users or registered users contribute more significantly to your revenue and profit margins.

- How Pricing and Costs Affect Revenue and Profit:
Understanding the relationship between your pricing strategy, operational costs, and their impact on overall financial performance.

- Factors Influencing Business Performance and How This Data Can Be Used to Make Decisions, Including Price Adjustments or Other Strategies:

- Identifying key drivers of business success and leveraging data insights to inform strategic decisions, such as adjusting prices or implementing new business strategies.

### Data Analysis

```sql
with cte as (
select * from bike_share_yr_0
union all
select * from bike_share_yr_1)

select 
dteday,
season,
a.yr,
weekday,
hr,
rider_type,
riders,
price,
COGS,
riders * CAST(price AS DECIMAL(10,2)) AS revenue,
riders * CAST(price AS DECIMAL(10,2)) - CAST(COGS AS DECIMAL(10,2)) AS profit

from cte a
left join cost_table b
on a.yr = b.yr
```

### Findings/Result
- KPI Over Time
The graph shows the comparison of the number of riders, profit, and revenue by month.
![KPI Overtime](https://github.com/user-attachments/assets/b7a6c546-9dab-4467-9c79-356c0c5f07c8)

- Peak Hours:
Morning (07:00 - 09:00): A high number of users is likely during this time as people are commuting to work or school.
Evening (17:00 - 19:00): There's an increase in users again as people return from work.
Weekends (10:00 - 14:00): A spike in casual users can be seen, likely using bikes for leisure or recreational activities.
![hr per week](https://github.com/user-attachments/assets/7c1ddc8c-3d63-4e14-98c7-71419ec552d9)

- The Most Profitable Seasons
The graph indicates that Season 3 is the most profitable, followed by Season 2, then Season 4, with Season 1 generating the lowest profit.
  ![revenue by season](https://github.com/user-attachments/assets/f4757f79-08a4-4dcb-91de-60a1a65451df)

- User
  - Registered Riders:
Revenue Contribution: Account for approximately 82% of total revenue.
Usage Frequency: High

  - Casual Riders:
Revenue Contribution: Account for approximately 18% of total revenue.
Usage Frequency: Low
![rider by demographic](https://github.com/user-attachments/assets/d2dc8c88-b11b-4343-b538-f923291f758b)

### Dashboard
![Dashboard](https://github.com/user-attachments/assets/3006daef-aa6f-4094-a397-a19572acfc99)

### Recommendation 

Recommendation
- Conservative Increase: Considering the substantial increase last year, a more conservative increase might be prudent to avoid hitting a price ceiling where demand starts to drop. An increase in the range of 10-15% could test the market's response without risking a significant loss of customers.
  
- Price Setting:
If the price in 2022 was $4.99, a 10% increase would make the new price about $5.49.
A 15% increase would set the price at approximately $5.74.

- Recommended Strategy:
  - Market Analysis: Conduct further market research to understand customer satisfaction, potential competitive changes, and the overall economic environment. This can guide whether leaning towards the lower or higher end of the suggested increase.
  - Segmented Pricing Strategy: Consider different pricing for casual versus registered users, as they may have different price sensitivities.
  - Monitor and Adjust: Implement the new prices but be ready to adjust based on immediate customer feedback and sales data. Monitoring closely will allow you to fine-tune your pricing strategy without committing fully to a price that might turn out to be too high. 









