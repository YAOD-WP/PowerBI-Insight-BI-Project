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

