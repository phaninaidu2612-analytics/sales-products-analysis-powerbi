# Sales & Promotion Analysis Dashboard | Power BI

## Dashboard Link :

https://app.powerbi.com/view?r=eyJrIjoiMGM1YzRkMzUtYzdkMC00MDUyLWEwNDAtMzcxMDI2MWQ5NTRhIiwidCI6IjA2Y2Q0ZWQ1LTNiN2YtNDdiMC04ZWY2LTI5ZGVlMWM1MDYwYiJ9&pageName=e80b2ad7f871bbcdc5eb

## Dashboard Preview :

![dashboard](https://github.com/user-attachments/assets/6977f5e1-86e5-4ac0-9e24-ed6c4720ccf4)

## Problem Statement :

This project focuses on analyzing sales transactions, customer purchases, product performance, and promotional impacts using Power BI.

The objective of the dashboard is to:

Track total sales and net sales performance
Analyze the impact of promotions and discounts
Understand customer and product trends
Build a complete star-schema based sales model using fact and dimension tables

The dashboard enables business stakeholders to make data-driven decisions regarding sales strategy, product performance, and promotional effectiveness.

## Data Source & Integration :
Imported raw sales data from Excel Workbook into Power BI
Built a star schema model using:
- 3 Dimension Tables
- 1 Fact Table

Performed table relationships and data integration using Power Query Editor.

![model](https://github.com/user-attachments/assets/c346c74e-6c99-4072-810f-b9a42660b4af)

## Dataset Description :

**Dimension Tables**
1. Customers Table : 
- Customer ID
- Customer Name
- City
- State
- Pincode
- EmailID
- Phone Number
2. Products Table :
- ProductID
- Product Name
- Product Line
- Price (INR)
3. Promotion Table :
- PromotionID
- Promotion Name
- Ad Type
- Coupon Code
- Price Reduction Type
4. Fact Table
- Date (dd/mm/yyyy)
- CustomerID
- PromotionID
- Product ID
- Units Sold
- Price Per Unit
- Total Sales
- Discount Percentage
- Discount Value
- Net Sales

## Data Cleaning & Transformation (Power Query) : 

Initially, the following columns in the fact table contained null values:

- Price Per Unit
- Total Sales
- Discount Percentage
- Discount Value
- Net Sales

These values were calculated and populated using data from the dimension tables.

Data Transformation Steps

Product Merge
Merged:
Product ID from Fact Table
ProductID from Products Table
Extracted:
Product Price → mapped to Price Per Unit

**Total Sales Calculation** : 

Calculated:

Total Sales = Units Sold × Price Per Unit

![c1](https://github.com/user-attachments/assets/096f0de3-fc27-4bfb-bb99-d82b4248e846)

Promotion Merge
Merged Fact Table with Promotion Table using PromotionID
Extracted numerical discount values from:
Price Reduction Type

**Discount Calculation**:

Calculated:

Discount Value = (Total Sales × Discount Percentage) / 100

![c2](https://github.com/user-attachments/assets/3bec4797-b6f4-4bee-ba17-4566595e8440)

**Net Sales Calculation**:

Calculated:

Net Sales = Total Sales - Discount Value

![c3](https://github.com/user-attachments/assets/f24434e1-780f-4bf4-a7b4-e11edc6a2923)

**Additional Transformations**:
- Changed column data types
- Reordered columns
- Removed unnecessary columns
- Prepared final fact table with enriched values from dimension tables

## Dashboard Features : 
- Interactive sales dashboard built using a Star Schema Data Model (3 Dimension Tables + 1 Fact Table)
- Advanced Power Query transformations to populate missing sales, discount, and net sales values
- Dynamic analysis using:
 - Bookmark Selector
 - Edit Interactions
 - Top & Bottom N Filters
 - Slicer-based filtering
- Product performance analysis by:
 - Sales
 - Quantity Sold
 - Profit
- Promotion-wise discount analysis and campaign effectiveness tracking
- City-wise sales distribution using Map Visualizations
- Profit vs Net Sales correlation analysis
- Time-series sales trend analysis for identifying seasonal and promotional spikes
- KPI monitoring for:
 - Total Orders
 - Total Sales
 - Discount Impact
 - Net Sales Performance

![bm](https://github.com/user-attachments/assets/f5a405af-d839-495d-ab7c-5a613c402a5a)

### DAX Measures Used for edit interactions:

**Total Quantity calculation** :

Total Quantity = 
CALCULATE(
    SUM('Fact table'[Units Sold]),
    ALL('Date table 1'),
    USERELATIONSHIP('date table 2'[Date], 'Fact table'[Date (dd/mm/yyyy)])
) 


**Total Profit calculation** : 

Total Profit = 
CALCULATE(
    SUM('Fact table'[Profit]),
    ALL('Date table 1'),
    USERELATIONSHIP('date table 2'[Date], 'Fact table'[Date (dd/mm/yyyy)])
)

**Total sum of sales**:

Sum of Net Sales = 
CALCULATE(
    SUM('Fact table'[Net Sales]),
    ALL('Date table 1'),
    USERELATIONSHIP('date table 2'[Date], 'Fact table'[Date (dd/mm/yyyy)])
)


![tb](https://github.com/user-attachments/assets/89c6e328-3797-46ce-a855-58dcfbaec51d)



![ei](https://github.com/user-attachments/assets/8e53f227-e7e1-4673-8178-29324baf4dc0)

![dm](https://github.com/user-attachments/assets/f1e4e8a1-8cf8-4692-95a5-85fce07443d2)

## Key Insights : 

- **Product Performance**:
Premium electronic products such as Apple iPhone 14, MacBook Air, and Sony Bravia TV generate the highest sales and profitability.
High sales quantity does not always guarantee high profit margins.

- **Promotion Effectiveness**:
Weekend Flash Sale and Clearance Sale contribute the highest customer engagement and discount activity.
Discounts increase sales volume but can reduce overall net profit margins.

- **Regional Sales Trends**:
Major metropolitan cities including Mumbai, Delhi, Bangalore, and Kolkata contribute significantly to total sales performance.
Urban regions demonstrate stronger purchasing behavior and higher transaction activity.

- **Profitability Analysis**:
A strong positive relationship exists between Profit and Net Sales, indicating higher-performing transactions directly improve business profitability.
Pricing and discount strategies significantly influence net sales outcomes.

- **Time-Based Sales Analysis**:
Sales trends fluctuate across different periods due to:
Seasonal demand
Promotional campaigns
Product popularity
Certain time periods show noticeable sales spikes driven by promotional strategies and customer demand patterns.

- **Business Impact**:
The dashboard helps businesses:
Identify top and low-performing products
Optimize promotional campaigns
Track regional sales growth
Improve pricing strategies
Monitor overall sales and profitability performance

## Tools & Technologies Used : 
- Power BI Desktop
- Power Query Editor
- Excel Workbook
- Data Modeling (Star Schema)
- DAX
- Interactive Visualizations

## Conclusion :

This project demonstrates a complete sales analytics workflow involving:

- Data modeling using fact and dimension tables
- Data transformation using Power Query
- Business metric calculations
- Interactive dashboard development in Power BI

The dashboard provides valuable insights into sales performance, promotional effectiveness, and customer purchasing behavior.tion
