# ⌛  Case Study - Customer Retention
# Data Exploration - Cleansing

<p align="right"> Excel - Power Query</p>

## :books: Table of Contents <!-- omit in toc -->


## 💻 Data exploration

---
- customerID: 7043 customers
- gender: Male or Female
- SeniorCitizen: 0 or 1
- Partner: No or Yes
- Dependants: No or Yes
- tenure: Min 0, Max 72
- PhoneService: No or Yes
- MultipleLines: No, Yes or No phone service
- InternetService: No, DSL or Fiber optic
- OnlineSecurity: No, Yes or No internet service
- OnlineBackup: No, Yes or No internet service
- DeviceProtection: No, Yes or No internet service
- TechSupport: No, Yes or No internet service
- StreamingTV: No, Yes or No internet service
- StreamingMovies: No, Yes or No internet service
- Contract: Month-to-month, One year, Two year
- PaperlessBilling: No or Yes
- PaymentMethod: Bank transfer (automatic), Credit card (automatic), Mailed Check, Electronic Check
- MonthlyCharges: Min 18.25, Max 118.75
- TotalCharges: Min 18.8, Max 8684.8, 11 blank cell
- numAdminTickets: Min 0, Max 5
- numTechTickets: Min 0, Max 9
- Churn: No or Yes

---
## 🧽 Cleansing data

- Replace value No/Yes from Churn column
```
= Table.ReplaceValue(#"Changed Type","Yes","Churned",Replacer.ReplaceText,{"Churn"})
= Table.ReplaceValue(#"Replaced Value","No","Stayed",Replacer.ReplaceText,{"Churn"})
```
- Add column YearCategory
```
= Table.AddColumn(#"Replaced Value1", "YearCategory", each if [tenure] <= 12 then "0-1" else if [tenure] <= 24 then "1-2" 
else if [tenure] <= 36 then "2-3" else if [tenure] <= 48 then "3-4" else if [tenure] <= 60 then "4-5" else if [tenure] <= 72 
then "5-6" else "6+")
```
---
## 🧮 Measures

- ChurnRate
```
ChurnRate = DIVIDE(CALCULATE(COUNT(churn_dataset[Churn]),churn_dataset[Churn]="Churned"),COUNT(churn_dataset[Churn]))
```
- PercentRevenueLoss
```
PercentRevenueLoss = DIVIDE(CALCULATE(sum(churn_dataset[TotalCharges]),churn_dataset[Churn]="Churned"),sum(churn_dataset[TotalCharges]))
```

