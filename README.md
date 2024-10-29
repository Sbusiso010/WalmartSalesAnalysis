# WalmartSalesAnalysis

### Project Overview
This project aims to dive deep into the Walmart Sales data to uncover insights about the top-performing branches and products. I'll analyze sales trends across different product categories and customer behavior patterns. The goal is to identify areas where sales strategies can be improved and optimized for better performance. The dataset, sourced from the [Walmart Sales Forecast](https://kaggle.com), provides a rich foundation for my analysis. By studying this data, I aim to develop actionable recommendations that will help refine sales approaches and boost overall business outcomes for Walmart.

### Purpose of the Project
This project aims to gain insights into Walmart's sales data to understand factors affecting sales across branches. Analyzing top-performing products, sales trends, and customer behavior patterns will help develop strategies to improve and optimize sales. Data sourced from the Kaggle [Walmart Sales Forecast](https//kaggle.com).

### Data Source
This dataset, sourced from the [Walmart Sales Forecast](https//kaggle.com), includes sales transactions from three Walmart branches located in Mandalay, Yangon, and Naypyitaw. It comprises 17 columns and 1,000 rows, offering a comprehensive view of the sales data across these branches.
![Screenshot (31)](https://github.com/user-attachments/assets/6f4773b8-53ec-4e30-bc93-7b9781a3abb3)

### Tools
- MySQL Workbench

### Analysis Areas

- Product Analysis
   - Conduct analysis on the data to understand the different product lines, the products lines performing best and the product lines that need to be improved
- Sales Analysis
   - This analysis aims to answer the question of the sales trends of product. The result of this can help use measure the effectiveness of each sales strategy the business applies and what modificatoins are needed to gain more sales.
- Customer Analysis
   - This analysis aims to uncover the different customers segments, purchase trends and the profitability of each customer segment.

### Approach Utilized

1. Data Wrangling: This is the first step where inspection of data is done to make sure NULL values and missing values are detected and data replacement methods are used to replace, missing or NULL values.
- Buid Database
- Create table and insert values
- There are no null values in our database in creating tables, i set NOT NULL for each field, hence null values are filtered out.

 2. Feature Engineering: This will assist me to genrate new columns from existing ones.

  - Add a new column named time_of_day to give insight of sales in the Morning, Afternoon and Evening. This will help answer the question on which part of the day most sales are made.
  - Add a new column named day_name that contains the extracted days of the week on which the given transaction took place (Mon, Tue, Wed, Thur, Fri). This will help answer the question on which week of the day each branch is busiest.
  - Add a new column named month_name that contains the extracted months of the year on which the given transaction took place (Jan, Feb, Mar). Help determine which month of the year has the most sales and profit.  

3. Exploratory Data Analysis(EDA): Exploratory data analysis is done to answer the listed questions and aims of this projects.

## Business Questions To Address

### General Questions
1. How many unique cities does the data have?
2. In Which City is each branch located?

### Product
1. How many unique product lines does the data have?
2. What is the most common payment method?
3. What is the most selling product line?
4. What is the total revenue by month?
5. What month had the largest COGS?
6. What product line had the largest revenue?
7. What is the city with the largest revenue?
8. What product line had the largest VAT?
9. Which branch sold more products than average product sold?
10. What is the most common product line by gender?
11. What is the average rating of each product line?

### Sales
1. Number of sales made in each time of the day per weekday
2. Which of the customer types brings the most revenue?
3. Which city has the largest tax percent/ VAT (Value Added Tax)?
4. Which customer type pays the most in VAT?

### Customer   
1. How many unique customer types does the data have?
2. How many unique payment methods does the data have?
3. What is the most common customer type?
4. Which customer type buys the most?
5. What is the gender of most of the customers?
6. What is the gender distribution per branch?
7. Which time of the day do customers give most ratings?
8. Which time of the day do customers give most ratings per branch?
9. Which day fo the week has the best avg ratings?
10. Which day of the week has the best average ratings per branch?

### Revenue And Profit Calculations
$ COGS = unitsPrice * quantity $

$ VAT = 5% * COGS $

VAT is added to the COGS(Cost of Goods Sold) and this is what is billed to the customer.

$ total(gross_sales) = VAT + COGS $

$ grossProfit(grossIncome) = total(gross_sales) - COGS $

Gross Margin is gross profit expressed in percentage of the total(gross profit/revenue)

$ \text{Gross Margin} = \frac{\text{gross income}}{\text{total revenue}} $

###SQL Code
- For the rest of the code, [View SQL Data](data.sql)
 file


```sql
CREATE DATABASE walmartSales;
CREATE TABLE sales(
	invoice_id VARCHAR(30) NOT NULL PRIMARY KEY,
    branch VARCHAR(5) NOT NULL,
    city VARCHAR(30) NOT NULL,
    customer_type VARCHAR(30) NOT NULL,
    gender VARCHAR(30) NOT NULL,
    product_line VARCHAR(100) NOT NULL,
    unit_price DECIMAL(10,2) NOT NULL,
    quantity INT NOT NULL,
    tax_pct FLOAT(6,4) NOT NULL,
    total DECIMAL(12, 4) NOT NULL,
    date DATETIME NOT NULL,
    time TIME NOT NULL,
    payment VARCHAR(15) NOT NULL,
    cogs DECIMAL(10,2) NOT NULL,
    gross_margin_pct FLOAT(11,9),
    gross_income DECIMAL(12, 4),
    rating FLOAT(2, 1)
);  




