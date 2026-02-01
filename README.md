# excel-sales-analytics-assignment
This guide introduces Microsoft Excel as a beginner-friendly tool for basic data analytics, covering data cleaning, formulas, pivot tables, and simple visualizations using real Excel examples.

Part A — Data Cleaning & Preparation:
1) Create a staging table where you:
   • Remove exact duplicate rows (define and document your duplicate criteria).
Used Conditional Formating on the order date date and highlighted the duplicate in red= ORD-2023-521818

   • Fix data types (dates as Dates, numeric fields as numbers).
   • Handle missing values for City, Salesperson, and Channel using reasonable business logic (document your approach).
Missing values were completed by comparing similar orders based on country, product type and customer segment,channel and applying the most common result

   • Flag and correct suspicious UnitPrice values (e.g., negative prices) and discounts (e.g., > 30%).
Used Conditional Formating with cells less than zero in the unit Price 3 values found & corrected
Used Conditional Formating with cells greater than 0.3 in the DiscountPct 7 values found & added a new sheet called"Flagged Discount %"

   • Ensure RequiredDate is not earlier than OrderDate; where it is, impute a corrected RequiredDate (explain your rule).
From the Lead Time Days I flagged the Required dates which were before the order dates and highlighed them red

   • Add a derived 'LeadTimeDays' = RequiredDate − OrderDate (in days).
 = RequiredDate − OrderDate then change the column to numbers so it will be in days

2) Create calculated columns (do these in Excel, not by formula in the data source):
   • GrossRevenue = UnitPrice × Quantity × (1 − DiscountPct).
   • CostOfGoods = UnitCost × Quantity.
   • GrossProfit = GrossRevenue − CostOfGoods.
   • MarginPct= IF(GrossRevenue=0, 0, GrossProfit / GrossRevenue).

3) Create standardized dimensions:
   • Month (MMM-YYYY) from OrderDate.
used a custom MMM-YYYY date format

   • Quarter (e.g., Q1-2024).
IF and AND functions were used to classify OrderDate into calendar quarters.

   • Region hierarchy: Region → Country → City.
A PivotTable was created to display the Region → Country → City hierarchy its labelled"Region Hierarchy"

   • ProductCategory and a derived 'PriceBand' (e.g., Low/Medium/High using quantiles).
ProductCategory was reviewed for consistency, UnitPrice was segmented using quantiles, and products were classified into Low, Medium, and High price bands for analysis
Part B — Analysis Tasks (show workings with PivotTables / formulas):
4) Build a cohort of first-time sales by Country and Month:

5) ABC analysis by SKU within each ProductCategory using GrossRevenue:
   • Classify SKUs into A (top 80%), B (next 15%), C (last 5%) of revenue per category.
Created a PivotTable to summarize GrossRevenue.
Sorted items from highest to lowest revenue.
Calculated cumulative revenue using a running total percentage.
Classified items into A (top 80%), B (next 15%), and C (final 5%) categories.

6) Salesperson productivity:
   • Compute Revenue/Order, Orders/Month, and GrossProfit/Order by Salesperson; highlight the top and bottom 3.
Created a PivotTable to summarize GrossRevenue, Order count, and GrossProfit by Salesperson.
Calculated Revenue per Order and GrossProfit per Order using aggregated values.
Determined Orders per Month by grouping OrderDate into months and counting orders.
Sorted results to identify the top and bottom three salespeople based on productivity metrics

7) Channel mix & cannibalization:
   • Compare revenue shares by Channel across Regions; identify where online cannibalizes retail (justify with data).
Created a new sheet to calculate revenue by Channel and Region using Excel formulas.
Computed channel revenue shares as a percentage of total regional revenue.
Compared Online and Retail shares across Regions to identify potential cannibalization.
Flagged regions where high Online share coincides with reduced Retail share, indicating channel cannibalization.

8) Service level proxy:
   • Using LeadTimeDays, determine % of orders meeting a 7-day target by Country and Category.
Created an on-time indicator based on a 7-day LeadTimeDays target.
Used a PivotTable to calculate the percentage of on-time orders by Country and ProductCategory.
Interpreted the average on-time rate as a service level proxy.

9) Price compliance:
   • Share of orders with DiscountPct > 20% by Region and Salesperson; list outliers.
Created a price compliance indicator to flag orders with DiscountPct greater than 20%.
Used a PivotTable to calculate the share of non-compliant orders by Region and Salesperson.
Applied conditional formatting to highlight outliers with unusually high non-compliance rates.

Part C — Scenario Modeling (What-If):
10) Build a What-If control panel (slider/cell inputs):
   • Global Discount Cap (e.g., 0%–25%).
   • UnitCost inflation factor (e.g., 0%–15%).
   • Quantity uplift (e.g., 0%–20%).
   Recalculate Revenue and Profit metrics under these scenarios and compare to the baseline.

Part D — Interactive Dashboard:
11) Create a single-page dashboard with:
   • Slicers for Region, Country, Channel, ProductCategory, Month, and Salesperson.
   • KPIs: Total Revenue, Gross Profit, Margin %, Avg Order Value, On-Time % (LeadTimeDays ≤ 7).
   • Visuals:
       – Revenue by Month (line chart).
       – Profit by Region and Channel (stacked column).
       – Top 10 SKUs by Revenue (bar).
   • Dynamic titles reflecting applied filters.

12) Tell a story:
   • Write 5–8 bullet insights derived from the dashboard; include at least one insight per Region.
Africa relies heavily on Retail and Marketplace sales but underperforms on service level metrics.
Americas shows strong Online performance with signs of Retail cannibalization.
Europe delivers high revenue and profit but with uneven service levels by category.
Asia drives volume through Distributor and Marketplace channels but faces margin pressure.
A small set of SKUs and high-discount orders have an outsized impact on revenue and profitability.
