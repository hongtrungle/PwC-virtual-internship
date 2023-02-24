# :telephone:  Case Study:  Call Centre Trends
<img width="715" alt="Screen Shot 2021-06-15 at 5 23 06 PM" src="https://user-images.githubusercontent.com/95112831/221083069-ef6e713c-ee0a-4d53-b0d7-425ddd86db6e.png">

Create a dashboard in Power BI for Claire that reflects all relevant Key Performance Indicators (KPIs) and metrics in the dataset. Get creative! 

__Possible KPIs include (to get you started, but not limited to):__

- Overall customer satisfaction
- Overall calls answered/abandoned
- Calls by time
- Average speed of answer
- Agent’s performance quadrant -> average handle time (talk duration) vs calls answered

# :bookmark_tabs:  Dataset

---
### Call center dataset

- Call Id	: id of the call
- Agent	: name of agent
- Date	: date of call
- Time	: time of call
- Topic	: topic of call
- Answered (Y/N): Did the call answered?
- Resolved: Did the call resolved the problem?
- Speed of answer in seconds
- AvgTalkDuration	: Average talk duration
- Satisfaction rating

<div align="center"> 
First 10 rows
</div>

| Call Id| Agent     | Date  | Time    | Topic   | Answered(Y/N) | Resolved| Speed of answer in seconds | AvgTalkDuration | Satisfaction rating|
|:-------|:----------|:------|:--------|:--------|:--------------|:--------|:---------------------|:--------|:----|
|ID0001|	Diane   |	2021-01-01  |	9:12:58 |	Contract related    |	Y |	Y   |	109 |	0:02:23 |	3   |  
|ID0002|    Becky   |	2021-01-01  |	9:12:58 |	Technical Support   |	Y |	N   |	70  |	0:04:02 |	3   |
|ID0003|	Stewart |	2021-01-01  |	9:47:31 |	Contract related    |	Y |	Y   |	10  |	0:02:11 |   3   |
|ID0004|	Greg    |   2021-01-01  |	9:47:31 |	Contract related    |	Y |	Y   |	53  |	0:00:37 |   2   |
|ID0005|	Becky   |   2021-01-01	|   10:00:29|	Payment related     |	Y |	Y   |	95  |	0:01:00 |   3   |
|ID0006|	Stewart	|   2021-01-01	|   10:00:29|	Technical Support   |	N |	N   |		|           |       |	
|ID0007|	Diane	|   2021-01-01	|   10:22:05|	Payment related     |	Y |	Y   |	24  |	0:03:40 |   2   |
|ID0008|	Diane	|   2021-01-01	|   10:22:05|	Payment related     |	Y |	Y   |	22  |	0:00:38 |   4   |
|ID0009|	Greg    |	2021-01-01  |	11:13:55|	Admin Support       |	Y |	Y   |	15  |	0:06:38 |   4   |

# :toolbox:   Tools used in this case study

---
- Excel: data exploration 
- Power BI: cleaning and visualizing data