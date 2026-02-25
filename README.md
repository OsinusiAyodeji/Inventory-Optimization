# Inventory Health Check: Capital Optimization & Stockout Mitigation

## Abstract Summary
![Inventory Dashboard](Inventory%20Screenshot%202.png)

This project addresses the critical balance between overstocking and understocking within a retail environment. By analyzing inventory health, I identified **$136.1M** in tied-up capital and a **$2.99M** loss due to stockout costs. The analysis highlights significant inefficiencies, including a **308.4%** average forecast error, which directly impacts cash flow and customer satisfaction. Through this data-driven approach, the project pinpoints "Cash Traps" (dead stock) and "Ghost Revenue" (lost sales) to provide actionable insights for inventory optimization.

---

## Introduction

### Background
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

---

## Data Description

### Data Sources
The primary dataset for this analysis was provided by **Retail Solution Inc.**, containing records of inventory levels, sales performance, and procurement metrics.

### Data Collection
The data was extracted from the organization's internal inventory management and sales reporting systems to provide a granular view of transactional history.

### Data Characteristics
The dataset includes several key variables used to calculate inventory health metrics:
* **Product Identifiers:** `Product_ID`, `Product_Name`, and `Product_Category`.
* **Financial Metrics:** `Cost_Price`, `Selling_Price`, and `Profit_Margin`.
* **Supply Chain Metrics:** `Lead_Time`, `Reorder_Point`, and `Reorder_Quantity`.
* **Sales & Demand:** `Sales_Volume`, `Forecasted_Demand`, and `Demand_Variance`.

---

## Methodology

### Data Cleaning & Transformation
The initial data preparation was performed using **Power Query** to ensure data integrity:
* **De-duplication:** Identified and removed fully duplicated rows.
* **Standardization:** Normalized categorical columns for consistency.
* **Type Conversion:** Rectified incorrect data types into required formats (e.g., numerical and date formats).
* **Feature Engineering:** Developed custom columns such as `Total_Inventory_Value` and `Abs_Error_Pct`.

### Exploratory Data Analysis (EDA)
I utilized the **Data Profiling tools** in Power Query to perform an initial examination of the data:
* **Profiling:** Inspected each column to understand data distribution, quality, and to identify potential outliers.
* **Integrated Workflow:** Both cleaning and exploratory analysis were handled within Power Query.

### Statistical Analysis & KPI Development
Using **Power Pivot** and Pivot Tables, I calculated four critical KPIs:

![Inventory Optimization KPIs](Inventory%20Optimization%20KPI's.png)

* **Total Inventory Value ($136.1M):** Value of capital currently tied up in unsold stock.
  * *Formula:* `[Current_Stock_Level] * [Cost_Price]`.
* **Stockout Cost ($2.99M):** Estimated revenue lost because shelves were empty.
* **Average Forecast Error (308.4%):** Measure of how far off predictions are from reality.
  * *Formula:* `Average of (Number.Abs([Forecasted_Demand] - [Sales_Volume]) / [Sales_Volume])`.
* **Stockout Frequency (1,955 items):** Count of specific products missing from the shelves.

---

## Analysis & Findings

### Overstock Analysis: The "Dusty Box"
#### Approach
I summarized the **Total Inventory Value** by both **Product Name** and **Product Category** to determine where capital is being tied up.

#### Findings
![Capital by Category](Capital%20Tied%20up%20by%20category.png)

* **Uniform Capital Distribution:** Tied-up capital is almost equally distributed across categories: **Accessories ($45.9M)**, **Electronics ($45.6M)**, and **Home Appliances ($44.6M)**.
* **Top 5 Cash Traps (Dead Stock):** Five specific items are responsible for over **$85M** in stagnant capital, including Smartwatches (**$17.44M**) and TVs (**$17.37M**).

![Top 5 Cash Traps](capital%20tied%20up%20by%20product.png)

### Stockout Analysis: The "Empty Shelf"
#### Approach
I analyzed the **Stockout Cost** and **Frequency** across categories to identify revenue leaks.

#### Findings
![Where is Revenue Leaking](Revenue%20leak%20by%20category.png)

* **Revenue Leakage:** We have lost an estimated **$2.99M** in sales because products were unavailable.
* **Top 5 "Ghost Revenue" Items:** Chargers (**$386K**) and Smartwatches (**$380K**) suffered the highest lost sales.

![Top 5 Ghost Revenue Items](Revenue%20leaks%20by%20product%20name.png)

---

## Recommendations

### 1. Host a "Cash Recovery" Sale
Immediately run aggressive clearance sales on **Top 5 Cash Trap** items (Smartwatches, TVs, etc.) to convert dead stock into liquid cash. 

### 2. Prioritize "Must-Have" Items
Shift recovered cash into buying high-demand items like Chargers and Headphones to stop the **$2.99M** revenue leakage.

### 3. Stop the "Guesswork" in Ordering
Replace the current "guessing" system with a data-driven prediction model to reduce the **308.4% error rate**.

---

## Conclusion: Moving from Reactive to Proactive
The "Inventory Health Check" reveals that Retail Solutions Inc. is not suffering from a lack of data, but a lack of **data-driven decision-making**. By identifying that overstocking and stockouts are organizational-wide symptoms of a **308.4% forecast error**, this project provides a clear roadmap to recovery. Implementing the recommended "Smart Reordering" and liquidating "Cash Traps" will allow the business to stop hoarding what it doesn't need and start providing what its customers actually want. This transition will protect the bottom line, free up millions in working capital, and significantly improve customer trust.
