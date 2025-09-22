📊 Churn Analysis Project
📌 Overview

This is an end-to-end churn analysis pipeline built using SQL Server Management Studio 21 (SSMS 21), Power BI, and Python.
The project helps businesses understand churn patterns, build predictive insights, and design proactive strategies to reduce customer churn.

🎯 Problem Statement

Customer churn — when customers stop using a service — leads to significant revenue loss. Businesses need to:

Identify customers at risk of leaving

Understand key churn drivers

Take proactive actions to retain them

This project provides a data-driven churn analysis solution by combining SQL, Power BI, and Python.

🛠️ Tech Stack

SQL Server Management Studio 21 (SSMS 21): ETL, data cleaning, preprocessing, and view creation

Power BI: Data transformation, modeling, and interactive dashboards

Python (Pandas, NumPy, Matplotlib, Scikit-learn): EDA 

Machine Learning Algorithm - Random Forests Regression

GitHub: Version control and project hosting

🔄 Project Workflow
1️⃣ SQL Server (ETL & Data Cleaning)

Imported raw customer dataset into SSMS 21

Cleaned missing values, duplicates, and invalid entries

Created staging & production tables for analysis

Built views to separate churned vs. retained customers

2️⃣ Power BI (Transformations & Dashboards)

Transformations (Power Query):

prod_Churn Table → Added Churn Status flag, Monthly Charge ranges

mapping_AgeGrp Table → Categorized age into groups (<20, 20–35, 36–50, >50)

mapping_TenureGrp Table → Grouped tenure into <6M, 6–12M, 12–18M, 18–24M, >=24M

prod_Services Table → Unpivoted services, renamed fields for clarity

Key DAX Measures:

Total Customers = COUNT(prod_Churn[Customer_ID])

New Joiners = CALCULATE(COUNT(prod_Churn[Customer_ID]), prod_Churn[Customer_Status] = "Joined")

Total Churn = SUM(prod_Churn[Churn Status])

Churn Rate = [Total Churn] / [Total Customers]

3️⃣ Python (EDA & Prediction)

EDA: Correlation heatmaps, feature distributions, churn trend analysis

Models: Logistic Regression, Decision Tree, and Random Forest for churn prediction

Insights: Identified key drivers of churn and generated retention strategies

📊 Dashboard Preview

Summary Page: KPIs, churn trends, customer demographics(https://github.com/Ahadxcode/Churn-Analysis-Project/blob/main/ChurnAnalysisPrediction.png)

Prediction Page: Predicted churners count with visualizations (https://github.com/Ahadxcode/Churn-Analysis-Project/blob/main/ChurnAnalysisSummary.png)

🚀 Future Improvements

Deploy ML model as an API for real-time predictions

Automate ETL pipeline using Airflow / SSIS

Enable live database connections for dashboard refresh

👨‍💻 Developed By

Ahad Khan
