🔹 Power BI Transformations & Measures
✅ Power Query Transformations
1. Add Calculated Columns in prod_Churn

Churn Status

= if [Customer_Status] = "Churned" then 1 else 0


(Change data type → Whole Number)

Monthly Charge Range

= if [Monthly_Charge] < 20 then "< 20" 
  else if [Monthly_Charge] < 50 then "20-50" 
  else if [Monthly_Charge] < 100 then "50-100" 
  else "> 100"

2. Create mapping_AgeGrp Table (Reference from prod_Churn)

Keep only Age column → Remove duplicates.

Age Group

= if [Age] < 20 then "< 20" 
  else if [Age] < 36 then "20 - 35" 
  else if [Age] < 51 then "36 - 50" 
  else "> 50"


AgeGrpSorting

= if [Age Group] = "< 20" then 1 
  else if [Age Group] = "20 - 35" then 2 
  else if [Age Group] = "36 - 50" then 3 
  else 4


(Change data type → Whole Number)

3. Create mapping_TenureGrp Table (Reference from prod_Churn)

Keep only Tenure_in_Months column → Remove duplicates.

Tenure Group

= if [Tenure_in_Months] < 6 then "< 6 Months" 
  else if [Tenure_in_Months] < 12 then "6-12 Months" 
  else if [Tenure_in_Months] < 18 then "12-18 Months" 
  else if [Tenure_in_Months] < 24 then "18-24 Months" 
  else ">= 24 Months"


TenureGrpSorting

= if [Tenure Group] = "< 6 Months" then 1 
  else if [Tenure Group] = "6-12 Months" then 2 
  else if [Tenure Group] = "12-18 Months" then 3 
  else if [Tenure Group] = "18-24 Months" then 4 
  else 5


(Change data type → Whole Number)

4. Create prod_Services Table (Reference from prod_Churn)

Unpivot all service-related columns.

Rename columns:

Attribute → Services

Value → Status

✅ DAX Measures
📊 Summary Page

Total Customers

Total Customers = COUNT(prod_Churn[Customer_ID])


New Joiners

New Joiners = 
CALCULATE(
    COUNT(prod_Churn[Customer_ID]),
    prod_Churn[Customer_Status] = "Joined"
)


Total Churn

Total Churn = SUM(prod_Churn[Churn Status])


Churn Rate

Churn Rate = [Total Churn] / [Total Customers]

📈 Churn Prediction Page

Count Predicted Churner

Count Predicted Churner = COUNT(Predictions[Customer_ID]) + 0


Title Predicted Churners

Title Predicted Churners = 
"COUNT OF PREDICTED CHURNERS : " & COUNT(Predictions[Customer_ID])