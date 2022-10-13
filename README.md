# Pewlett-Hackard-Analysis

## Overview of the analysis: 
The purpose of the analysis is to figure out the number of employees who are going to retire by title and also to identify a certain set of employees who are eligigble for a mentorship program based on some conditions. 

## Results: 

Based on the recent analysis and the queries ran on the tables, it is evident that a huge number of Senior Engineer and Senior Staff are going to retire from the organization. This constitues over 70% of the workforce. 

![ScreenShot](https://github.com/LIPSASHARMA/Pewlett-Hackard-Analysis/blob/main/Resources/employees_retiring.png)

If we look at the data that we fetched from the mentorship query, it is evident that the number of people eligible for mentorship are nowhere close to the number of people retiring from the organization. We see that the ratio is approximately 0.0214 or 2.14%, which is really less. This indicates there will be a huge number of positions that need to be filled. 

![ScreenShot](https://github.com/LIPSASHARMA/Pewlett-Hackard-Analysis/blob/main/Resources/employees_eligible_mentorship.png)

There is a huge amount of Engineers in the retirees list that make up to approxiately half of the workforce that are going to retire. 

A similar trend is seen with regards to the employees eligible for mentorship where we observe that approximately 43% of employees are engineers who are eligible for mentorship.

## Summary: 

How many roles will need to be filled as the "silver tsunami" begins to make an impact?
Answer: The total number of roles to be filled in are 72,458

Are there enough qualified, retirement-ready employees in the departments to mentor the next generation of Pewlett Hackard employees?
Answer: I think there are sufficient number of employees who are retiring and they are eligible for mentorship. 
To find this we will first get the count of people eligible for mentorship per department. This can be done using the query as:

  SELECT title,
  	COUNT(title)
  INTO mentor_count
  FROM mentorship_eligibility
  GROUP BY title;

  We can then do the comparison by doing a join on the tables with mentors grouped by titles and the people retiring also grouped by titles. 
  You can see the details by running the query below.

SELECT rt.title,
  	rt.count as retire_count,
  	mtc.count as menti_count
INTO compare_table
FROM retiring_titles as rt
LEFT JOIN mentor_count as mtc
ON (rt.title = mtc.title);