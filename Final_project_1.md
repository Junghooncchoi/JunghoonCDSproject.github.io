---
layout: page
title: "[Final Project_1]"
permalink: / https://JunghoonCDSproject.github.io/Final_project_1.md
---

## 📖 1. Paper Methodology Summary
*Summarize the 4-step framework proposed in the paper in your own words.*

Clustering is an unsupervised learning technique, meaning it lacks ground-truth labels. This makes the results inherently difficult to interpret and trust. To bridge this gap, this paper proposes a **4-step explainable clustering framework**:

1. **Data Preprocessing**: merging  datasets in the zip file.
2. **Dimensionality Reduction**: Eliminating noise and terminate unusing features for better visualization and performance.
3. **Clustering**: Grouping data points into optimal, distinct clusters.
4. **Classification for Explainability**: Training a supervised classification model using the generated cluster labels as targets. This allows us to use feature importance metrics to explain *why* the data points were grouped together, providing crucial transparency.

---

## 📊 2. Dataset Description
*Describe your chosen dataset source and its variables.*

* **Source**:https://data.seoul.go.kr/dataList/OA-15182/F/1/datasetView.do# - [서울특별시 공공자전거 대여이력 정보_2025.zip]
* **Observations**: 150 samples (Meets the minimum requirement of 100)
* **Key Variables**:

| Variable Name | Data Type | Description |
| :--- | :--- | :--- |
| 자전거번호 | Categorical | Bicycle identification number |
| 대여일시 | Datetime | Date and time when the bicycle was rented |
| 대여 대여소번호 | Numerical | Rental station identification number |
| 대여 대여소명 | Categorical | Name of the rental station |
| 대여거치대 | Numerical | Rental dock/rack number |
| 반납일시 | Datetime | Date and time when the bicycle was returned |
| 반납대여소번호 | Numerical | Return station identification number |
| 반납대여소명 | Categorical | Name of the return station |
| 반납거치대 | Numerical | Return dock/rack number |
| 이용시간(분) | Numerical | Total usage time in minutes |
| 이용거리(M) | Numerical | Total travel distance in meters |
| 생년 | Numerical | Birth year of the user |
| 성별 | Categorical | Gender of the user |
| 이용자종류 | Categorical | Type/category of user |
| 대여대여소ID | Categorical | Rental station ID code |
| 반납대여소ID | Categorical | Return station ID code |
| 자전거구분 | Categorical | Type/category of bicycle |
---

## ❓ 3. Research Question
*How can explainable cluster analysis uncover different usage patterns among Seoul public bike rental stations?*


---

## 💻 4. Initial Data Exploration (.ipynb)
The initial exploratory data analysis (EDA), including missing value checks and descriptive statistics, is documented in the Jupyter Notebook below:

* 🔗 [View Initial Data Exploration Notebook](./Final_project_303.ipynb)
