🏢 Cooperative Performance Clustering & Android App — Dinas Koperasi Jawa Timur

📌 Project Overview

This project was developed during a certified internship (Magang Bersertifikat MBKM) at the Dinas Koperasi, Usaha Kecil dan Menengah (UKM) Provinsi Jawa Timur, placed under the Subbagian Penyusunan Program dan Anggaran. The project analyzes and clusters the performance of cooperatives across East Java using K-Means Clustering, and translates the results into an Android application prototype to help the agency monitor cooperative performance more efficiently.

## Business Problem

East Java recorded a decline of 656 active cooperative units, driven by highly varied cooperative performance across the province. The agency needed a data-driven way to group cooperatives by performance level so that coaching and support programs can be targeted at the units that need it most.

This project aims to answer the following questions:

How can cooperatives across East Java be grouped based on their performance indicators?
How many distinct performance clusters exist, and how are they characterized?
Which clusters represent high-performing, growing, and underperforming cooperatives?
How can these clustering results be made accessible and actionable for the agency's supervision team through a mobile application?

## Dataset

The dataset consists of 12,121 records and 39 variables, covering cooperative data across districts/cities in East Java, including:

IDKOP — unique cooperative ID
KOPERASI — cooperative name
ALAMAT, DESA, KELURAHAN, KECAMATAN, KABUPATEN — location fields
BENTUK KOPERASI, JENIS KOPERASI — cooperative form and type
ASSET — total assets
VOLUME USAHA — business volume
JUMLAH ANGGOTA — number of members
SISA HASIL USAHA (SHU) — net operating surplus

The three core clustering parameters used to represent cooperative performance were Asset, Volume Usaha, and Jumlah Anggota, as these are the standard indicators commonly used to assess cooperative health.

## Tools
Python (Google Colab) — data cleaning, feature engineering, K-Means clustering (scikit-learn)
Pandas / NumPy — data preprocessing and log transformation
Matplotlib / Seaborn — Elbow Method and cluster visualization
PCA (Principal Component Analysis) — dimensionality reduction for 2D cluster visualization
Microsoft Excel & Power BI — supporting data exploration and reporting
Kotlin (Android Studio) — mobile application prototype (UI/UX design)

## Analysis & Key Findings
1. Data Preparation & Feature Engineering
- Explored dataset dimensions (12,121 rows × 39 columns) and data types
- Checked skewness of key features (JUMLAH ANGGOTA: 73.09, ASSET: 46.77, VOLUME USAHA: 66.07) — all highly right-skewed
- Applied log transformation to reduce skewness before scaling
- Applied StandardScaler to normalize feature scales, and PCA to reduce dimensionality for visualization

  Insight: The raw performance indicators were extremely skewed (a small number of very large cooperatives), making log transformation and scaling essential   
  preprocessing steps before clustering could produce meaningful groups.

2. Determining the Optimal Number of Clusters
- Tested cluster counts from k=2 to k=10 using the Elbow Method (inertia) and Silhouette Score
- Both methods converged on k=3 as the optimal number of clusters
  
  Insight: A 3-cluster structure aligns naturally with a practical performance framework — advanced, developing, and needs-improvement — making the results
  directly usable for policy segmentation.

3. Clustering Results

    K-Means clustering (k=3) grouped cooperatives into three performance tiers:
    
    Cluster	Cooperative Count	Characteristics
    Koperasi Maju (Advanced)	3,680 units	Highest performance based on member count, asset, and business volume; can serve as a model/example for other
    cooperatives
    Koperasi Berkembang (Developing)	4,761 units	Shows good growth potential; needs a push to move up to the advanced tier
    Koperasi Perlu Ditingkatkan (Needs Improvement)
    
    The clustering model was evaluated together with the agency's supervisory division and achieved an accuracy of up to 90%, confirming that the K-Means grouping
    effectively reflects real-world cooperative performance levels.
    
    Insight: Nearly a third of cooperatives (3,700 units) fall into the "needs improvement" tier — this is the priority segment for targeted coaching and
    financial/technical assistance programs.

4. Android Application Prototype
  
    Based on the clustering model, an Android application prototype (built in Kotlin) was designed to make the results accessible to the agency's field team:
    
    Home/Dashboard: overview of total cooperatives and cluster distribution (donut chart, bar chart, scatter plot of clusters)
    Cluster list: browsable list of cooperatives grouped by tier (Unggul/Berkembang/Perlu Ditingkatkan), with search and map view
    Cooperative detail page: shows cooperative type, address, contact info, and its assigned cluster/performance profile
    
    The application went through a revision iteration — the initial version was refined based on feedback to improve clarity of the cluster explanation and data
    presentation shown to end users (dinas staff).
    
    Note: The application is currently a UI/UX design prototype; backend development and REST API integration were not completed within the internship timeframe
    due to time constraints.

## Recommendations
  1. Prioritize Coaching for the "Needs Improvement" Cluster
  The 3,700 cooperatives in this tier should be the primary target for hands-on coaching, access-to-financing programs, and operational capacity building, since
  they show the largest gap in members, assets, and business volume.
  
  3. Use "Advanced" Cooperatives as Mentor/Model Units
  The 3,680 top-performing cooperatives could be leveraged as mentors or case studies in training programs for developing and underperforming cooperatives,
  accelerating knowledge transfer within the sector.
  
  3. Push "Developing" Cooperatives Toward the Advanced Tier
  The largest segment (4,761 units) already shows growth potential — targeted incentives or streamlined access to business expansion support could help this group
  graduate into the advanced tier.
  
  5. Complete Backend Development for the Android App
  To move from prototype to a usable tool, the next phase should prioritize backend development and REST API integration so field staff can access up-to-date
  clustering data directly from the app rather than static reports.

  5. Re-run Clustering Periodically
  Since cooperative performance changes over time, the clustering pipeline should be re-run on a regular basis (e.g., annually) so the agency's intervention
  targeting stays current.

## Dashboard / Application Prototype

  Based on the clustering model, an Android application prototype (built in Kotlin) was designed to make the results accessible to the agency's field team.
  1. Home Page (redesigned) — now leads with key summary numbers: total cooperatives in East Java (20,885) and total cooperatives included in the clustering model
     (12,122), followed by a "Koperasi Unggulan" (Featured Cooperatives) section listing top-tier cooperatives (e.g., Koperasi Konsumen HIMPAUDI Kecamatan Semen,
     KPPS Al Karomah Makmur Jaya, Koperasi Petani Ngoom B...).
  2. Cooperative Detail Page — tapping a cooperative opens its profile, showing: cooperative logo/icon, jenis koperasi (cooperative type), alamat lengkap (full
     address), kabupaten/kota, informasi kontak (phone/email, marked "tidak tersedia" when not on file), and a short profil koperasi description.
  3. Hasil Clustering (Clustering Results) Page — a donut chart breaking down cooperatives by cluster with percentages and average business volume per tier, e.g.,
     Maju 30.20% (avg. Volume Usaha ~Rp1.3M), Berkembang 39.28% (~Rp750K), Belum Berkembang 30.53% (~Rp500K).
  4. Statistik Page — shows the total number of cooperatives used in the analysis (12,122), a bar chart of cooperative categories/types ("Diagram Bidang Kategori
     Koperasi"), and a scatter chart illustrating business volume growth trends ("Diagram Pertumbuhan Volume Usaha").

## Conclusion

This internship project demonstrated that K-Means Clustering can effectively segment East Java's cooperatives into three actionable performance tiers — advanced, developing, and needs-improvement — based on asset, business volume, and membership data, achieving up to 90% agreement with the agency's own performance assessments. The resulting Android application prototype provides a foundation for translating this analysis into a practical monitoring tool for policymakers.

The experience combined applied data science (K-Means clustering, feature engineering, model evaluation) with mobile application design, and was carried out within a real government agency setting — offering direct, hands-on exposure to how data-driven decision-making supports public sector policy on cooperative and SME development.

## Skills Demonstrated
- Data cleaning, feature engineering, and skewness correction on real-world government data (12K+ records)
- Unsupervised machine learning (K-Means Clustering) in Python (scikit-learn)
- Model selection using Elbow Method and Silhouette Score
- Dimensionality reduction and visualization with PCA
- Data analysis with Excel and Power BI
- Android application design and prototyping (Kotlin, UI/UX)
- Cross-functional collaboration within a government agency (Dinas Koperasi dan UKM Provinsi Jawa Timur)
- Technical reporting and stakeholder presentation
