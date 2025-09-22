📊 Churn Analysis Project
📌 Overview

This project is an end-to-end churn analysis pipeline built using SQL Server Management Studio 21 (SSMS 21), Power BI, and Python.
The goal is to understand customer churn patterns, create interactive dashboards, and build predictive insights to help businesses reduce churn.

It covers:

ETL and data cleaning in SQL Server (SSMS 21)

Data transformation and visualization in Power BI

Exploratory Data Analysis (EDA) and predictive modeling in Python

🔹 Problem Statement

Customer churn (when customers stop using a service) causes significant revenue loss. Businesses need to:

Identify which customers are likely to leave

Understand factors driving churn

Take proactive measures to retain customers

This project demonstrates a data-driven solution using SQL, Power BI, and Python to analyze churn, visualize insights, and predict at-risk customers.

🔹 Tech Stack

SQL Server Management Studio 21 (SSMS 21) → ETL, data cleaning, preprocessing, and view creation

Power BI → Data transformation, modeling, interactive dashboards

Python (Pandas, NumPy, Matplotlib, Scikit-learn) → EDA and churn prediction

GitHub → Version control and project hosting

🔹 Project Workflow
1. SQL Server Management Studio 21 (ETL & Data Cleaning)

Imported raw customer dataset into SSMS 21.

Cleaned missing values, duplicates, and invalid entries.

Created staging and production tables for analysis.

Built views for Churned vs Stayed customers.

2. Power BI (Transformations & Dashboards)
🔹 Power Query Transformations

prod_Churn Table:

Churn Status → 1 if Customer_Status = "Churned" else 0

Monthly Charge Range → Grouped as <20, 20–50, 50–100, >100

mapping_AgeGrp Table:

Age groups: <20, 20–35, 36–50, >50 with sorting column

mapping_TenureGrp Table:

Tenure groups: <6M, 6–12M, 12–18M, 18–24M, >=24M with sorting

prod_Services Table:

Unpivoted service-related columns

Renamed Attribute → Services and Value → Status

🔹 DAX Measures

Summary Page:

Total Customers = COUNT(prod_Churn[Customer_ID])
New Joiners = CALCULATE(COUNT(prod_Churn[Customer_ID]), prod_Churn[Customer_Status] = "Joined")
Total Churn = SUM(prod_Churn[Churn Status])
Churn Rate = [Total Churn] / [Total Customers]


Churn Prediction Page:

Count Predicted Churner = COUNT(Predictions[Customer_ID]) + 0
Title Predicted Churners = "COUNT OF PREDICTED CHURNERS : " & COUNT(Predictions[Customer_ID])

3. Python (EDA & Prediction)

Conducted Exploratory Data Analysis: correlation heatmaps, feature distribution, and churn patterns.

Built predictive models (Logistic Regression, Decision Tree) to identify at-risk customers.

Generated insights to improve retention strategies.

🔹 Dashboard Preview

Summary Page: KPIs, churn trends, demographics

Prediction Page: Predicted churners count and visualization

🔹 Future Improvements

Deploy predictive model as an API for real-time churn prediction

Automate ETL pipeline using Airflow or SSIS

Integrate live database connections for dashboard refresh

👨‍💻 Developed By

Ahad Khan