Project name: Snowflake Sales Performance Dashboard

Description: This project aims to build a Snowflake data warehouse to analyze sales data and generate performance metrics. The goal is to create a schema, load sales data, and run queries to generate insights like total sales, sales by region, and monthly sales trends.

Overview

This project demonstrates how to analyze sales data using Snowflake. It involves setting up a Snowflake data warehouse, creating tables, loading sample data, and running SQL queries to generate insights into sales performance. The project aims to help you understand how to work with Snowflake for basic data warehousing and analysis tasks.

Prerequisites

Snowflake Account: You need a Snowflake account. Sign up for a free trial if you don’t have one.
Snowflake Web Interface: Access your Snowflake environment through the web interface.
[CSV Files]: This project uses CSV files to load sample data into Snowflake.
Project Structure

Data Sources:
Sales Data: Information about sales transactions.
Products Data: Information about products.
Regions Data: Information about regions where sales occurred.
/data: Contains sample CSV files.

product.csv: Sample product data.
regions.csv: Sample region data.
sales.csv: Sample sales transaction data.
Objective:
- Create a Snowflake schema.
- Load sales, products, and regions data into Snowflake.
- Perform analysis to generate insights such as total sales, sales by region, and sales trends over time.
/Sql: Contains SQL scripts.

create_tables.sql: SQL script for creating tables. (salestable, regionstable and productstable)

load_data.sql: SQL script for loading data into Snowflake. (loaded data for each table seperately)

analysis_queries.sql: SQL script for running analysis queries.

Total sales
SELECT SUM(TOTAL_AMOUNT) AS TOTAL_SALES
FROM SALESTABLE;

-- Sales by region
SELECT REGION_NAME, SUM(TOTAL_AMOUNT) AS TOTAL_SALES
FROM SALESTABLE
JOIN REGIONSTABLE ON SALEStable.REGION_ID = REGIONStable.REGION_ID
GROUP BY REGION_NAME
ORDER BY TOTAL_SALES DESC;

-- Monthly sales trends
SELECT EXTRACT(YEAR FROM SALE_DATE) AS YEAR, EXTRACT(MONTH FROM SALE_DATE) AS MONTH, SUM(TOTAL_AMOUNT) AS TOTAL_SALES
FROM SALESTABLE
GROUP BY YEAR, MONTH
ORDER BY YEAR, MONTH;

README.md: This file, providing an overview and instructions.

Setup Instructions

Create a Snowflake Account

Sign up for a Snowflake account if you don’t already have one: Snowflake Sign-Up.
Set Up Snowflake Environment

Log in to the Snowflake web interface: Snowflake UI.
Create a new Snowflake database to use for this project.
Run SQL Scripts

Create Tables: Run "sql/create_tables.sql" to set up the schema in your Snowflake database.
-- Run the script to create tables
Load Data: Run "sql/load_data.sql" to load sample data from the CSV files into Snowflake.
-- Run the script to load data
Run Analysis Queries: Execute "sql/analysis_queries.sql" to perform analysis and generate insights.
-- Run the script to analyze data
Review Results

Check the results of your analysis queries in the Snowflake web interface to gain insights into sales performance.
Important Resources
Snowflake Documentation: Comprehensive guides and references for using Snowflake.
[Snowflake Documentation] (https://docs.snowflake.com/en/)
Snowflake SQL Reference: Detailed SQL syntax and usage.
[Snowflake SQL Reference] (https://docs.snowflake.com/en/sql-reference/)
CSV File Formatting: Ensure your CSV files are correctly formatted.
[CSV File Format] (https://en.wikipedia.org/wiki/Comma-separated_values)
Data Loading in Snowflake: How to load data from files into Snowflake tables.
[Loading Data into Snowflake] (https://docs.snowflake.com/en/user-guide/data-load-overview.html)
