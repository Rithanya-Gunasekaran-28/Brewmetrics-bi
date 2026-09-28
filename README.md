# BrewMetrics BI

## Sales Performance Dashboard

BrewMetrics BI is a Power BI project developed to analyze sales performance across cities, product categories, store formats, and time.

## Objectives

- Analyze total sales and quantity
- Compare sales performance across cities
- Analyze sales by product category
- Analyze sales by store format
- Monitor sales trends over time
- Support interactive filtering and drill-down analysis

## Data Model

The project follows a star-schema structure.

### Dimension Tables
- Dim_Date
- Dim_City
- Dim_Product

### Fact Table
- Fact_Sales

The date dimension is used for time-based analysis, while city and product dimensions provide descriptive attributes for sales analysis.

## Key Measures

- Total Sales
- Total Quantity
- Total Transactions
- Average Order Value
- Month-over-Month Sales Growth %
- Running Total Sales
- City Sales Rank
- Average Sales per Quantity

## Dashboard Features

The dashboard includes:

- Total Sales KPI
- Total Quantity KPI
- Total Transactions KPI
- Average Order Value KPI
- Sales Trend Over Time
- Sales by City
- Sales by Category
- Sales by Store Format
- City and Category slicers
- Date hierarchy for time-based analysis

## DAX Development

Copilot was used to generate and review DAX formulas. The suggested formulas were checked against the existing data model and adjusted where necessary.

The development notes are documented in `NOTES.md`.

## Tools Used

- Power BI Desktop
- DAX
- Git
- GitHub
- VS Code
- Power BI Project (.pbip)

## Author

RITHANYA.G  
24BAD132

A version-controlled Power BI analytics solution for BrewMetrics Coffee Co.
