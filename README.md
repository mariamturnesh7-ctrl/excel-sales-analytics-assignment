# excel-sales-analytics-assignment
This guide introduces Microsoft Excel as a beginner-friendly tool for basic data analytics, covering data cleaning, formulas, pivot tables, and simple visualizations using real Excel examples.

Purpose

This workbook analyzes sales operations data to clean, enrich, analyze, and present insights through Excel-based analytics and an interactive dashboard.

Data Issues Identified

Missing values in City, Salesperson, and Channel fields.

Invalid values including negative UnitPrice and excessive discounts (>30%).

Inconsistent dates where RequiredDate occurred before OrderDate.

Blank dimension values (e.g., SKU) affecting PivotTables and charts.

Data Cleaning Rules Applied

Duplicates: Exact duplicate rows were removed using all columns as matching criteria.

Missing City: Filled using the most common City based on Country and ProductCategory trends.

Missing Salesperson: Inferred using dominant geographic sales ownership patterns; otherwise labeled Unassigned.

Missing Channel: Imputed based on historical Salesperson, ProductCategory, and Customer Segment behavior.

Invalid Prices: Negative UnitPrice values were replaced with the median price for the same ProductCategory.

Discounts: DiscountPct values above 30% were capped at 30% and flagged for review.

Dates: RequiredDate earlier than OrderDate was corrected using a standardized lead-time rule.

Derived Fields & Calculations

Month / Quarter: Derived from OrderDate using custom formatting and IF logic.

LeadTimeDays: Calculated as RequiredDate minus OrderDate.

Revenue, Cost, Profit, Margin: Computed using Excel formulas (no hard-coded totals).

PriceBand: Created using quantiles to classify products into Low, Medium, and High price ranges.

On-Time Flag: Orders flagged as on-time when LeadTimeDays ≤ 7.

Analytical Methods Used

Cohort Analysis: Tracked monthly revenue from each country’s first active month.

ABC Analysis: Ranked SKUs by GrossRevenue and classified into A, B, and C groups using cumulative contribution.

Salesperson Productivity: Measured revenue per order, orders per month, and profit per order.

Channel Mix & Cannibalization: Compared channel revenue shares by region to identify substitution patterns.

Price Compliance: Measured share of orders with DiscountPct > 20% by Region and Salesperson.

Service Level Proxy: Calculated percentage of orders meeting a 7-day lead-time target.

Dashboard & Interactivity

Single-page interactive dashboard built using PivotTables and charts.

Slicers applied for Region, Country, Channel, ProductCategory, Month, and Salesperson.

KPIs dynamically update without broken references.

Charts include revenue trends, profit by channel and region, and top-performing SKUs.
