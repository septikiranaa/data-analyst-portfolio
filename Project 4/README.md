# Project 4 - Olist E-Commerce Analysis

SQL & Power BI analysis using the Brazilian E-Commerce Public Dataset by Olist.

# Business Background & Problem Statement
Dalam industri distribusi candy, efisiensi rute pengiriman sangat memengaruhi biaya operasional dan kepuasan pelanggan. Beberapa factory berjarak sangat jauh (rata-rata >9.000 km) dari kota-kota dengan penjualan tertinggi seperti New York City, Los Angeles, Philadelphia, San Francisco, dan Seattle — menimbulkan tantangan biaya dan waktu pengiriman.
Problem statement :
Bagaimana meningkatkan efisiensi distribusi ke kota-kota dengan penjualan tertinggi (3–5 area) yang menyumbang 10% dari total penjualan perusahaan dalam waktu 1 tahun, menggunakan data latitude dan longitude?
Objective: Meningkatkan efisiensi distribusi ke kota-kota strategis tersebut melalui evaluasi jarak factory–kota dan realokasi produksi berbasis data geospasial.

Possible Root Causes (dugaan awal):
Geographical Distance — jarak factory ke kota permintaan tinggi terlalu jauh
Disparity in Factory Location — sebaran factory tidak merata / terkonsentrasi di wilayah tertentu
High Customer Demand in Distant Areas — permintaan tinggi justru berasal dari kota yang jauh dari factory utama

# Root Cause Analysis (Fishbone)

Dianalisis melalui 3 cabang utama penyebab rendahnya efisiensi distribusi:

1. Competitor
- Kompetitor menawarkan biaya lebih murah
- Layanan pengiriman lebih cepat
- Kualitas produk lebih baik

2. Location
- Jarak antara factory dan customer terlalu jauh (fokus analisis)
- Data latitude/longitude yang tidak akurat pada beberapa entri (fokus analisis)

3. Cost
- Ship Mode: selisih order date & ship date terlalu lama; Same Day Mode terlalu mahal namun sulit dipenuhi jika jarak jauh
Route Distribution: rute tidak optimal, distribusi ke kota berpenjualan tinggi tidak efisien, kurangnya perencanaan logistik

## Metodologi & Alur Kerja
Problem Understanding — merumuskan masalah bisnis & tujuan analisis
Data Preparation & Cleaning — membersihkan 10.194 record, 39 variabel dari 5 tabel
Perhitungan Jarak Geospasial (karena dataset asli tidak menyediakan kolom jarak):
Metode Haversine (asumsi bumi bulat sempurna) — dihitung manual di Excel
Metode Vincenty (asumsi bumi elipsoid, lebih presisi) — dihitung dengan Python (geopy)
Data final memakai hasil Vincenty karena lebih akurat (selisih dengan Haversine kecil tapi tidak signifikan)
Exploratory Data Analysis (EDA)
Data Analysis — analisis penjualan & produk, analisis jarak factory-kota, evaluasi mode pengiriman
Data Visualization — dashboard interaktif multi-panel
Insight & Recommendation

# Dataset 
Sumber : kanggle
