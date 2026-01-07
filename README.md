Project: Business Intelligence Dashboard for TechHub Retail
1. Introduction
TechHub Retail is a rapidly growing UK-based online electronics retailer with 18 months of expansion across 18 stores. The company specializes in electronics categories including smartphones, tablets, monitors, laptops, networking, and Accessories. Despite growth, TechHub lacks comprehensive analytics to guide strategic decisions for 2025 planning.
The purpose of this dashboard and analysis is to provide executive-level insights into sales performance, customer behavior, and product profitability using integrated data from sales transactions, customer profiles, and product catalog. The scope includes identifying growth opportunities, analyzing trends, and offering actionable recommendations to inform 2025 strategy, focusing on products, regions, and customer segments.
2. Multi-Dataset Integration Summary
The three datasets were connected in Tableau by importing each as a data source. Sales data was joined with Products on 'product_id' using an inner join, and then with Customers on 'customer_id' using an inner join. This ensured matched records for analysis, resulting in a unified data model with relationships for cross-dataset querying.
Calculated fields created:
Profit Amount = [Revenue] - ([Cost Price] × [Quantity]) – To calculate profit per transaction for profitability analysis.
Profit Margin % = ([Profit Amount] / [Revenue]) × 100 – To assess profitability efficiency.
Customer Tenure Days = DATEDIFF('day', [Signup Date], TODAY()) – To measure customer longevity for segmentation.
Customer Lifetime Value = SUM([Revenue]) grouped by customer – To evaluate long-term customer value.
Product Age Days = DATEDIFF('day', [Launch Date], [Order Date]) – To analyze product lifecycle impact on sales.
Data relationship challenges included duplicate 'product_category' columns after join, resolved by aliasing as 'product_category (Sales)' and using it for consistency. No missing values were found in key fields, but date hierarchies were created for drilling down.
(Screenshot of Data Source relationships view: In Tableau, the relationships pane shows Sales connected to Products via product_id, and to Customers via customer_id, with cardinality many-to-one for products and customers to sales.)
3. Dashboard Design Summary
The interactive executive dashboard is laid out with a top KPI section, followed by trends, geographic map, product treemap, customer scatter, and supplier bar chart. Visualizations use blue-orange color scheme for positive/negative metrics, with tooltips for details.
Key visualizations:
Executive KPI Dashboard: Cards showing Total Revenue (€31.69M), Average Order Value (€2,641), Total Customers (2,960), Average Profit Margin (-7.87%), with MoM growth arrows (e.g., revenue up 3-5% in early months).
Sales & Profitability Trends: Dual-axis line chart with revenue (bar) and profit (line) over months, showing upward trend from 2023 to 2024, with forecasting line predicting 5% growth.
Geographic Performance: Filled map of UK regions colored by revenue per customer, drill-down to city (e.g., South West highest at €3,453 per customer).
Product Portfolio Analysis: Treemap sized by revenue, colored by profit margin (Smartphones largest and green for high margin).
Customer Segmentation Matrix: Scatter plot of CLV vs. Tenure, clustered by loyalty tier and age group (Gold tier in higher CLV cluster).
Supplier & Product Performance: Horizontal bar of suppliers by revenue, with product count labels (Nova Electronics to.p at €8.43M).
Interactive features: Date range slider (Jan 2023 - Jun 2024), product category multi-select, loyalty tier dropdown, region/city hierarchy for drill-down. Navigation uses actions for filter synchronization across views.
(Main dashboard view showing all visualizations; filtered view for Smartphones category; drill-down on London region to cities.)
4. Key Insights & Findings
Major trends include overall revenue growth from €1.72M in Jan 2023 to €1.67M in Jun 2024, with average monthly revenue of €1.76M. Profit is positive but average margin negative due to low-margin categories like Accessories. Smartphones drive 20% of revenue with 47% margin, while Accessories drag with -60%.
Statistical findings: Product age has weak positive correlation with revenue (0.027) and quantity (0.018), suggesting mature products perform slightly better. Customer tenure averages 1,374 days, with CLV mean €10,706 (max €42,620 for high-value customers).
Supporting chart: Monthly revenue and profit table shows peak in Mar 2024 (€1.91M revenue, €924K profit).
5. Business Questions Answered
1.Product categories and suppliers that offered the best profit margins for 2025 focus
Smartphones have the highest margin at 47.14%, followed by Tablets (17.93%) and Monitors (16.96%). Laptops, Networking, and Accessories have negative margins (-17.82%, -41.86%, -60.09%). Top suppliers: Quantum Supplies (32.27%), TechCorp (10.12%), Nova Electronics (2.74%). Best cat-sup pairs: Accessories-ByteWare (96.72%), Monitors-ByteWare (96.28%). Focus on Smartphones from FutureTek (72.23%) for 2025.
Supporting Charts: Grouped mean margins; treemap visualization highlights Smartphones as large/high-margin and bar plot visualization highlight Quantum supplier with high profit margin for 2025 in focus.
2.Customer demographics (age, location, loyalty tier) impact purchasing behavior
46-55 Females in Leeds (Bronze tier) have highest revenue €36K, 87 transactions. 26-35 Males in Nottingham (Silver) follow €40K, 82 transactions. Bronze tier dominates top segments, but Gold tier has higher average CLV. Urban locations like Leeds, Nottingham show higher spend; 26-35 and 36-45 age groups drive volume.
Supporting Chart: Grouped aggregation; scatter plot shows clustering in mid-tenure high-CLV for 36-45 Gold.
3.Seasonal patterns that exists across different product categories and regions?
Revenue peaks in March €1.92M average across years, low in July €.56M, only 2023 data. Smartphones high in March €790K, Monitors in January €673K. Regions: London high in January €447K, South West in January €514K. Patterns show Q1 strength, possibly holiday carryover; drop in summer.
Evidence: Monthly groupby unstack; line chart shows seasonal spikes in Q1 for most categories.


6. Strategic Recommendations
1.Focus on High-Margin Categories and Suppliers: Prioritize Smartphones and Monitors from Quantum Supplies and FutureTek for inventory expansion. Implementation: Q1 2025, allocate 40% budget to these, expected impact: 15% margin improvement, 10% revenue growth.
2.Optimize Customer Acquisition: Shift marketing spend to Referral and Social channels (top CLV). Launch referral program targeting 36-45 demographics in high-spend cities like Leeds. Implementation: Q2 2025, expected impact: 8% increase in CLV, 20% new customer growth.
3.Address Seasonal Patterns: Boost Q3 promotions for low-margin categories like Accessories to counter summer dips. Regional targeting for South West and North East. Implementation: Mid-2025, expected impact: 12% revenue lift in off-peak months.
4.Improve Negative Margins: Review pricing/costs for Laptops, Networking, Accessories; negotiate with low-margin suppliers like FutureTek. Implementation: Immediate, expected impact: Reduce losses by 25%.
Justified by margins, CLV, and seasonal data showing growth potential in high-performers.
7. Critical Reflection
The dashboard effectively supports executive decision-making with interactive filters for quick insights and forecasting for planning. 
8. Data Issues or Risks
Limitations include negative average margin, possibly data errors in cost prices. Data imbalance (only to Jun 2024) skews seasonal analysis for H2. Risk of feature leakage if predictive models used without time splits. Small sample in some demo groups may bias insights.

