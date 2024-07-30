# Sales Report Analysis

![](intro.JPG)

## Project Overview:
This sales report analysis covers the period from 2010 to 2014, utilizing data extracted from the AdventureWorksDW2022 database. The primary goal of this project is to provide comprehensive insights into sales performance and trends over the specified period, using Power BI for visualization and analysis.

## Skills/ concepts demonstrated:
- Data extraction and transformation using SQL.
- Advanced data analysis and visualization with Power BI.
- Application of DAX for detailed and dynamic business insights.

## Data Source:
The data was sourced from SQL Server Management Studio, specifically from the _AdventureWorksDW2022_ database. The following tables were used:
- DimCustomer
- DimGeography
- DimProductCategory
A LEFT JOIN query was employed to combine the DimProductCategory table:

<pre>
SELECT DimProduct.ProductKey, DimProductCategory.EnglishProductCategoryName
FROM DimProduct
LEFT JOIN DimProductSubcategory
ON DimProductSubcategory.ProductSubcategoryKey = DimProduct.ProductSubcategoryKey
LEFT JOIN DimProductCategory
ON DimProductCategory.ProductCategoryKey = DimProductSubcategory.ProductCategoryKey;
  </pre>
  
![](model.JPG)

## The purpose of this analysis is to:
1. Evaluate Total Sales and Total Orders: Understand overall sales performance and order volumes.
2. Analyze Sales Trends: Examine sales trends on a weekly basis (1 week, 4 weeks, 26 weeks, 52 weeks) using DAX.
3. Calculate Running Totals: Provide insights into cumulative sales performance over time.
4. Transaction Analysis by Product: Identify which products are driving sales.
5. Geographical Sales Analysis: Determine average sales amounts by country to understand geographical performance.

## Analysis and Visualization
### 1. Total Sales and Total Orders
- Insight: Provides a high-level overview of sales volumes and order counts over the four-year period.
  
### 2. Sales by Week (1 week, 4 weeks, 26 weeks, 52 weeks)
- Insight: Helps identify short-term and long-term sales trends, seasonal patterns, and potential anomalies.

### 3. Running Total by Week
- Insight: Shows the cumulative sales growth over time, allowing for easy identification of periods with significant growth or decline.

### 4. Transaction by Product
- Insight: Highlights the top-performing products and categories, aiding in inventory and marketing strategy decisions.

### 5. Average Amount by Country
- Insight: Reveals geographical disparities in sales performance, guiding regional sales strategies.

## DAX Formulas Used
- Total Sales:
<pre>
TotalSales = SUM(FactInternetSales[SalesAmount])
  </pre>

- Total Orders:
<pre>
TotalSales = COUNTROWS(FactInternetSales)
  </pre>

- Sales by Week:
<pre>
Sales4Weeks = CALCULATE(
    SUM(FactInternetSales[SalesAmount]),
    DATESINPERIOD(FactInternetSales[WeekDate], LASTDATE(FactInternetSales[WeekDate]), -28, DAY)
)
/
CALCULATE(
    DISTINCTCOUNT(FactInternetSales[WeekDate]),
    DATESINPERIOD(FactInternetSales[WeekDate], LASTDATE(FactInternetSales[WeekDate]), -28, DAY)
)
  
Sales26Weeks = CALCULATE(
    SUM(FactInternetSales[SalesAmount]),
    DATESINPERIOD(FactInternetSales[WeekDate], LASTDATE(FactInternetSales[WeekDate]), -182, DAY)
)
/
CALCULATE(
    DISTINCTCOUNT(FactInternetSales[WeekDate]),
    DATESINPERIOD(FactInternetSales[WeekDate], LASTDATE(FactInternetSales[WeekDate]), -182, DAY)
)
  
Sales52Weeks = CALCULATE(
    SUM(FactInternetSales[SalesAmount]),
    DATESINPERIOD(FactInternetSales[WeekDate], LASTDATE(FactInternetSales[WeekDate]), -365, DAY)
)
/
CALCULATE(
    DISTINCTCOUNT(FactInternetSales[WeekDate]),
    DATESINPERIOD(FactInternetSales[WeekDate], LASTDATE(FactInternetSales[WeekDate]), -365, DAY)
)
  </pre>

- Running Total by Week:
<pre>
CALCULATE(
    COUNT(FactInternetSales[CustomerKey]), 
    FILTER(
        ALLSELECTED(FactInternetSales),
        FactInternetSales[WeekDate] <= MAX(FactInternetSales[WeekDate])
    )
)
  </pre>

## Dashboard

![](dashboard.JPG)

## Conclusion
This sales report from 2010 to 2014 provides valuable insights into sales trends, product performance, and geographical sales distribution. By leveraging Power BI and DAX, the analysis offers clear and actionable insights that can inform strategic decisions and drive business growth. This project showcases the application of advanced data analytics techniques to real-world business data, demonstrating proficiency in SQL, DAX, and Power BI.



