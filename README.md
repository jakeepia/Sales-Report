# Sales Report Analysis

![](intro.JPG)

## Project Overview
This sales report analysis covers the period from 2010 to 2014, utilizing data extracted from the AdventureWorksDW2022 database with **SQL**. The primary goal of this project is to provide comprehensive insights into sales performance and trends over the specified period, using **Power BI** for visualization and analysis.

## Skills/ Concepts Demonstrated
- Data extraction and transformation using SQL.
- Advanced data analysis and visualization with Power BI.
- Application of DAX for detailed and dynamic business insights.

## Data Source
The data was sourced from SQL Server Management Studio, specifically from the _AdventureWorksDW2022_ database. The following tables were used:
- DimCustomer
- DimGeography
- DimProductCategory<br>
*A LEFT JOIN query was employed to combine the DimProductCategory table:*

<pre>
SELECT DimProduct.ProductKey, DimProductCategory.EnglishProductCategoryName
FROM DimProduct
LEFT JOIN DimProductSubcategory
ON DimProductSubcategory.ProductSubcategoryKey = DimProduct.ProductSubcategoryKey
LEFT JOIN DimProductCategory
ON DimProductCategory.ProductCategoryKey = DimProductSubcategory.ProductCategoryKey;
  </pre>

- FactInternetSales

<pre>
SELECT * FROM FactInternetSales
ORDER BY UnitPrice
  </pre>

## Data Model
A data model was created by establishing relationships between these tables to enhance the dataset for analysis. Specifically:

- DimCustomer was linked to FactInternetSales through the "CustomerKey".
- DimGeography was linked to DimCustomer through the "GeographyKey".
- DimProductCategory was linked to FactInternetSales through the "ProductKey".<br>

These relationships enabled a more comprehensive analysis, allowing for meaningful insights by connecting customer, product, location, and sales data across the dataset.

![](model.JPG)

## The purpose of this analysis is to:
1. **Evaluate Total Sales and Total Orders:** Understand overall sales performance and order volumes.
2. **Analyze Sales Trends:** Examine sales trends on a weekly basis (1 week, 4 weeks, 26 weeks, 52 weeks) using DAX.
3. **Calculate Running Totals:** Provide insights into cumulative sales performance over time.
4. **Transaction Analysis by Product:** Identify which products are driving sales.
5. **Geographical Sales Analysis:** Determine average sales amounts by country to understand geographical performance.

## DAX
- **Total Sales:**

- **Total Orders:**

- **Sales by Week:**

- **Running Total by Week:**

 - **Week Date:**

## Analysis and Visualization
### 1. Total Sales and Total Orders
- _Insight:_ Provides a high-level overview of sales volumes and order counts over the four-year period.
  
### 2. Sales by Week (1 week, 4 weeks, 26 weeks, 52 weeks)
- _Insight:_ Helps identify short-term and long-term sales trends, seasonal patterns, and potential anomalies.

### 3. Running Total by Week
- _Insight:_ Shows the cumulative sales growth over time, allowing for easy identification of periods with significant growth or decline.

### 4. Transaction by Product
- _Insight:_ Highlights the top-performing products and categories, aiding in inventory and marketing strategy decisions.

### 5. Average Amount by Country
- _Insight:_ Reveals geographical disparities in sales performance, guiding regional sales strategies.

## Dashboard

![](dashboard.JPG)

## Vital Recommendations
1. **Monitor and Optimize Sales Trends:** The sales trend shows significant growth in recent years, especially in 2013 and early 2014. Maintain the momentum by identifying and replicating successful strategies used during this period, such as seasonal promotions or new product launches.
 
2. **Capitalize on High-Performing Categories:** Accessories are the leading product category, contributing significantly to total sales. Focus on expanding this product line and related marketing efforts to maintain growth.
 
3. **Product Prioritization:** While accessories and bikes are key contributors, clothing have a smaller share. Explore opportunities to diversify and increase sales in underperforming categories, perhaps by bundling them with more popular products or offering targeted promotions.

4. **Customer Segmentation Focus:** The filters for gender, occupation, and country suggest that customer segmentation data is available. Leverage this information to tailor marketing strategies to specific segments, optimizing product offerings and promotions based on customer preferences.

## Conclusion
This sales report from 2010 to 2014 provides valuable insights into sales trends, product performance, and geographical sales distribution. By leveraging Power BI and DAX, the analysis offers clear and actionable insights that can inform strategic decisions and drive business growth. This project showcases the application of advanced data analytics techniques to real-world business data, demonstrating proficiency in SQL, DAX, and Power BI.



