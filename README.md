Markdown
### Data cleaning & Transformation
-- Create a temp table called cleandata
-- Remove duplicates
-- Combine the two activity tables to create one master table
-- Create a new column called total_min by using addition operator to add the activity min
```sql
with cleandata as (select distinct ActivityDate, TotalSteps, LightlyActiveMinutes, FairlyActiveMinutes, VeryActiveMinutes, SedentaryMinutes, Calories
FROM `case-study-bellabeat-490020.activity.activity1` 
union all  
SELECT distinct ActivityDate, TotalSteps, LightlyActiveMinutes, FairlyActiveMinutes, VeryActiveMinutes, SedentaryMinutes, Calories
FROM `case-study-bellabeat-490020.activity.activity2`
order by ActivityDate)
select ActivityDate,TotalSteps,Calories,LightlyActiveMinutes, FairlyActiveMinutes, VeryActiveMinutes, SedentaryMinutes,(LightlyActiveMinutes+FairlyActiveMinutes+VeryActiveMinutes+SedentaryMinutes)as total_min
from cleandata
order by ActivityDate;
```
