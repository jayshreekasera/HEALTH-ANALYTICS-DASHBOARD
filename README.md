# HEALTH-ANALYTICS-DASHBOARD
SQL QUERIES- 
# -- 1. Count & Pct of F vs M that have OCD & -- Average Obsession Score by Gender
 select
  gender,
  count(`Patient ID`) as patient_count,
  round(count(`Patient ID`)*100/(select count(*) from ocd_patient_dataset),2) as percentage,
  avg(`Y-BOCS Score (Obsessions)`) as avg_obs_score
  from ocd_patient_dataset
  group by Gender
 

# -- 2. Count of Patients by Ethnicity and their respective Average Obsession Score

select
	Ethnicity,
	count(`Patient ID`) as patient_count,
	avg(`Y-BOCS Score (Obsessions)`) as obs_score
From health_data.ocd_patient_dataset
Group by 1
Order by 2;

# -- 3. Number of people diagnosed with OCD MoM

# -- alter table health_data.ocd_patient_dataset
# -- modify `OCD Diagnosis Date` date;
select
date_format(`OCD Diagnosis Date`, '%Y-%m-01 00:00:00') as month,
-- `OCD Diagnosis Date`
count(`Patient ID`) patient_count
from health_data.ocd_patient_dataset
group by 1
Order by 1
;

# -- 4. What is the most common Obsession Type (Count) & it's respective Average Obsession Score

Select
`Obsession Type`,
count(`Patient ID`) as patient_count,
round(avg(`Y-BOCS Score (Obsessions)`),2) as obs_score
from health_data.ocd_patient_dataset
group by 1
Order by 2
;

# -- 5. What is the most common Compulsion type (Count) & it's respective Average Obsession Score

Select
`Compulsion Type`,
count(`Patient ID`) as patient_count,
round(avg(`Y-BOCS Score (Obsessions)`),2) as obs_score
from health_data.ocd_patient_dataset
group by 1
Order by 2
;
