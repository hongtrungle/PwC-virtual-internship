# :telephone:  Case Study - Call Center Trends
# Data Exploration - Cleansing

<p align="right"> Excel - Power Query</p>

## :books: Table of Contents <!-- omit in toc -->


## 💻 Data exploration

---
- Call Id: There are 5000 calls in total.
- Agent: 8 agents - Becky, Dan, Diane, Greg, Jim, Joe, Martha and Stewart.
- Date: 01/01/2021 to 31/03/2021
- Time: 9am - 18pm
- Topic: 5 topics - Admin support, Contract related, Payment related, Streaming, Technical support.
- Answered(Y/N): Yes or No
- Resolved: Yes or No
- Speed of answer in seconds: Min(10), Max(125), 946 blank values (Answered = No)
- AvgTalkDuration: Min(30s), Max(7mins), 946 blank values (Answered = No)
- Satisfaction Rating: From 1 to 5, 946 blank values (Answered = No)

---
## 🧽 Cleansing data

- Change type 
```
= Table.TransformColumnTypes(Source,{{"Call Id", type text}, {"Agent", type text}, {"Date", type date}, {"Time", type time}, {"Topic", type text}, 
{"Answered (Y/N)", type text}, {"Resolved", type text}, {"Speed of answer in seconds", Int64.Type}, {"AvgTalkDuration", type duration}, 
{"Satisfaction rating", Int64.Type}})
```
- Transform column AvgTalkDuration to seconds unit
```
= Table.TransformColumns(#"Changed Type",{{"AvgTalkDuration", Duration.TotalSeconds, type number}})
```
- Call time (AM or PM) 
```
= Table.AddColumn(#"Changed Type", "AM/PM", each Text.End(Text.From([Time], "en-US"), 2), type text)
```

---
## 🧮 Measures

- Total Calls
```
TotalCalls = COUNT(call_center_tbl[Answered (Y/N)])
```
- Number of calls answered
```
CallsAnswered = CALCULATE(COUNT(call_center_tbl[Answered (Y/N)]),call_center_tbl[Answered (Y/N)]="Y")
```
- Percent of calls answered
```
PercentofAnswered = [CallsAnswered]/[TotalCalls]
```
- Number of calls resolved
```
CallsResolved = CALCULATE(COUNT(call_center_tbl[Resolved]),call_center_tbl[Resolved]="Y")
```
- Percent of calls resolved
```
PercentOfResolved = [CallsResolved]/[TotalCalls]
```
- Average call duration
```
CallDuration = AVERAGE(call_center_tbl[AvgTalkDuration])
```
- Average speed of answer
```
SpeedOfAnswer = AVERAGE(call_center_tbl[Speed of answer in seconds])
```


