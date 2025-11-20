# US Store Sales Analysis – Power BI Dashboard

This repository contains an end-to-end Power BI project built to analyze US Store Sales using advanced data modeling, Power Query transformations, calculated columns, DAX measures, and interactive dashboards.
The project showcases the complete BI workflow—from raw data → cleaned model → relationships → DAX → visualization.

## Project Overview

The goal of this project is to provide a detailed analysis of sales performance, profitability, regional distribution, and customer behavior across US stores.

The dashboard answers key business questions such as:

Which store types generate the highest sales?

Which regions and sales channels are most profitable?

What is the average delivery performance?

Which products generate maximum discounts and profit?

What factors influence total profit?

## Tech Stack

Power BI Desktop

Power Query

DAX (Data Analysis Expressions)

Data Modeling (Snowflake Schema)

Power BI AI Visuals (Key Influencers, Decomposition Tree)

## Data Preparation (Power Query)

All datasets were cleaned and transformed in Power Query Editor.


### Applied Transformations

Promoted Headers

Changed Data Types

Filtered Rows (multiple stages)

Removed Errors

Replaced Values

Renamed Columns

Locale-based type conversion

Null value handling

Cleaned inconsistencies in Store Locations, Sales Orders, etc.

These transformations ensure the data is clean, consistent, and ready for modeling.

## Data Modeling – Snowflake Schema

The model follows a Snowflake Schema, making it clean and extensible.

### Fact Table
Sales Orders (center of the model)

### Dimension Tables
Products

Customers

Store Locations

Regions

Sales Team

## Relationships include:

One-to-many between dimensions and fact tables

Star/Snowflake hybrid for optimized reporting

Proper relationship cardinality and cross-filter directions

## Calculated Columns (DAX)
Created in the Sales Orders table:

### Unit Profit
Unit profit = 'Sales Orders'[Unit Price] - 'Sales Orders'[Unit Cost]

### Sale Per Order
Sale Per Order = 'Sales Orders'[Order Quantity] * 'Sales Orders'[Unit Price]

### Profit Per Order
Profit Per Order = 'Sales Orders'[Order Quantity] * 'Sales Orders'[Unit profit]

### Avg Delivery Days Per Order
Avg delivery days per order =
DATEDIFF('Sales Orders'[Order Date], 'Sales Orders'[Delivery Date], DAY)

These columns support drill-down analysis, profitability KPIs, and trend visuals.


## DAX Measures Used

### Total Sales
Total Sale = SUM('Sales Orders'[Sale Per Order])

### Total Profit
Total Profit = SUM('Sales Orders'[Profit Per Order])

### Total Quantity Sold
Total Qty Sold = SUM('Sales Orders'[Order Quantity])

### Average Delivery Days
Avg delivery days = AVERAGE('Sales Orders'[Avg delivery days per order])

### Average Order Quantity
(Shown in KPI gauge)


## Power BI Dashboard Features

The report consists of multiple pages with rich visuals.

Page 1 – Sales Analysis Dashboard

### Includes:

#### KPIs

Total Sale — $61.25M

Total Profit — $22.86M

Total Quantity Sold — 27K

Avg Delivery Days — 21 Days

#### Bar Charts

Total Sales by Store Type

Discount by Top Products

Profit by Region

#### Pie/Donut Charts

Count of Orders by Sales Team

Count of Orders by Sales Channel

#### Map Visualization
Total Profit by Country (Geographical Distribution)

#### Gauge KPI
Average Order Quantity

### Page 2 – Advanced Analytics
#### Decomposition Tree

##### Breakdown of Profit by:
Sales Channel
Region

### Customer attributes

#### Key Influencers Visual
Identifies factors that most influence Total Profit

Example:

Profit increases when County = Los Angeles County

## Repository Structure
 PowerBI-US-Store-Sales
 ┣  Dataset
 
 ┣  PBIX File
 
 ┣  README.md
 
 ┗ Screenshots of Dashboard

## Insights Delivered

City stores contribute the largest portion of sales.

Online channel has strong performance after in-store.

West & South regions drive majority of profit.

Products like TVs, Phones, and Audio have highest discounts.

Delivery performance averages around 21 days.

Profit is heavily influenced by store location and region.
