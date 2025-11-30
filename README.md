<p align="center">
  <img src="Banner image/banner.jpg" width="100%" />
</p>

# 🚖 NYC TLC Data Engineering Pipeline

A production-grade, end-to-end data engineering and analytics pipeline built from **NYC Taxi & Limousine Commission (TLC)** trip records.  
This project demonstrates real-world data engineering, data cleaning, feature engineering, EDA, statistics, and clustering — structured cleanly for recruiters, data science managers, and portfolio reviewers.

---

# 🏗️ Project Overview
This project implements a **full-stack data workflow**:

- 🕸 **Web Scraping** TLC website for dataset links
- 📁 **Dataset Selection Logic** (best-coverage year, taxi type, file type)
- 💾 **Automated Downloading** of monthly parquet files
- 🧱 **Consolidation** into a single year-level dataset
- 🧪 **Deterministic 12K Sample** for reproducible analysis
- ⚙️ **Feature Engineering** (duration, speed, temporal features)
- 📊 **Advanced EDA** (correlations, distributions, outliers)
- 📉 **Statistics** (ANOVA, regression, effect size)
- 🤖 **KMeans Clustering** for trip pattern segmentation
- 🖼 **Automatic Plot Export** to `results/plots/`

---

# 📂 Repository Structure
```
nyc-tlc-data-engineering-pipeline/
│
├── data/
│   ├── raw/            # Monthly parquet files
│   ├── processed/      # Consolidated & sample datasets
│
├── results/
│   └── plots/          # Exported PNG charts
│
├── notebooks/
│   └── nyc-tlc-data-engineering-pipeline.ipynb
│
├── README.md
└── requirements.txt
```

---

# 🚀 Pipeline Breakdown

## **1️⃣ Web Scraping**
A custom HTML parser extracts dataset URLs + metadata (taxi type, year, month, file format).

## **2️⃣ Automatic Dataset Selection**
Selects:
- Taxi type → **Yellow**
- Year with maximum monthly parquet coverage → **2025**
- Parquet-only for schema stability

## **3️⃣ Dataset Consolidation**
- Downloads all monthly files
- Merges into: `nyc_tlc_primary.parquet`
- Creates reproducible sample: `nyc_tlc_sample_12000.csv`

## **4️⃣ Feature Engineering**
- `trip_duration_min`
- `speed_mph`
- `pickup_hour`
- `weekday`, `is_weekend`

---

# 📊 Exploratory Data Analysis & Visuals
Below are the exported charts stored in `results/plots/`.

## 🔥 Correlation Heatmap
Shows strong relationships between distance, fare, and duration.
```
results/plots/corr_heatmap.png
```

## 🕒 Trips by Hour
Distribution of pickup hours (sample skew noted).
```
results/plots/trips_by_hour.png
```

## ⚡ Speed vs Distance
Identifies realistic taxi speeds + outliers.
```
results/plots/speed_vs_distance.png
```

## 💵 Weekday vs Weekend Fare Distribution
Compares fare patterns across days.
```
results/plots/fare_weekday_vs_weekend.png
```

## 🧠 KMeans Trip Segmentation
Clustered patterns in trip behavior.
```
results/plots/kmeans_trip_clusters.png
```

## 💰 Revenue by Hour
Revenue concentration insights.
```
results/plots/revenue_by_hour.png
```

---

# 📉 Statistical Analysis Summary

### **📌 Pearson Correlation**
- Distance ↔ Fare = **0.76** (strong)

### **📌 OLS Regression**
```
Fare ≈ 4.05 * Distance + intercept
R² ≈ 0.573
```
✔ Distance reliably predicts fare

### **📌 ANOVA (hourly differences)**
- F = **2.28**
- p = **0.033**
→ Small but significant effect of hour on fare

### **📌 Cohen's d**
- Not stable in this sample (variance issues), but distributions are visually similar

---

# 🧠 Key Insights
- Trip distance is the **strongest driver of fare**, consistent with taxi pricing.
- Late-night hours contribute **highest revenue**, reflecting nightlife + airport arrivals.
- KMeans reveals clear **trip-type clusters** (city trips vs long airport rides).
- Outlier speeds indicate expected real-world noise in manually logged datasets.
- Even a small, well-sampled subset provides strong predictive signals.

---

# 🛠 Tech Stack
- Python 3
- pandas, numpy
- pyarrow
- seaborn, matplotlib
- statsmodels
- scikit-learn
- Jupyter / Google Colab

---

# 🧑‍💻 Author
**Mugunthan Kesavan**  
Engineering Data Science, University of Houston  
Portfolio-ready data engineering & analytics case study

---

If you like this project, ⭐ star the repo and share it! 🚀

