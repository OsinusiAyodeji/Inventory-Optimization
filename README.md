# Inventory Health Check: Capital Optimization & Stockout Mitigation

## Abstract Summary
![Inventory Dashboard](Inventory%20Screenshot%202.png)

This project addresses the critical balance between overstocking and understocking within a retail environment. By analyzing inventory health, I identified **$136.1M** in tied-up capital and a **$2.99M** loss due to stockout costs. The analysis highlights significant inefficiencies, including a **308.4%** average forecast error, which directly impacts cash flow and customer satisfaction. Through this data-driven approach, the project pinpoints "Cash Traps" (dead stock) and "Ghost Revenue" (lost sales) to provide actionable insights for inventory optimization.



## Background
In the retail sector, maintaining the right amount of stock is a constant challenge. This project explores the inventory dynamics of **Retail Solution Inc.** across three primary categories: Accessories, Electronics, and Home Appliances. The focus is on understanding how capital is distributed and where revenue "leaks" occur due to supply chain or forecasting failures.


### Business Problem Statement
Retail Solutions Inc. is currently failing to balance supply with customer demand. Despite having historical data, the company is trapped in a cycle of **Inventory Imbalance**, oscillating between two expensive extremes that are hurting profitability:

* **Stockouts (The "Empty Shelf"):** Frequently running out of high-demand products, which leads directly to lost revenue and frustrated customers.
* **Overstock (The "Dusty Box"):** Over-purchasing slow-moving items to compensate, resulting in millions of dollars in tied-up capital sitting uselessly in the warehouse.
* **The Root Cause:** This imbalance is driven by inefficient inventory control and significant forecasting errors, meaning the current system cannot accurately predict what customers want.

### Objectives
The primary goal of this project is to develop a comprehensive **Inventory Health Check** to diagnose these inefficiencies. Specifically, the analysis aims to:

* **Identify Financial Leakage:** Quantify the impact of "Ghost Revenue" (lost sales) and "Cash Traps" (dead stock) across the organization.
* **Segment Category Health:** Evaluate which product categories are most susceptible to supply-demand mismatches.
* **Isolate Problematic SKUs:** Pinpoint specific items that contribute most to capital stagnation.
* **Assess Forecasting Integrity:** Analyze the variance between predicted demand and actual sales to establish a baseline for procurement improvements.

## Data Description

### Data Sources
The primary dataset for this analysis was provided by **Retail Solution Inc.**, containing detailed records of inventory levels, sales performance, and procurement metrics across various product categories.

### Data Collection
The data was extracted from the organization's internal inventory management and sales reporting systems. The dataset provides a granular view of transactional history and stock status, enabling a deep dive into forecasting accuracy and capital allocation.

### Data Characteristics
The dataset includes several key variables used to calculate inventory health metrics. Below is a breakdown of the core data fields:

* **Product Identifiers:** `Product_ID`, `Product_Name`, and `Product_Category` (Accessories, Electronics, and Home Appliances).
* **Financial Metrics:** `Cost_Price`, `Selling_Price`, and `Profit_Margin` used to evaluate tied-up capital and potential revenue.
* **Supply Chain Metrics:** `Lead_Time`, `Reorder_Point`, and `Reorder_Quantity` to assess procurement efficiency.
* **Sales & Demand:** `Sales_Volume`, `Forecasted_Demand`, and `Demand_Variance` used to calculate forecasting errors.
* **Inventory Health Indicators:** `Stockouts`, `Overstock`, `Overstock_Cost`, and `Stockout_Cost` (logical and numerical flags for identifying imbalances).

## Methodology

### Data Cleaning & Transformation
The initial data preparation was performed using **Power Query** to ensure data integrity and readiness for analysis. Key steps included:
* **De-duplication:** Identified and removed fully duplicated rows to prevent inflated inventory valuations.
* **Standardization:** Normalized necessary categorical columns to ensure consistent naming conventions across the dataset.
* **Type Conversion:** Rectified incorrect data types by converting them into the required formats (e.g., numerical and date formats) for accurate processing.
* **Feature Engineering:** Developed custom columns within Power Query, such as `Total_Inventory_Value` and `Abs_Error_Pct`, to facilitate the final analysis.

### Exploratory Data Analysis (EDA)
I utilized the **Data Profiling tools** in Power Query to perform an initial examination of the data.
* **Profiling:** Inspected each column to understand data distribution, quality, and to identify potential outliers.
* **Integrated Workflow:** Both cleaning and exploratory analysis were handled within Power Query to ensure a streamlined and efficient transformation process.

### Statistical Analysis & KPI Development
Using **Power Pivot** and Pivot Tables, I calculated four critical Key Performance Indicators (KPIs) to quantify the business impact of the current inventory state:

![Inventory Optimization KPIs](Inventory%20Optimization%20KPI's.png)

* **Total Inventory Value ($136.1M):** Represents the value of capital currently tied up in unsold stock.
  * *Formula:* `[Current_Stock_Level] * [Cost_Price]` (Aggregated via Sum in Pivot Table).
* **Stockout Cost ($2.99M):** The estimated revenue lost because customers wanted to buy, but shelves were empty.
  * *Method:* Sum of the `Stockout_Cost` column calculated via Pivot Table.
* **Average Forecast Error (308.4%):** A measure of how far off predictions are from reality, indicating a reliance on "blind guessing."
  * *Formula:* `Average of (Number.Abs([Forecasted_Demand] - [Sales_Volume]) / [Sales_Volume])`.
* **Stockout Frequency (1,955 items):** The count of specific products missing from the shelves.
  * *Method:* Counted dataset rows filtered for where the `Stockout` flag is **TRUE**.




















