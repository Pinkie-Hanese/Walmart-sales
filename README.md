# Walmart Sales Analysis

## Table of Contents
- [Project overview](#project-overview)
- [Data Sources](#data-sources)
- [Tools](#tools)
- [Data Cleaning & Preparation](#data-cleaning-&-preparation)
- [Exploratory Data Analysis](#exploratory-data-analysis)
- [Data Analysis](#data-analysis)
- [Data Visualization](#data-visualization)
- [Results/Findings](#results/findings)
- [Recommendations](#recommendations)
- [References](#references)

## Project Overview

 This data analysis project aims to provide in-depth insights on the Walmart sales. Through an analysis of various aspects of this data, we seek to identify trends across different 
 temperatures, Holidays, and weeks. 

### Data Sources

 Sales Data: The data set used for this analysis "Walmart_sales.csv" file which contains detailed information about the sales made by the store.

### Tools
- Microsoft Exel- Cleaning data [download here](https://microsoft.com)
- SQL server- Data Analysis [download here](https://mySQL.com)
- Tableau - Data Visualization [download here](https://tableau.com)

### Data Cleaning & Preparation

 The following tasks were performed in the initial data preparation phase;
  1. Data examination
  2. Removing duplicates
  3. Handling missing values
  4. Fixing errors

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


      
### Results/Findings
The results from this analysis are as follows:
- The highest and lowest weekly sales were determined.
- Sales tend to increase around holidays.
- Average sales is highest in cold weather, meanimg people might be shopping more for winter-related products.

### Recommendations
Based on the analysis, the following actions are recommended;
1. Optimize inventory fr cld weather & holiday seasons.
   - Stock up on seasonal essentials (winter clthing, heaters, hot beverages etc)
   - Ensure the availability of hig-demand holiday items (gifts, decorations,festive foods)
     
2. Launch seasonal promotions & discounts
  - Offer holiday dicounts and winter sales promotions to attract more customers.
  - Bundle cold weather items together fpr upselling (winter essentials pack)
    
    
3. Enhance store operatins during peak periods.
   - Extend store hurs  during holidays and winter weends to capture nore foot traffic.
   - Hire seasonal staff to handle increased demand.
   - Ensure efficient restocking so shelves are always full. 
   

     ### References
     (https://kaggle.com)




  

