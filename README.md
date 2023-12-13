# Global Salaries
Data Exploration on Global AI, ML, Data (including Analyst, Scientist, and Engineer) Salaries
Data Source = [https://ai-jobs.net/salaries/](https://ai-jobs.net/salaries/download/)https://ai-jobs.net/salaries/download/

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
Based on its value counts, the overwhelming majority of employment type is full-time. Contract, part-time, and full-time jobs only occured less than 50 times combined. Based on this information, it is decided that the analysis will be performed only on full-time entries.

