# Global Salaries
Data Exploration on Global AI, ML, Data (including Analyst, Scientist, and Engineer) Salaries
Data Source = [https://ai-jobs.net/salaries/](https://ai-jobs.net/salaries/download/)https://ai-jobs.net/salaries/download/

To view the notebook better directly on a browser, use this NBViewer link: https://nbviewer.org/github/mezkymy/global-salaries/blob/main/global-salaries.ipynb

## Goal
The goal of this project is to explore the dataset available on ai-jobs.net and find any interesting insights and gain understanding on variables that might influence salaries on the data world.

## Variables/Features
Using `.info()` method, there are 10 columns identified in this dataset:

|No.|Column Name|Count|Type|
|---|--------------------|----------------|------|
|0  |work_year           |8805 non-null   |int64 |
|1  |experience_level    |8805 non-null   |object|
|2  |employment_type     |8805 non-null   |object|
|3  |job_title           |8805 non-null   |object|
|4  |salary              |8805 non-null   |int64 |
|5  |salary_currency     |8805 non-null   |object|
|6  |salary_in_usd       |8805 non-null   |int64 |
|7  |employee_residence  |8805 non-null   |object|
|8  |remote_ratio        |8805 non-null   |int64 |
|9  |company_location    |8805 non-null   |object|
|10 |company_size        |8805 non-null   |object|

In this project, we will focus on salary (in USD) relationship to work year, experience level, employment type, job title, employee residence, remote ratio, company location, and company size. Salary and salary currency will not be included since it becomes redundant with the availability of salary (in USD) data.

There are 8805 entries in this dataset and no missing values in any columns.

## Outliers and Exceptions

![Employment Type Count](https://github.com/mezkymy/global-salaries/assets/79908491/ddf9a7c9-3a15-4ab4-91c4-9f327bffd91e)

Based on its value counts, the overwhelming majority of employment type is full-time. Contract, part-time, and full-time jobs only occured less than 50 times combined. Based on this information, it is decided that the analysis will be performed only on full-time entries.

Based on experience level and company size, there is one category on both variables that is significantly larger in their number of samples than the rest of categories, but other categories still have a decent amount of samples.

## Job Titles Grouping

In the filtered dataset, there are 121 unique job titles. Some of the job titles are similar (some even only differ in the usage of abbreviations), while others are also on the same group or performs a very similar role, or difference in hierarchy - which should already be represented with `experience_level`. To simplify the analysis, these job titles are grouped into 8 main groups (+ Others for other job titles that are unable to be grouped to any of the 8 main groups) based on authors knowledge, assumptions, and information from online sources. 

Do note that this grouping might be imperfect since it is mainly limited to the authors knowledge and assumptions, and job titles are not always indicative on the actual role of the respondents since the job title for the actual role is decided by each company; for example in some companies a Data Analyst might actually perform Data Science/Engineer role. The main groups are:

|Job Title Group|Count|
|---------------------------------|----|
|Data Engineer                    |2388|
|Data Scientist                   |2101|
|Data Analyst                     |1662|
|Machine Learning                 |1195|
|Research Scientist               | 666|
|Business Intelligence/Analyst    | 317|
|Data Operations                  | 269|
|AI Developer/Engineer            | 119|
|Others                           |  45|

Since there are only 45 job titles grouped in `Others`, this group entries shall be removed and not analyzed further since the number of sample is too small and it is a combination of various jobs that might be very different and not comparable to each other.

## Company Locations Filtering
List of company locations that occurs more than 50 times in the filtered dataset:

|Country Code|Count|
|------|----|
|US    |7513|
|GB    | 421|
|CA    | 203|
|ES    | 108|
|DE    |  70|

While there are 57 different countries where the data are sourced from, only 5 countries have more than 50 entries each. Since having less than 50 data may result in sampling bias due to the lack of samples, the analysis will focus only on the 5 countries. The filtered dataset (combined with all the other filtering above) results in 8315 remaining entries, which is still around 94% of the original dataset.

## Analysis
### Company Size to Salary
![Salary Range on Each Company Size](https://github.com/mezkymy/global-salaries/assets/79908491/dd79677b-d2c3-4962-b929-69dd90403d36)


Tukey HSD shows that the difference between medium sized and large sized companies are very insignificant, with a p-value nearing 1. This shows that statistically speaking there is no significant difference in the salary of large sized and medium sized companies.

One looking for a higher salary could try to get into either medium or large companies with no significant difference in either choice.

### Job Title to Annual Salary
![Average Salary of Data Scientists from 2020 to 2023](https://github.com/mezkymy/global-salaries/assets/79908491/6b0230a5-2e0e-4b94-9667-d471b5d4a8ee)


Data Scientist salaries across the board are increasing annually, except at 2021 where it shows a decline from 142k to 114k. From 2020 to 2023, it shows a quite significant growth from 142k to 169k (+27k), which is around 20% increase over 3 years or around 6% annual increase. This increase is similar to the US total inflation from 2020-2023 which is around 19% compounded (source: [usinflationcalculator.com](https://www.usinflationcalculator.com/inflation/current-inflation-rates/))

### Others
For complete analysis, open the notebook using github/jupyter/NBViewer (link to NBViewer provided at the [top](#global-salaries))
