# Walmart Sales Analysis

## Table of Contents
- [Introduction](#introduction)
- [Project overview](#project-overview)
- [Objectives](objectives)
- [Data Set](#data-set)
- [Tools](#tools)
- [Project Workflow](#project-workflow)
- [Exploratory Data Analysis](#exploratory-data-analysis)
- [Data Analysis](#data-analysis)
- [Data Visualization](#data-visualization)
- [Results/Findings](#results/findings)
- [Recommendations](#recommendations)
- [References](#references)

## Introduction

This data analysis project aims to provide in-depth insights on the Walmart sales. Through an analysis of various aspects of this data, we seek to identify Walmart's sales trends to understand how external factors like temperature and holidays impact revenue. The insights are intended to inform strategic decisisons such as promotional planning and inventory management.

## Project Overview

This project analyzes historical sales data from Walmart to uncover patterns and trends that influence weekly sales performance. The primary focus is to determine whether extenal factors -such as holidays andd temperature variations significantly affect sales. Based on these insights, actionable recommendations are provided to help Walmart make informed business decisions, particularly in sales forecasting, marketing and inventory management.

## Objectives
- Analyze weekly sales trends over time.
- Evaluate the impact of hlidays on sales.
- Examine how temperature fluctuations correlate with sales performance.
- Provide data-driven recommendations to optimize business strategies.

### Data set

- Source: (https://kagglewalmartsales.com)
- Content:
   - Weekly sales data across various walmart stores and departments.
   - External factors such as temperature,fuel prices,CPI and holiday indicators.

### Tools
- Microsoft Exel- Cleaning data [download here](https://microsoft.com)
- SQL server- Data Analysis [download here](https://mySQL.com)
- Tableau - Data Visualization [download here](https://tableau.com)

### Project Workflow
1. Data cleaning & Preparation
   - Data examination
   - Handled missing values
   - Standardized clumn names and data types
   - Removing duplicates
   - Handling missing values
   - Fixing errors
     
2.  Exploratory Data Analysis(EDA)
    - Sales performancee acroos different weeks and stores.
    - Impact analysis of holidays and seasonal factors.
     
3. Analysis & Insights
   - Identified significant sales increases during major holidays.
   - Observed higher average sales in clder weeks.

4. Visualization & Storytelling
   - Created Tableau dashboard to represent trends. (https://public.tableau.com/app/profile/pinkie.hanese/viz/WalmartSalesTablaeau/Dashboard1?publish=yes) 

### Exploratory Data Analysis

  For EDA, the sales data was explored in order to answer the following questions:
  1. What are the highest and lowest sales weeks in the dataset? What might explain these trends?
  2. How do weekly sales fluctuate over time? Are there any noticeable trends?
  3. Do sales significantly increase or decrease around holidays?
  4. How does temperature affect weekly sales? Do higher or lower temperatures lead to increased sales?
     

### Data Analysis
  1. What is the highest sales week in the dataset? What might explain these trends?
     ```sql
     select date,weekly_sales,holiday_flag,Temperature from walmart_sales
     order by weekly_sales desc
     limit 1;
     ```
     - What is the lowest sales week in the data set?
       ```sql
        select date,weekly_sales,holiday_flag,Temperature from walmart_sales
        order by weekly_sales asc
        limit 1;
       ```
  
   2. How do weekly sales fluctuate over time? Are there any noticeable trends?
      ```sql
         select date, weekly_sales,
         avg(weekly_sales) over (order by date rows between 4 preceding and current row) as moving_avg_5w,
         holiday_flag
         from walmart_sales
         order by date and weekly_sales desc;
      ```
  
   3. Do sales significantly increase or decrease around holidays?
      ```sql
      select holiday_flag,
      avg(weekly_sales) as avg_sales,
      count(*) as num_weeks
      from walmart_sales
      group by holiday_flag
      order by avg_sales desc;
      ```
   
   4. How does temperature affect weekly sales? Do higher or lower temperatures lead to increased sales?
       ```sql
           select
           case
           when temperature < 40 then 'cold' 
           when temperature between 40 and 70 then 'moderate'
           else 'hot'
           end as temp_category,
           avg(weekly_sales) as avg_sales, 
           count(*) as num_weeks
           from walmart_sales
           group by temp_category
           order by avg_sales desc;
       ```

### Data visualization

![Screenshot (34)_edit_184032005179209](https://github.com/user-attachments/assets/2897f17c-288d-4c45-b836-df5718061587)




      
### Results/Findings
The results from this analysis are as follows:
- The highest and lowest weekly sales were determined.
- Sales tend to increase around holidays.
- Average sales is highest in cold weather, meaning people might be shopping more for winter-related products.

### Recommendations
Based on the analysis, the following actions are recommended;
1. Optimize inventory for cold weather & holiday seasons.
   - Stock up on seasonal essentials (winter clthing, heaters, hot beverages etc)
   - Ensure the availability of high-demand holiday items (gifts, decorations,festive foods)
     
2. Launch seasonal promotions & discounts
  - Offer holiday dicounts and winter sales promotions to attract more customers.
  - Bundle cold weather items together fpr upselling (winter essentials pack)
    
    
3. Enhance store operatins during peak periods.
   - Extend store hours  during holidays and winter weends to capture nore foot traffic.
   - Hire seasonal staff to handle increased demand.
   - Ensure efficient restocking so shelves are always full. 
   

     ### References
     (https://kaggle.com)




  

