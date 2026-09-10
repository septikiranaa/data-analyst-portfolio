# Project 4 - Olist E-Commerce Analysis

SQL & Power BI analysis using the Brazilian E-Commerce Public Dataset by Olist.

## Business Background & Problem Statement
The business needs to increase distribution efficiency to the cities with the highest sales contribution, using geographic data to guide production and logistics decisions.
This analysis aims to answer the following questions:
1. Which cities contribute the most to total sales, and which products drive that performance?
2. How far are the factories from the top-selling cities, and which factory is most efficient for each city?
3. Which shipping mode is the most cost-efficient for each city?
4. How does sales performance change over time, and are there seasonal patterns?
5. Which factory should be prioritized to supply high-demand cities more efficiently?
6. How can underperforming products and cities be supported through targeted promotion?

## Problem Understanding
![problem_understading](root_cause_analysis)

## Dataset 
The dataset was sourced from the Maven Analytics platform (Kaggle) and contains 10,194 records and 39 variables, organized into the following tables:

Sales — product sales information across various cities
Factory — location and details of production facilities
Product — details of marketed products
Target — product divisions and their sales targets
US Zips — US postal code data for identifying geographic locations

Since the original dataset did not include a distance field, distance between each factory and destination city was calculated manually using two methods:

Haversine formula (assumes a perfectly spherical Earth) — calculated in Excel
Vincenty formula (assumes an ellipsoidal Earth, more precise) — calculated in Python using geopy

The final analysis uses the Vincenty distance, as it is more accurate (the difference from Haversine was small but the more precise method was preferred).

Dataset Link : https://mavenanalytics.io/data-playground?order=number_of_records%2Cdesc&search=US%20candy

## Tools
Microsoft Excel for data exploration, Haversine distance calculation, pivot tables
Python (Pandas, Geopy) — Vincenty distance calculation, data cleaning
Whimsical for root cause analysis (fishbone diagram)
Dashboard/BI Tool — interactive dashboard for sales, distance, and shipping analysis

## Analysis & Key Findings
1. Sales & Profit Overview
    Overall performance across the dataset:
    
    Total sales: approximately $122.95K
    Total gross profit: approximately $82.14K
    Total units sold: approximately 35K
    
    Insight: The business shows healthy overall margins, with a small number of cities and products driving the majority of performance.

2. Top 5 City Performance

    The top 5 cities together contributed 30.91% of total company sales:
    
    City	Sales	Gross Profit	% of Total Sales
    New York City	$10,945.89	$7,302.53	8.90%
    Los Angeles	$9,371.55	$6,269.83	7.62%
    Philadelphia	$6,369.27	$4,223.03	5.18%
    San Francisco	$6,218.24	$4,157.56	5.06%
    Seattle	$5,105.48	$3,411.70	4.15%
    
    Insight: New York City is the dominant market hub, generating nearly double the sales of the next closest region outside the top 5.

3. Product Performance by City

    Each top city shows a different best-selling product, indicating that stock should be tailored per city rather than standardized:
    
    City	Top Product	Units	Sales
    New York City	Wonka Bar – Scrumdiddlyumptious	755	$2,718
    Los Angeles	Wonka Bar – Milk Chocolate	653	$2,122.25
    Philadelphia	Wonka Bar – Fudge Mallows	379	$1,364.40
    San Francisco	Wonka Bar – Triple Dazzle Caramel	391	$1,466.25
    Seattle	Wonka Bar – Milk Chocolate	312	$1,014
    
    Across the whole dataset, Wonka Bar – Scrumdiddlyumptious ($25.7K) and Wonka Bar – Milk Chocolate ($24.8K) were the two best-selling products overall, while
    Nerds, Fun Dip, Lickable Wallpaper, and Everlasting Gobstopper each sold fewer than 10 units.
    
    Insight: The top 5 cities are strategic markets to reintroduce underperforming products through bundling or discount campaigns.

4. Factory-to-City Distance

    Average distance from each factory to the destination cities:
    
    Factory	Avg Distance (km)	Total Units Shipped
    Sugar Shack	262.83	35
    Wicked Choccy's	8,056.16	4,409
    The Other Factory	8,988.75	134
    Secret Factory	9,047.65	152
    Lot's O' Nuts	10,932.98	6,140
    
    Insight: Lot's O' Nuts ships the highest volume (6,140 units) despite having the longest average distance (~10,933 km), while Wicked Choccy's offers a better
    balance of proximity and volume — making it a strong candidate for expanded production. Sugar Shack is by far the closest factory to major cities but
    currently ships a very limited volume.

5. Shipping Mode Efficiency

    Average shipping cost by mode across all cities:
    
    Ship Mode	Avg Cost Range
    Standard Class	$4.00 – $4.50
    Second Class	$3.90 – $4.20
    First Class	$3.60 – $4.40
    Same Day	$4.00 – $4.70
    
    Insight: Standard Class is the most efficient and most frequently used mode across all cities. Same Day shipping is consistently the most expensive, except in
    Los Angeles, where it is comparatively cheaper ($3.50) than in other cities — an opportunity for targeted promotion.

6. Seasonal Sales Trend

    Sales grew consistently from 2021 to 2024, with a clear seasonal spike every Q4:
    
    2021 Q4: $8.1K → 2022 Q4: $8.7K → 2023 Q4: $10.1K → 2024 Q4: $11.9K
    
    Insight: The Q4 spike likely reflects the impact of Halloween, seasonal promotions, and holiday demand, and should inform inventory planning for future years.

7. Product Division Performance
    Chocolate division: 98.22% of total sales
    Other division: 1.52%
    Sugar division: 0.26%
    
    Insight: The business is heavily concentrated in the Chocolate division, which should remain the primary focus for promotion and stock planning.

## Recommendation
1. Reallocate Production for New York City

    New York City generates the highest sales but is currently served by Lot's O' Nuts, the factory farthest away (11,102 km). Shifting production of Wonka Bar –
    Scrumdiddlyumptious — NYC's top-selling product (>$2.7K) — to Wicked Choccy's (8,237 km) would shorten the distribution distance and support continued sales
    growth in this key market.

2. Reallocate Production for Seattle

    Seattle currently ranks lowest among the top 5 cities. Allocating Scrumdiddlyumptious production to Wicked Choccy's (7,838 km) instead of Lot's O' Nuts
    (10,703 km) would improve product penetration and support a gradual sales increase.

3. Launch a Discount Program for Top-Selling Products

    Apply a 5–10% discount on the best-selling product in each top-5 city (Scrumdiddlyumptious in NYC, Milk Chocolate in LA, Fudge Mallows in Philadelphia, Triple
    Dazzle Caramel in San Francisco and Seattle). This is estimated to contribute an additional $38.43K in combined sales.

4. Bundle Underperforming Products with Best Sellers

    Products with low total sales (Kazookles and Wonka Gum, combined $590.5) should be bundled with each city's top seller to increase visibility and drive
    incremental sales in high-traffic markets.

5. Optimize Shipping Mode by City

    Prioritize Standard Class as the default shipping mode due to its low cost and high efficiency. Reserve Same Day shipping for high-margin, priority orders
    only. Promote Same Day shipping specifically in Los Angeles, where it is comparatively cheaper, and review shipping routes and volume in Seattle to reduce its
    above-average Standard Class cost.

## Dashboard
The interactive dashboard was built to provide an overview of total sales, gross profit, and units sold, alongside breakdowns by city, product, division, year/quarter, and factory-to-city distance.

![dashboard_visualisasi](dashboard_visualisasi_project4)

## Conclusion
The analysis shows that while the business has a clear set of high-performing cities and products, distribution efficiency is currently constrained by factory locations that are poorly matched to demand. New York City, the top-performing market, is served by one of the farthest factories, while a closer, high-capacity factory (Wicked Choccy's) is underutilized relative to its proximity advantage.

Overall, the findings suggest that reallocating production closer to high-demand cities, applying targeted discounts and bundling strategies, and optimizing shipping mode usage by city could meaningfully improve distribution efficiency and support continued sales growth.

## Skills Demonstrated
Data cleaning and validation across multi-table datasets (10K+ records)
Geospatial distance calculation (Haversine and Vincenty methods) in Excel and Python
Root cause analysis (fishbone diagram)
Exploratory data analysis
Sales, profitability, and shipping cost analysis
Data visualization and dashboard development
Business insight and recommendation development
Cross-functional team collaboration (cleaning, analysis, visualization, communication)

