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
