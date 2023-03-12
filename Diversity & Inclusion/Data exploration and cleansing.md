# :balance_scale:  Case Study - Diversity & Inclusion
# Data Exploration - Cleansing

<p align="right"> Excel - Power Query</p>

## :books: Table of Contents <!-- omit in toc -->


## 💻 Data exploration

---
- Employee ID: 500 employees
- Gender: Male or Female
- Job level after FY20 promotion: 6 job levels
- New hire FY20?: N or Y
- FY20 Performance Rating: 1-4, 87 blank cells
- Promotion in FY21?: No or Yes
- FY20 leaver?: No or Yes
- In base group for turnover FY20: N or Y
- Department @01.07.2020: 6 departments
- Last Department in FY20: 6 departments
- Job Level group for PRA: 5 job level, 62 blank cells
- Time in Job Level @01.07.2020: 0-9
- Job Level before FY20 promotions: 6 job levels, 66 blank cells
- Age group: 6 age groups 
- Nationality 1: 
- Region group: nationality 1: 5 region groups
- Years since last hire: 0-9

---
## 🧽 Cleansing data

- Replace value N/Y from column 'New hire FY20?' to No/Yes
- Replace value N/Y from column 'In base group for turnover FY20?' to No/Yes
---
## 🧮 Measures

- Number of fy20 leavers
```
#_of_fy20_leavers = CALCULATE(COUNT('Pharma Group AG'[Employee ID]),'Pharma Group AG'[FY20 leaver?]="Yes")
```
- Number of fy21 promoted
```
#_of_fy21_promoted = CALCULATE(COUNT('Pharma Group AG'[Promotion in FY21?]),'Pharma Group AG'[Promotion in FY21?]="Yes")
```
- Number of hires fy20
```
#_of_hires_fy20 = CALCULATE(COUNT('Pharma Group AG'[New hire FY20?]),'Pharma Group AG'[New hire FY20?]="Yes")
```
- Number of men
```
#_of_men = CALCULATE(COUNT('Pharma Group AG'[Employee ID]),'Pharma Group AG'[Gender]="Male")
```
- Number of women
```
#_of_women = CALCULATE(COUNT('Pharma Group AG'[Employee ID]),'Pharma Group AG'[Gender]="Female")
```
- % employees promoted fy21
```
%_employees_promoted_fy21 = DIVIDE(CALCULATE(COUNT('Pharma Group AG'[Promotion in FY21?]),'Pharma Group AG'[Promotion in FY21?]="Yes"),
CALCULATE(COUNT('Pharma Group AG'[In base group for Promotion FY21]),'Pharma Group AG'[In base group for Promotion FY21]="Yes"))
```
- % of hires men
```
%_of_hires_men = DIVIDE(CALCULATE(COUNT('Pharma Group AG'[New hire FY20?]),'Pharma Group AG'[New hire FY20?]="Yes",'Pharma Group AG'[Gender]="Male"),
CALCULATE(COUNT('Pharma Group AG'[New hire FY20?]),'Pharma Group AG'[New hire FY20?]="Yes"))+0
```
- % of hires women 
```
%_of_hires_women = DIVIDE(CALCULATE(COUNT('Pharma Group AG'[New hire FY20?]),'Pharma Group AG'[New hire FY20?]="Yes",'Pharma Group AG'[Gender]="Female"),
CALCULATE(COUNT('Pharma Group AG'[New hire FY20?]),'Pharma Group AG'[New hire FY20?]="Yes"))+0
```
- % of men
```
%_of_men = DIVIDE(CALCULATE(COUNT('Pharma Group AG'[Employee ID]),'Pharma Group AG'[Gender]="Male"),COUNT('Pharma Group AG'[Employee ID]))
```
- % of promoted men
```
%_of_promoted_men = DIVIDE(CALCULATE(COUNT('Pharma Group AG'[Promotion in FY21?]),'Pharma Group AG'[Promotion in FY21?]="Yes",'Pharma Group AG'[Gender]="Male"),
CALCULATE(COUNT('Pharma Group AG'[Promotion in FY21?]),'Pharma Group AG'[Promotion in FY21?]="Yes"))
```
- % of women 
```
%_of_women = DIVIDE(CALCULATE(COUNT('Pharma Group AG'[Employee ID]),'Pharma Group AG'[Gender]="Female"),COUNT('Pharma Group AG'[Employee ID]))+0
```
- % of promoted women 
```
%_of_promoted_women = DIVIDE(CALCULATE(COUNT('Pharma Group AG'[Promotion in FY21?]),'Pharma Group AG'[Promotion in FY21?]="Yes",'Pharma Group AG'[Gender]="Female"),
CALCULATE(COUNT('Pharma Group AG'[Promotion in FY21?]),'Pharma Group AG'[Promotion in FY21?]="Yes"))
```
- % turnover fy20 
```
%_turnover_fy20 = DIVIDE(CALCULATE(COUNT('Pharma Group AG'[FY20 leaver?]),'Pharma Group AG'[FY20 leaver?]="Yes"),
CALCULATE(COUNT('Pharma Group AG'[In base group for turnover FY20]),'Pharma Group AG'[In base group for turnover FY20]="Yes"))
```
- % turnover men 
```
%_turnover_men = DIVIDE(CALCULATE(COUNT('Pharma Group AG'[FY20 leaver?]),'Pharma Group AG'[FY20 leaver?]="Yes",'Pharma Group AG'[Gender]="Male"),
CALCULATE(COUNT('Pharma Group AG'[FY20 leaver?]),'Pharma Group AG'[FY20 leaver?]="Yes"))+0
```
- % turnover women 
```
%_turnover_women = DIVIDE(CALCULATE(COUNT('Pharma Group AG'[FY20 leaver?]),'Pharma Group AG'[FY20 leaver?]="Yes",'Pharma Group AG'[Gender]="Female"),
CALCULATE(COUNT('Pharma Group AG'[FY20 leaver?]),'Pharma Group AG'[FY20 leaver?]="Yes"))+0
```
- Average performance rating
```
avg_perf_rating = CALCULATE(AVERAGE('Pharma Group AG'[FY20 Performance Rating]),'Pharma Group AG'[New hire FY20?]="No")
```
- Average performance rating leavers 
```
avg_perf_rating_leavers = CALCULATE(AVERAGE('Pharma Group AG'[FY20 Performance Rating]),'Pharma Group AG'[FY20 leaver?]="Yes")
```
- Average performance rating men 
```
avg_perf_rating_men = CALCULATE(AVERAGE('Pharma Group AG'[FY20 Performance Rating]),'Pharma Group AG'[Gender]="Male",'Pharma Group AG'[New hire FY20?]="No")
```
- Average performance rating stayers 
```
avg_perf_rating_stayers = CALCULATE(AVERAGE('Pharma Group AG'[FY20 Performance Rating]),'Pharma Group AG'[FY20 leaver?]="No",'Pharma Group AG'[New hire FY20?]="No")
```
- Average performance rating women 
```
avg_perf_rating_women = CALCULATE(AVERAGE('Pharma Group AG'[FY20 Performance Rating]),'Pharma Group AG'[Gender]="Female",'Pharma Group AG'[New hire FY20?]="No")
```

