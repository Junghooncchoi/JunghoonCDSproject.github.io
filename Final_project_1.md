title: “[Final Project_1]”
permalink: / https://JunghoonCDSproject.github.io/Final_project_1.md

# Post 

## Introduction
The objective of this project is to identify hidden characteristics of Seoul Public Bike (Ddareungi).
Classify stations into meaningful ecological groups using clustering analysis.
ALl the transaction data was based in Decemner 2024
---

## 📖  Paper Methodology Summary
*Summarize the 4-step framework proposed in the paper in your own words.*

Clustering is an unsupervised learning technique, meaning it lacks ground-truth labels. This makes the results inherently difficult to interpret and trust. To bridge this gap, this paper proposes a **4-step explainable clustering framework**:

1. **Data Preprocessing**: merging  datasets in the zip file.
2. **Dimensionality Reduction**: Eliminating noise and terminate unusing features for better visualization and performance.
3. **Clustering**: Grouping data points into optimal, distinct clusters.
4. **Classification for Explainability**: Training a supervised classification model using the generated cluster labels as targets. This allows us to use feature importance metrics to explain *why* the data points were grouped together, providing crucial transparency.

---

## 📊 2. Dataset Description
Describe your chosen dataset source and its variables.*

* **Source**:https://data.seoul.go.kr/dataList/datasetList.do# -
  
# Data Sources

| Dataset | Features Generated |
|----------|----------|
| `공공자전거 대여소 정보(25.6월 기준).xlsx` | total_rack_count, qr_ratio, station_age_days |
| `서울특별시 공공자전거 대여이력 정보_2412.csv` | avg_trip_duration, avg_distance, round_trip_ratio, sprout_bike_ratio, foreigner_ratio, nonmember_ratio |
| `서울특별시 공공자전거 이용정보(시간대별)_202412.csv` | weekend_ratio, rush_hour_ratio, late_night_ratio, hourly_entropy, peak_concentration, temporal_stability |
| `서울특별시 공공자전거 이용정보(월별)_24.7-12.csv` | male_ratio, youth_ratio, middle_age_ratio, senior_ratio, other_age_ratio, age_entropy |
| `tpss_bcycl_od_statnhm_20241201~31.csv` | destination_entropy, inflow_outflow_ratio, degree_centrality, closeness_centrality, betweenness_centrality |
| `서울특별시 공공자전거 외국인 대여정보(일별)_24.7-12.csv` | foreigner_activity, foreigner_balance, foreigner_stability, foreigner_daily_mean |
| `data_2412.csv` | avg_rack_count, rack_variability, rack_stability, low_rack_ratio, peak_rack_pressure |

## 1. Station Information

Station-Level Feature Construction

A total of 36 engineered station-level features were constructed.

# Feature Engineering

## Infrastructure Features

| Variable         | Definition              | Formula                            |
| ---------------- | ----------------------- | ---------------------------------- |
| total_rack_count | Total rack capacity     | LCD + QR                           |
| qr_ratio         | QR rack proportion      | QR / Total                         |
| station_age_days | Days since installation | Reference Date − Installation Date |

### Rationale

These variables measure station maturity, infrastructure scale, and modernization level.
QR is next version of LCD (bike type).

---

## Mobility Features

| Variable          | Definition              | Formula                                 |
| ----------------- | ----------------------- | --------------------------------------- |
| avg_trip_duration | Average trip duration   | Mean(usage_time)                        |
| avg_distance      | Average travel distance | Mean(usage_distance)                    |
| round_trip_ratio  | Return-to-origin ratio  | Same origin & destination / Total trips |
| sprout_bike_ratio | Sprout bike usage ratio | Sprout trips / Total trips              |
| foreigner_ratio   | Foreigner ratio         | Foreigner trips / Total trips           |
| nonmember_ratio   | Non-member ratio        | Non-member trips / Total trips          |

### Rationale

Mobility features capture whether stations are used primarily for commuting, recreation, tourism, or short-distance travel.

---

## Temporal Features

| Variable           | Definition              | Formula                        |
| ------------------ | ----------------------- | ------------------------------ |
| weekend_ratio      | Weekend usage share     | Weekend Usage / Total Usage    |
| rush_hour_ratio    | Rush-hour usage share   | Rush Hour Usage / Total Usage  |
| late_night_ratio   | Late-night usage share  | Late Night Usage / Total Usage |
| hourly_entropy     | Temporal diversity      | -Σ p log(p)                    |
| peak_concentration | Peak-hour concentration | Max Hour Usage / Total Usage   |
| temporal_stability | Usage stability         | 1 - SD / Mean                  |

### Rationale

Temporal variables identify commuter-oriented stations, nightlife stations, and recreational stations.

---

## Demographic Features

| Variable         | Definition               | Formula                  |
| ---------------- | ------------------------ | ------------------------ |
| male_ratio       | Male user share          | Male Usage / Total Usage |
| youth_ratio      | Youth share              | (~10s + 20s) / Total     |
| middle_age_ratio | Middle-age share         | (30s+40s+50s) / Total    |
| senior_ratio     | Senior share             | (60s+70+) / Total        |
| other_age_ratio  | Other age category share | Other / Total            |
| age_entropy      | Age diversity            | -Σ p log(p)              |

### Rationale

Demographic composition helps distinguish stations serving students, commuters, seniors, or mixed populations.

---

## Network Features

| Variable               | Definition            | Formula                         |
| ---------------------- | --------------------- | ------------------------------- |
| destination_entropy    | Destination diversity | -Σ p log(p)                     |
| inflow_outflow_ratio   | Flow balance          | Inflow / Outflow                |
| degree_centrality      | Connectivity          | NetworkX Degree Centrality      |
| closeness_centrality   | Accessibility         | NetworkX Closeness Centrality   |


### Rationale

These variables quantify each station's role within the citywide mobility network.

---

## Foreigner Features

| Variable             | Definition                       | Formula             |
| -------------------- | -------------------------------- | ------------------- |
| foreigner_activity   | Total foreigner activity         | Rentals + Returns   |
| foreigner_balance    | Foreigner flow balance           | Returns / Rentals   |
| foreigner_stability  | Foreigner usage stability        | 1 - SD / Mean       |
| foreigner_daily_mean | Average daily foreigner activity | Mean Daily Activity |

### Rationale

These variables identify tourism hotspots and internationally active mobility nodes.

## ❓ 3. Research Question
*How can explainable cluster analysis uncover different usage patterns among Seoul public bike rental stations?*


---

## 💻 4. Initial Data Exploration (.ipynb)
The initial exploratory data analysis (EDA), including missing value checks and descriptive statistics, is documented in the Jupyter Notebook below:

* 🔗 [View Initial Data Exploration Notebook](./Final_project_303.ipynb)

---



