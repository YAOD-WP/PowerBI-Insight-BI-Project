# Dynamic Sales Performance & Profitability Analysis Dashboard

## Project Overview

This project delivers a comprehensive Business Intelligence solution, transforming raw transactional data into actionable insights for sales performance and profitability analysis. Designed with scalability and user accessibility in mind, this solution leverages Microsoft's robust ecosystem, integrating **Azure SQL Database** for data warehousing with **Power BI** for dynamic visualization and reporting. The goal was to empower business stakeholders with an intuitive, interactive dashboard to monitor key performance indicators, identify trends, understand brand-level performance, and ultimately support strategic decision-making.

**Live Interactive Report:** [https://app.powerbi.com/reportEmbed?reportId=2806c617-61b9-41ab-926b-45953790cd9c&appId=fae0d82f-8ee0-44e5-b6ce-e82c7165ded2&autoAuth=true&ctid=6e2cc058-79af-4df8-92e6-ee6e0d1dea3e&actionBarEnabled=true](https://app.powerbi.com/reportEmbed?reportId=2806c617-61b9-41ab-926b-45953790cd9c&appId=fae0d82f-8ee0-44e5-b6ce-e82c7165ded2&autoAuth=true&ctid=6e2cc058-79af-4df8-92e6-ee6e0d1dea3e&actionBarEnabled=true)

---

## Technical Architecture & Skills Demonstrated

This project showcases a versatile skill set vital for any aspiring Data Analyst or Business Intelligence Developer. Each phase of the project was executed with best practices in mind, focusing on efficiency, accuracy, and user experience.

### 1. Data Ingestion & Cloud Data Warehousing (Azure SQL Database)

* **Skill:** Cloud Database Management, ETL Fundamentals, Scalable Data Storage.
* **Implementation:** The initial dataset, provided in CSV format, was efficiently loaded and managed within **Azure SQL Database**. This strategic choice ensures:
    * **Scalability:** Ability to handle increasing data volumes without significant performance degradation.
    * **Reliability & Security:** Leveraging Azure's robust infrastructure for data integrity and access control.
    * **Accessibility:** Providing a centralized, accessible data source for Power BI and potential future applications.
* **Process:**
    * **Database Provisioning:** Set up an Azure SQL Database instance with appropriate performance tiers.
    * **Data Loading:** Utilized bulk insert methods (e.g., SQL import/export wizard or Azure Data Factory if the scale was larger) to ingest the CSV data into a dedicated table.
    * **Schema Design:** Ensured optimal column data types and indexing (if applicable for larger datasets) for query performance.

### 2. Data Cleaning & Transformation (SQL & Power Query M)

* **Skill:** Data Wrangling, Data Quality, ETL Processes, SQL Scripting, Power Query (M Language).
* **Implementation:** Data quality is paramount for reliable insights. A multi-stage approach was adopted:
    * **Pre-processing with SQL (Optional but good practice):** For initial clean-up of common issues like duplicates, inconsistent casing, or basic data type corrections directly at the source, reducing load on Power BI. (If specific SQL scripts were used for this, mention them, e.g., "SQL scripts in `sql_scripts/data_preparation.sql` handled initial normalization.")
    * **Advanced Transformations with Power Query:** Within Power BI Desktop, **Power Query Editor** was extensively used. This involved:
        * **Handling Missing Values:** Identifying and addressing nulls or empty strings strategically (e.g., replacing with "N/A" or appropriate defaults).
        * **Data Type Enforcement:** Ensuring correct data types for all columns to prevent aggregation errors.
        * **Text Transformations:** Cleaning and standardizing text fields (e.g., trimming whitespace, converting to proper case).
        * **Custom Column Creation:** Dynamically creating new columns derived from existing data using Power Query's M language for improved analytical capabilities *before* loading into the data model.

### 3. Data Modeling & Advanced DAX Calculations

* **Skill:** Dimensional Modeling, Relationship Management, DAX (Data Analysis Expressions), Analytical Thinking.
* **Implementation:** A well-structured data model is the backbone of an efficient and insightful Power BI report.
    * **Star Schema Principles:** While this project might involve a single fact table for simplicity, the underlying principles of separating facts (sales figures) from dimensions (brands, products, time) were considered to ensure scalability and ease of analysis.
    * **Relationship Management:** Established clear and accurate relationships between tables to enable correct data filtering and cross-table calculations.
    * **Measures & Calculated Columns with DAX:** This is where raw data was transformed into meaningful business metrics. Key DAX expressions created include:
        * `Discount %`: `DIVIDE([Total Discount], [Total Sales], 0)` - Calculated the average discount rate across transactions.
        * `Profit %`: `DIVIDE([Total Profit], [Total Sales], 0)` - Determined profitability margins.
        * `Cost Price Column`: (If this was a calculated column, explain how, e.g., `Sales Amount - Profit Amount` or `Sales Amount / (1 + Markup)`)
        * **Other Potential DAX (if applicable):** Time Intelligence functions (YTD, MTD), RANKX for top/bottom N analysis, filtering with CALCULATE, etc. Each DAX formula was designed for efficiency and accuracy, adhering to best practices for optimal report performance.

### 4. Interactive Dashboard Design & Data Visualization

* **Skill:** UX/UI Principles, Data Storytelling, Visual Best Practices, Power BI Visualization Library.
* **Implementation:** The dashboard was designed to be intuitive, visually appealing, and highly interactive, providing a comprehensive view of sales performance.
    * **User-Centric Design:** Focused on the end-user's needs, starting with a high-level overview and allowing for drill-down capabilities.
    * **Multi-Page Reporting:** Organized insights across logical pages (e.g., "Brands Overview," "Details") to prevent information overload and guide the user through the data story.
    * **Strategic Visual Selection:** Employed a diverse range of Power BI visuals, each chosen for its effectiveness in conveying specific insights:
        * **Bar Charts:** Ideal for comparing discrete categories (e.g., "Top % Brands by Average Discount %").
        * **Donut Charts:** Effectively represented part-to-whole relationships (e.g., "Top % Brands by highest number of varieties").
        * **Ribbon Charts:** Demonstrated rank changes over time or across categories (e.g., "Top 6 brands by average sales price").
        * **Area Charts:** Showcased trends and magnitudes (e.g., "Top 6 brands by highest average profit %").
        * **Circle Graphs (Pie/Donut variants):** For proportional distribution (e.g., "Bottom 5 brands by average profit %").
    * **Filtering & Slicing:** Incorporated interactive slicers and filters to allow users to dynamically explore data by various dimensions (e.g., Brand, Date).
    * **Branding & Aesthetics:** Maintained a clean, professional aesthetic with consistent color palettes and font styles for enhanced readability and user experience.

### 5. Deployment & Sharing (Power BI Service & Apps)

* **Skill:** Power BI Service Administration, Report Publishing, Collaboration, Secure Sharing.
* **Implementation:** The final report was deployed to the **Power BI Service** and shared as a **Power BI App**, demonstrating knowledge of enterprise-level report distribution.
    * **Publishing to Service:** Published the `.pbix` file from Power BI Desktop to a dedicated workspace in the Power BI Service.
    * **Gateway Configuration (Implicit):** Understood the need for a data gateway if the Azure SQL Database were on-premises, ensuring scheduled data refreshes. (Though for Azure SQL, direct cloud connection is often feasible.)
    * **App Creation & Management:** Packaged the report into a Power BI App. This method provides:
        * **Centralized Access:** Users access reports from a single, organized location.
        * **Version Control:** Easier management of updates and new content.
        * **Audience-Specific Access:** Controlled access permissions, ensuring only authorized users view the report.

---

## Technical Stack

* **Cloud Database:** Microsoft Azure SQL Database
* **Business Intelligence & Visualization:** Microsoft Power BI Desktop, Power BI Service
* **Query Languages:** SQL (for initial data handling), DAX (Data Analysis Expressions for calculations), M (Power Query for data transformation)
* **Data Source:** CSV (transformed and loaded into Azure SQL)

---

## Project Structure

This repository is organized to provide clarity and easy navigation for reviewers:
├── data/
│   └── original_sales_data.csv         # (Optional) A sample or placeholder for the original dataset.
│                                       # Contains raw data with columns: Brand, Title, Original Price, Sale Price
├── powerbi_report/
│   └── Sales_Performance_Dashboard.pbix # Power BI file with data model, queries, and interactive dashboard
├── sql_scripts/
│   └── create_table_sales.sql           # SQL script to create the table in Azure SQL Database
│   └── insert_data_sales.sql            # (Optional) Script to insert cleaned data into the table
│   └── initial_data_cleaning.sql        # (Optional) SQL script for pre-processing or data transformations
├── images/
│   └── dashboard_overview_1.jpg         # Screenshot of the Brands Overview Dashboard
│   └── dashboard_details_2.png          # Screenshot of the Detailed Sales Analysis Dashboard
├── README.md                            # Project documentation (this file)
└── .gitignore                           # Ensures unnecessary files are not committed to version control

## Dashboard Walkthrough & Key Insights

The interactive dashboard provides a holistic view of sales performance, empowering users to slice and dice data to reveal specific insights.

### Page 1: Brands Overview

![Brands Overview Page](images/dashboard_overview_1.jpg)
*Figure 1: Brands Overview Page - Providing a high-level summary of brand performance and key metrics.*

This page acts as a landing point, showcasing:
* **Available Brands:** A comprehensive list for context.
* **Overall Performance Metrics:** Summaries of key sales figures.
* **Visual Appeal & Navigation:** Designed to be engaging while guiding the user to deeper analysis.

### Page 2: Detailed Sales Analysis

![Detailed Sales Analysis Dashboard](images/dashboard_details_2.png)
*Figure 2: Detailed Sales Analysis Dashboard - Drilling down into specific performance indicators for in-depth analysis.*

This page offers granular insights through various interactive visuals:
* **Top % Brands by Average Discount %:** Identifies brands with the highest average discount rates, prompting questions about pricing strategies and profitability.
* **Top % Brands by highest number of varieties:** Shows brands with the broadest product offerings, indicating portfolio diversity.
* **Top % Brands by highest Average Sale price:** Highlights premium brands or those with higher-value items.
* **Top 6 Brands by highest average profit % & Bottom 5 Brands by average Profit %:** Crucial for understanding profitability drivers and identifying underperforming areas. This direct comparison enables focused strategic interventions.

---

## Future Enhancements (Roadmap)

This project lays a strong foundation, and potential future enhancements could include:

* **Time Intelligence:** Implementing more advanced DAX for year-over-year, quarter-over-quarter comparisons, and moving averages.
* **What-If Analysis:** Adding parameters to simulate different scenarios (e.g., impact of discount changes on profit).
* **Row-Level Security (RLS):** Implementing RLS in Power BI Service to control data visibility based on user roles.
* **Integration with Other Data Sources:** Combining sales data with marketing, inventory, or customer demographics for a 360-degree view.
* **Automated Data Refresh:** Setting up scheduled data refreshes from Azure SQL to Power BI Service.
* **Power BI Goals/Scorecards:** Integrating key metrics into Power BI Goals for performance tracking against targets.
---

## MySQL SQL Queries for Data Exploration & Analysis

This section contains a comprehensive set of SQL queries used throughout the project for data exploration, cleaning, and preliminary analysis within the `MenTshirt` table. These queries demonstrate proficiency in SQL for data manipulation, quality checks, and deriving insights directly from the database.

**Note:** For practical deployment in your GitHub repository, it's recommended to place this SQL script in a separate file (e.g., `sql_scripts/men_tshirt_analysis_mysql.sql`) and simply link to it here. However, for a self-contained `README.md` that showcases everything at a glance, embedding it directly is also effective.

```sql
-- MYSQL server Script for Men's T-shirt Sales Analysis
-- Database: MySQL Server
-- Table: MenTshirt (Assuming 'dbo.' prefix is not used in MySQL, and table name is 'MenTshirt' or 'men_tshirt')
-- Note: MySQL table names are case-sensitive on Linux, but not on Windows by default.
-- It's good practice to use consistent casing, typically snake_case (e.g., men_tshirt)

-- Schema of the 'MenTshirt' table based on provided image:
-- Brand         VARCHAR(50) NOT NULL
-- Title         VARCHAR(100) NOT NULL
-- Original_Price TEXT
-- Sale_Price    TEXT

-- ====================================================================
-- SECTION 1: Data Exploration and Basic Retrieval
-- These queries help in understanding the structure and content of the MenTshirt table.
-- ====================================================================

-- 1.1. Select All Data (Initial View)
-- Purpose: To get a quick overview of all columns and a sample of rows in the table.
--          Essential for initial data inspection.
-- Skill Showcased: Basic SELECT statement, understanding table contents.
SELECT
    Brand,
    Title,
    Original_Price,
    Sale_Price
FROM
    MenTshirt -- Adjusted for MySQL table naming convention
ORDER BY
    Brand, Title
LIMIT 100; -- MySQL equivalent of TOP/FETCH NEXT

-- 1.2. Count Total Records
-- Purpose: To determine the total number of entries in the dataset.
--          Useful for understanding data volume.
-- Skill Showcased: COUNT() aggregate function, understanding dataset size.
SELECT
    COUNT(*) AS TotalRecords
FROM
    MenTshirt;

-- 1.3. List Unique Brands
-- Purpose: To identify all distinct brands present in the dataset.
--          Important for categorical analysis and understanding data diversity.
-- Skill Showcased: DISTINCT keyword, categorical data identification.
SELECT DISTINCT
    Brand
FROM
    MenTshirt
ORDER BY
    Brand;

-- 1.4. Count Products per Brand
-- Purpose: To see how many t-shirts are listed under each brand.
--          Helps in understanding brand distribution.
-- Skill Showcased: GROUP BY, COUNT(), ORDER BY with aggregate functions.
SELECT
    Brand,
    COUNT(Title) AS NumberOfProducts
FROM
    MenTshirt
GROUP BY
    Brand
ORDER BY
    NumberOfProducts DESC;

-- ====================================================================
-- SECTION 2: Data Type Conversion & Cleaning
-- Given Original_Price and Sale_Price are stored as TEXT, these queries
-- demonstrate handling potential data quality issues and safe conversion.
-- ====================================================================

-- 2.1. Inspect Non-Numeric Price Values
-- Purpose: To identify rows where Original_Price or Sale_Price cannot be cleanly
--          converted to a numeric type. Crucial for data cleaning before calculations.
-- Skill Showcased: REGEXP (for pattern matching in MySQL), WHERE clause for data validation,
--                  understanding data type inconsistencies.
-- Note: MySQL does not have TRY_CAST. We use regular expressions to find non-numeric strings.
-- This regex matches strings that are NOT entirely digits, a single decimal point, and digits.
SELECT
    Brand,
    Title,
    Original_Price
FROM
    MenTshirt
WHERE
    Original_Price IS NOT NULL
    AND TRIM(Original_Price) <> ''
    AND (Original_Price REGEXP '[^0-9.]' OR Original_Price LIKE '%.%.' OR Original_Price LIKE '-%'); -- Detects non-numeric characters, multiple dots, or negative signs

SELECT
    Brand,
    Title,
    Sale_Price
FROM
    MenTshirt
WHERE
    Sale_Price IS NOT NULL
    AND TRIM(Sale_Price) <> ''
    AND (Sale_Price REGEXP '[^0-9.]' OR Sale_Price LIKE '%.%.' OR Sale_Price LIKE '-%');

-- 2.2. Clean and Convert Price Columns (Safe Conversion for Calculation)
-- Purpose: To convert Original_Price and Sale_Price from TEXT to DECIMAL for
--          accurate mathematical operations. This handles non-numeric values
--          gracefully by converting them to NULL for calculations.
-- Skill Showcased: CAST(), NULLIF, preparing data for analysis, handling conversion errors.
SELECT
    Brand,
    Title,
    CAST(NULLIF(TRIM(Original_Price), '') AS DECIMAL(10, 2)) AS Converted_Original_Price,
    CAST(NULLIF(TRIM(Sale_Price), '') AS DECIMAL(10, 2)) AS Converted_Sale_Price
FROM
    MenTshirt
WHERE
    (TRIM(Original_Price) REGEXP '^[0-9]+(\\.[0-9]+)?$' OR Original_Price IS NULL OR TRIM(Original_Price) = '') -- Only numeric or empty/null
    AND (TRIM(Sale_Price) REGEXP '^[0-9]+(\\.[0-9]+)?$' OR Sale_Price IS NULL OR TRIM(Sale_Price) = '');

-- 2.3. Update Price Columns (Recommended: Create new columns first, then update)
-- Purpose: To demonstrate how to permanently clean and convert data types in the table.
--          This is crucial for robust data warehousing.
-- Skill Showcased: ALTER TABLE, UPDATE, SET, data type modification, conditional logic.
-- DANGER: ONLY RUN THESE ALTER/UPDATE STATEMENTS ON A TEST/DEVELOPMENT DATABASE.
-- For production, it's safer to create a new, properly typed table and insert cleaned data.

-- Step 1: Add new temporary columns with the correct DECIMAL type
-- ALTER TABLE MenTshirt
-- ADD COLUMN Temp_Original_Price DECIMAL(10, 2) NULL,
-- ADD COLUMN Temp_Sale_Price DECIMAL(10, 2) NULL;

-- Step 2: Update the new columns with safely cast values
-- UPDATE MenTshirt
-- SET
--     Temp_Original_Price = CASE
--         WHEN TRIM(Original_Price) REGEXP '^[0-9]+(\\.[0-9]+)?$'
--         THEN CAST(TRIM(Original_Price) AS DECIMAL(10, 2))
--         ELSE NULL
--     END,
--     Temp_Sale_Price = CASE
--         WHEN TRIM(Sale_Price) REGEXP '^[0-9]+(\\.[0-9]+)?$'
--         THEN CAST(TRIM(Sale_Price) AS DECIMAL(10, 2))
--         ELSE NULL
--     END;

-- Step 3: (Optional but good practice) Drop the old TEXT columns
-- ALTER TABLE MenTshirt
-- DROP COLUMN Original_Price,
-- DROP COLUMN Sale_Price;

-- Step 4: (Optional but good practice) Rename the new columns to the original names
-- ALTER TABLE MenTshirt
-- CHANGE COLUMN Temp_Original_Price Original_Price DECIMAL(10, 2) NULL,
-- CHANGE COLUMN Temp_Sale_Price Sale_Price DECIMAL(10, 2) NULL;

-- ====================================================================
-- SECTION 3: Basic Analytical Queries (Post-Cleaning Assumption)
-- For the following queries, we assume Original_Price and Sale_Price can
-- be reliably converted to numeric types. In a real scenario, you'd apply
-- the CAST/NULLIF or use a pre-cleaned table as per Section 2.2/2.3.
-- ====================================================================

-- Define a reusable expression for safe price conversion to avoid repetition
-- This is a common technique in SQL for readability and maintainability.
-- For actual execution, replace (CAST(NULLIF(TRIM(Original_Price), '') AS DECIMAL(10, 2)))
-- and (CAST(NULLIF(TRIM(Sale_Price), '') AS DECIMAL(10, 2))) with your chosen method or
-- use the cleaned columns if you updated the table permanently.

-- Example: Use the temp columns if you ran the ALTER/UPDATE in Section 2.3
-- Or, continue using the CAST/NULLIF method if you prefer non-destructive querying.
-- For this script, we'll continue with the CAST/NULLIF for demonstration purposes,
-- assuming the original TEXT columns are still present.

-- 3.1. Calculate Discount Amount and Percentage
-- Purpose: To derive key business metrics like the actual discount amount and the
--          discount percentage for each product. Essential for pricing analysis.
-- Skill Showcased: Basic arithmetic operations, CASE statement for division by zero prevention,
--                  understanding sales metrics.
SELECT
    Brand,
    Title,
    CAST(NULLIF(TRIM(Original_Price), '') AS DECIMAL(10, 2)) AS OriginalPrice,
    CAST(NULLIF(TRIM(Sale_Price), '') AS DECIMAL(10, 2)) AS SalePrice,
    (CAST(NULLIF(TRIM(Original_Price), '') AS DECIMAL(10, 2)) - CAST(NULLIF(TRIM(Sale_Price), '') AS DECIMAL(10, 2))) AS DiscountAmount,
    CASE
        WHEN CAST(NULLIF(TRIM(Original_Price), '') AS DECIMAL(10, 2)) > 0
        THEN ((CAST(NULLIF(TRIM(Original_Price), '') AS DECIMAL(10, 2)) - CAST(NULLIF(TRIM(Sale_Price), '') AS DECIMAL(10, 2))) / CAST(NULLIF(TRIM(Original_Price), '') AS DECIMAL(10, 2))) * 100
        ELSE 0 -- Or NULL, depending on desired behavior for 0 Original_Price
    END AS DiscountPercentage
FROM
    MenTshirt
WHERE
    CAST(NULLIF(TRIM(Original_Price), '') AS DECIMAL(10, 2)) IS NOT NULL
    AND CAST(NULLIF(TRIM(Sale_Price), '') AS DECIMAL(10, 2)) IS NOT NULL;


-- 3.2. Average Sale Price per Brand
-- Purpose: To determine the average selling price for products from each brand.
--          Helps in understanding brand positioning (premium, budget).
-- Skill Showcased: AVG() aggregate function, GROUP BY for brand-level aggregation.
SELECT
    Brand,
    AVG(CAST(NULLIF(TRIM(Sale_Price), '') AS DECIMAL(10, 2))) AS AverageSalePrice
FROM
    MenTshirt
WHERE
    CAST(NULLIF(TRIM(Sale_Price), '') AS DECIMAL(10, 2)) IS NOT NULL
GROUP BY
    Brand
ORDER BY
    AverageSalePrice DESC;

-- 3.3. Top 5 Brands by Average Discount Percentage
-- Purpose: To identify which brands are offering the highest average discounts.
--          This directly addresses one of your Power BI visuals.
-- Skill Showcased: Subqueries or CTEs, AVG(), GROUP BY, ORDER BY, LIMIT for ranking.
WITH BrandDiscounts AS (
    SELECT
        Brand,
        AVG(CASE
                WHEN CAST(NULLIF(TRIM(Original_Price), '') AS DECIMAL(10, 2)) > 0
                THEN ((CAST(NULLIF(TRIM(Original_Price), '') AS DECIMAL(10, 2)) - CAST(NULLIF(TRIM(Sale_Price), '') AS DECIMAL(10, 2))) / CAST(NULLIF(TRIM(Original_Price), '') AS DECIMAL(10, 2))) * 100
                ELSE 0
            END) AS AverageDiscountPercentage
    FROM
        MenTshirt
    WHERE
        CAST(NULLIF(TRIM(Original_Price), '') AS DECIMAL(10, 2)) IS NOT NULL
        AND CAST(NULLIF(TRIM(Sale_Price), '') AS DECIMAL(10, 2)) IS NOT NULL
    GROUP BY
        Brand
)
SELECT
    Brand,
    AverageDiscountPercentage
FROM
    BrandDiscounts
WHERE
    AverageDiscountPercentage IS NOT NULL -- Exclude brands where no valid discount could be calculated
ORDER BY
    AverageDiscountPercentage DESC
LIMIT 5;

-- 3.4. Brands with Products Below a Certain Price Threshold
-- Purpose: To identify brands that offer products at a lower price point,
--          potentially targeting a specific market segment.
-- Skill Showcased: HAVING clause with aggregate functions, conditional filtering.
SELECT
    Brand,
    MIN(CAST(NULLIF(TRIM(Sale_Price), '') AS DECIMAL(10, 2))) AS MinSalePrice,
    MAX(CAST(NULLIF(TRIM(Sale_Price), '') AS DECIMAL(10, 2))) AS MaxSalePrice,
    AVG(CAST(NULLIF(TRIM(Sale_Price), '') AS DECIMAL(10, 2))) AS AvgSalePrice
FROM
    MenTshirt
WHERE
    CAST(NULLIF(TRIM(Sale_Price), '') AS DECIMAL(10, 2)) IS NOT NULL
GROUP BY
    Brand
HAVING
    AVG(CAST(NULLIF(TRIM(Sale_Price), '') AS DECIMAL(10, 2))) < 500 -- Example threshold
ORDER BY
    AvgSalePrice ASC;

-- 3.5. Identify Brands with Price Inconsistencies (Original <= Sale Price)
-- Purpose: To flag potential data errors or unusual pricing strategies where
--          the sale price is equal to or higher than the original price.
-- Skill Showcased: Data validation, COUNT(), GROUP BY, WHERE for complex conditions.
SELECT
    Brand,
    COUNT(*) AS NumberOfInconsistentPrices
FROM
    MenTshirt
WHERE
    CAST(NULLIF(TRIM(Original_Price), '') AS DECIMAL(10, 2)) IS NOT NULL
    AND CAST(NULLIF(TRIM(Sale_Price), '') AS DECIMAL(10, 2)) IS NOT NULL
    AND CAST(NULLIF(TRIM(Original_Price), '') AS DECIMAL(10, 2)) <= CAST(NULLIF(TRIM(Sale_Price), '') AS DECIMAL(10, 2))
GROUP BY
    Brand
ORDER BY
    NumberOfInconsistentPrices DESC;

-- ====================================================================
-- SECTION 4: Advanced Analytical Queries
-- These queries delve deeper into the data, demonstrating more complex SQL capabilities.
-- ====================================================================

-- 4.1. Rank Brands by Average Discount (Using DENSE_RANK())
-- Purpose: To provide a clear ranking of brands based on their average discount percentage,
--          handling ties.
-- Skill Showcased: Window Functions (DENSE_RANK()), CTEs for multi-step logic.
WITH BrandDiscount AS (
    SELECT
        Brand,
        AVG(CASE
                WHEN CAST(NULLIF(TRIM(Original_Price), '') AS DECIMAL(10, 2)) > 0
                THEN ((CAST(NULLIF(TRIM(Original_Price), '') AS DECIMAL(10, 2)) - CAST(NULLIF(TRIM(Sale_Price), '') AS DECIMAL(10, 2))) / CAST(NULLIF(TRIM(Original_Price), '') AS DECIMAL(10, 2))) * 100
                ELSE 0
            END) AS AvgDiscountPercentage
    FROM
        MenTshirt
    WHERE
        CAST(NULLIF(TRIM(Original_Price), '') AS DECIMAL(10, 2)) IS NOT NULL
        AND CAST(NULLIF(TRIM(Sale_Price), '') AS DECIMAL(10, 2)) IS NOT NULL
    GROUP BY
        Brand
)
SELECT
    Brand,
    AvgDiscountPercentage,
    DENSE_RANK() OVER (ORDER BY AvgDiscountPercentage DESC) AS DiscountRank
FROM
    BrandDiscount
WHERE
    AvgDiscountPercentage IS NOT NULL
ORDER BY
    DiscountRank, Brand;

-- 4.2. Percentage of Products Discounted per Brand
-- Purpose: To understand what proportion of a brand's products are currently on sale.
-- Skill Showcased: Conditional aggregation (SUM(CASE WHEN ... END)), COUNT(), GROUP BY.
SELECT
    Brand,
    COUNT(*) AS TotalProducts,
    SUM(CASE WHEN CAST(NULLIF(TRIM(Original_Price), '') AS DECIMAL(10, 2)) > CAST(NULLIF(TRIM(Sale_Price), '') AS DECIMAL(10, 2)) THEN 1 ELSE 0 END) AS ProductsOnSale,
    (CAST(SUM(CASE WHEN CAST(NULLIF(TRIM(Original_Price), '') AS DECIMAL(10, 2)) > CAST(NULLIF(TRIM(Sale_Price), '') AS DECIMAL(10, 2)) THEN 1 ELSE 0 END) AS DECIMAL(10,2)) * 100.0) / COUNT(*) AS PercentageOfProductsOnSale
FROM
    MenTshirt
WHERE
    CAST(NULLIF(TRIM(Original_Price), '') AS DECIMAL(10, 2)) IS NOT NULL
    AND CAST(NULLIF(TRIM(Sale_Price), '') AS DECIMAL(10, 2)) IS NOT NULL
GROUP BY
    Brand
ORDER BY
    PercentageOfProductsOnSale DESC;

-- 4.3. Top 3 Most Expensive T-shirts by Original Price
-- Purpose: To find the highest-priced items, indicating premium offerings.
-- Skill Showcased: LIMIT with ORDER BY, understanding maximum values.
SELECT
    Brand,
    Title,
    CAST(NULLIF(TRIM(Original_Price), '') AS DECIMAL(10, 2)) AS OriginalPrice
FROM
    MenTshirt
WHERE
    CAST(NULLIF(TRIM(Original_Price), '') AS DECIMAL(10, 2)) IS NOT NULL
ORDER BY
    OriginalPrice DESC
LIMIT 3;

-- ====================================================================
-- SECTION 5: Potential Schema Enhancements (Conceptual)
-- This section demonstrates understanding of database design principles
-- and how to improve the existing schema for better analysis and integrity.
-- ====================================================================

-- Purpose: To show forethought in data modeling for future scalability and analytical depth.
-- Skill Showcased: Data modeling, database design principles, understanding of
--                  data warehousing concepts (e.g., star/snowflake schema).

-- Proposed Schema Improvements:
-- To enhance analytical capabilities and ensure data integrity, the current 'MenTshirt'
-- table could be refined into a more robust schema.

-- 1.  Dedicated Price Columns with Correct Data Types:
--     Original_Price and Sale_Price should be DECIMAL(10, 2) from the outset,
--     preventing text-to-numeric conversion issues and improving performance.

-- 2.  Product Dimension Table (DimProduct):
--     CREATE TABLE DimProduct (
--         ProductID INT PRIMARY KEY AUTO_INCREMENT,
--         Title VARCHAR(100) NOT NULL,
--         BrandID INT, -- Foreign Key to DimBrand
--         -- Add other product attributes like Category, Color, Size if available
--         FOREIGN KEY (BrandID) REFERENCES DimBrand(BrandID)
--     );

-- 3.  Brand Dimension Table (DimBrand):
--     CREATE TABLE DimBrand (
--         BrandID INT PRIMARY KEY AUTO_INCREMENT,
--         BrandName VARCHAR(50) NOT NULL UNIQUE
--     );

-- 4.  Fact Table (FactSalesPrice):
--     CREATE TABLE FactSalesPrice (
--         SalePriceID INT PRIMARY KEY AUTO_INCREMENT,
--         ProductID INT NOT NULL,
--         OriginalPrice DECIMAL(10, 2),
--         SalePrice DECIMAL(10, 2),
--         DateCaptured DATE, -- Crucial for tracking price changes over time
--         FOREIGN KEY (ProductID) REFERENCES DimProduct(ProductID)
--     );

-- Example Query on an Enhanced Schema (Conceptual - requires the above tables to exist):
-- This query demonstrates how analysis would be cleaner and more robust
-- with a normalized schema.
/*
SELECT
    b.BrandName,
    p.Title,
    fs.OriginalPrice,
    fs.SalePrice,
    (fs.OriginalPrice - fs.SalePrice) AS DiscountAmount,
    CASE
        WHEN fs.OriginalPrice > 0 THEN ((fs.OriginalPrice - fs.SalePrice) / fs.OriginalPrice) * 100
        ELSE 0
    END AS DiscountPercentage
FROM
    FactSalesPrice fs
JOIN
    DimProduct p ON fs.ProductID = p.ProductID
JOIN
    DimBrand b ON p.BrandID = b.BrandID
WHERE
    fs.DateCaptured = (SELECT MAX(DateCaptured) FROM FactSalesPrice) -- Latest prices
ORDER BY
    b.BrandName, p.Title;
*/
---
---

## Setup and Replication (For Recruiters/Fellow Developers)

To set up this project locally or understand the build process:

1.  **Azure SQL Database Setup:**
    * Ensure you have an active Azure subscription.
    * Create an Azure SQL Database instance (e.g., using `create_table_sales.sql` for schema).
    * Load your sales data (from your CSV) into the created SQL table.
    * Ensure appropriate firewall rules are configured to allow connections from your Power BI Desktop or Power BI Service.

2.  **Power BI Desktop:**
    * Download and install [Power BI Desktop](https://powerbi.microsoft.com/desktop/).
    * Open the `Sales_Performance_Dashboard.pbix` file located in the `powerbi_report/` directory.
    * **Data Source Settings:** You may need to update the data source settings to point to your specific Azure SQL Database server and credentials. Navigate to `File > Options and settings > Data source settings`, select the Azure SQL source, and click `Change Source...` to update the server name and database name.
    * **Refresh:** After updating the data source, refresh the data to ensure all visuals are populated.

3.  **Publish to Power BI Service:**
    * From Power BI Desktop, click `Publish` on the Home ribbon.
    * Select your desired workspace in the Power BI Service.
    * Once published, navigate to the Power BI Service (app.powerbi.com) to view and further manage the report.
    * **Create an App:** Consider packaging your report into a Power BI App for simplified sharing and management within your organization or with specific user groups.

---

## Contact

Feel free to connect with me on [[LinkedIn](https://www.linkedin.com/in/caroline-chebet-41683074/)] if you have any questions, feedback, or would like to discuss this project and my capabilities further.

