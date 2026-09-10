# 🌾 Harvest Risk Analysis — Horticulture Commodities Across Districts in East Java

📌 Project Overview

This project analyzes the risk of declining horticultural harvest yields across districts/cities in East Java, Indonesia, using environmental quality indices combined with agricultural production data. The analysis groups districts into risk categories through unsupervised clustering, helping local governments identify priority regions for intervention.

## Business/Research Problem 

  Several districts in East Java face the risk of declining harvest yields due to climate change, land degradation, water quality decline, and air pollution —
  creating challenges for regional food security and farmer welfare.
  
  This analysis aims to answer the following questions:
  
  How can districts/cities in East Java be grouped based on similarities in environmental quality and agricultural production?
  Which districts fall into high, medium, and low harvest-risk categories?
  Which environmental factors (land, water, air quality) most strongly relate to production stability?
  Which districts and commodities dominate horticultural production in the region?
  What policy approach fits each risk category?

## Dataset

The dataset combines secondary data from Open Data Jawa Timur and Badan Pusat Statistik (BPS) Jawa Timur, covering all districts/cities for the period 2023–2024. It is cross-sectional in nature, representing conditions for a single time period across all regions.

Key variables include:

Luas Panen — harvested area
IKLH — Environmental Quality Index (Indeks Kualitas Lingkungan Hidup)
IKA — Water Quality Index (Indeks Kualitas Air)
IKU — Air Quality Index (Indeks Kualitas Udara)
IKL — Land Quality Index (Indeks Kualitas Lahan)
Total Produksi — total seasonal vegetable/horticulture production per district

## Tools
Python (Google Colab) — data cleaning, feature engineering, Agglomerative Hierarchical Clustering, Silhouette Score & dendrogram evaluation
SHAP — feature importance / risk factor interpretation
Looker Studio — interactive dashboard for visualizing production and risk clusters

## Analysis & Key Findings
1. Data Preparation

Production data and environmental index data were standardized and merged by district/city code into a single integrated dataset.

District/city names were standardized to uppercase with a "KABUPATEN/KOTA" prefix for consistency
Missing production values were imputed with zero to avoid bias in total production calculations
A new feature, total_produksi, was engineered by aggregating all crop production per district, alongside the average of the environmental quality indices
Numeric variables were scaled to ensure balanced contribution across features — a necessary step before clustering

Insight: Careful standardization and feature engineering were essential prerequisites for producing a reliable and homogeneous clustering result.

2. Clustering Methodology

Agglomerative Hierarchical Clustering (Ward linkage, Euclidean distance) was applied to group districts based on total production and environmental quality indices.

A dendrogram was used to visually determine the optimal number of clusters, revealing three main clusters
Cluster quality was validated using the Silhouette Score, confirming a homogeneous and reliable grouping
Clusters were mapped into index categories (Poor, Moderate, Good) and production categories (Low, Moderate, High)

Insight: The three-cluster structure enabled a clear, interpretable framework for converting raw environmental and production data into actionable risk tiers.

3. Risk Classification Framework

Based on the cluster mapping, districts were classified into three harvest-risk levels:

Risk Level	Criteria
High Risk	Poor environmental index + High production
Medium Risk	Other combinations
Low Risk	Good environmental index + High production

Insight: High current productivity does not guarantee future sustainability — districts with high production but poor environmental quality are the most vulnerable to future yield decline.

4. Regional Interpretation
Surabaya and Malang — high production but classified as high risk due to poor environmental quality
Kota Batu — a strong example of low risk, maintaining balance between productivity and environmental quality
Some districts show relatively good environmental quality but still low production — indicating potential for improvement through better land optimization and agricultural technology
Districts with both good environmental quality and high production were classified as low risk, though continued environmental maintenance remains important for long-term sustainability

Insight: Each risk category requires a distinct policy approach — environmental restoration for high-risk areas, capacity building for medium-risk areas, and sustainability-focused programs for low-risk areas.

5. Production Overview (2024)
East Java's horticultural production grew 2.76% compared to the previous year
The largest contributors were Kabupaten Malang, Pasuruan, and Probolinggo
Dominant commodities: cabai (chili), bawang merah (shallots), and kentang (potato)
Most districts fall into the medium risk category overall

Insight: Growth in aggregate production coexists with uneven environmental sustainability across regions — underscoring the need for region-specific rather than uniform agricultural policy.

## Recommendations
1. Prioritize Environmental Recovery in High-Risk Districts

High-risk districts (e.g., Surabaya, Malang) should be prioritized for land rehabilitation, water conservation, and the adoption of environmentally friendly farming practices to protect long-term production sustainability.

2. Build Production Capacity in Medium-Risk Districts

Medium-risk regions should be directed toward increasing production capacity through agricultural technology adoption, input subsidies, and farmer mentoring/assistance programs for sustainable land optimization.

3. Maintain and Add Value in Low-Risk Districts

Low-risk districts (e.g., Kota Batu) should focus on maintaining environmental quality while developing added value, such as horticultural agrotourism, to serve as a model of best practice for other regions.

4. Integrate Environmental Monitoring into Agricultural Policy

Local governments should continue to track environmental indices (IKLH, IKA, IKU, IKL) alongside production data, rather than relying on production volume alone, to detect early warning signs of future yield decline.

5. Use the Risk Dashboard for Ongoing Decision-Making

The Looker Studio dashboard should be used as a living tool for policymakers to monitor cluster shifts over time and reassess district risk levels as new BPS/Open Data updates become available.

## Dashboard

An interactive dashboard was built using Looker Studio to visualize production trends, environmental quality indices, and the resulting risk clusters by district/city, presented through charts, tables, and maps.

🔗 Live Dashboard: https://lookerstudio.google.com/u/3/reporting/5ef719bc-2572-4186-93cc-f70297076a2e

## Conclusion

This research shows that environmental conditions have a significant influence on the stability of horticultural production in East Java. Using Agglomerative Clustering, districts/cities were successfully grouped into three risk categories — high, medium, and low — based on the interaction between environmental quality and production levels.

The findings highlight that high productivity today does not guarantee sustainability tomorrow if environmental quality continues to decline. Policy strategies should therefore be tailored to each risk category: environmental restoration for high-risk areas, capacity building for medium-risk areas, and sustainability/value-added development for low-risk areas.

## Skills Demonstrated
Secondary data collection and integration (BPS, Open Data Jawa Timur)
Data cleaning, standardization, and feature engineering
Unsupervised machine learning (Agglomerative Hierarchical Clustering)
Model evaluation (Silhouette Score, dendrogram analysis)
Model interpretability with SHAP
Python programming in Google Colab
Dashboard development with Looker Studio
Academic research writing and policy recommendation development


