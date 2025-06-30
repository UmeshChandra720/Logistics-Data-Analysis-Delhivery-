# 🚚 Logistics Trip Analysis Project

This project focuses on analyzing logistics trip-level data to uncover performance insights, identify inefficiencies, and propose actionable recommendations for operational improvement.

## 📌 Objective

To perform exploratory data analysis (EDA), feature engineering, and statistical testing on delivery trip data to understand patterns in time, distance, delivery performance, and operational behavior.

---

## 📂 Dataset Overview

The dataset contains **trip-level segment data** for deliveries with 24 columns and includes:
- Timestamps (`trip_creation_time`, `od_start_time`, `od_end_time`)
- Source/Destination info (`source_center`, `destination_center`, `source_name`, `destination_name`)
- Time and distance metrics (`actual_time`, `osrm_time`, `actual_distance_to_destination`, etc.)
- Segment-level and total-level route information

---

## 🔧 Steps Performed

### 1. 📥 Data Preprocessing
- Converted datatypes (`datetime64`, `category`)
- Replaced nulls in `source_name` and `destination_name` with `"UNKNOWN"`
- Removed unnecessary columns like `cutoff_factor`, `segment_factor`
- Dropped duplicates and cleaned anomalies

### 2. 📊 Exploratory Data Analysis
- Uncovered patterns in trip frequency across **days**, **weeks**, and **months**
- Identified top performing **states** and **cities** in source and destination

### 3. 🧮 Feature Engineering
- Extracted new features from datetime: `trip_creation_hour`, `weekday`, `month`, `weekofyear`
- Parsed `source_name` and `destination_name` into `city` and `state`

### 4. 🧪 Hypothesis Testing
- Checked normality using Shapiro-Wilk
- Used **Mann-Whitney U test** to compare:
  - `actual_time` vs `osrm_time`
  - `od_total_time` vs `start_scan_to_end_scan`
  - Segment-level and trip-level time/distance

### 5. 🧼 Outlier Detection
- Applied **IQR method** to detect and count extreme values in time and distance columns

### 6. ⚖️ Feature Scaling
- Used both **MinMaxScaler** and **StandardScaler** for modeling readiness

---

## 📈 Key Insights

- 🕒 87.9% of trips occurred in **September**; highest trip creation at **10 P.M**
- 🚛 **Carting** trips made up **60.2%** vs **FTL (39.8%)**
- 🌆 **Mumbai**, **Bengaluru**, **Gurgaon** dominate both source and destination cities
- 📉 Statistical tests reveal significant difference between predicted and actual times/distances (OSRM engine needs improvement)

---

## ✅ Final Recommendations

1. Optimize OSRM routing algorithms to improve accuracy in ETAs and distances.
2. Investigate cities/states with high traffic to optimize delivery operations.
3. Enhance route efficiency for long-distance FTL deliveries.
4. Improve data capture in missing or inconsistent location fields.
5. Leverage peak delivery times (evenings, mid-month) for resource planning.
6. Study outliers in delivery time to prevent operational delays.
