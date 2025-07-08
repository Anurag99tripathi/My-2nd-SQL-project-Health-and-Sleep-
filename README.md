# My-2nd-SQL-project-Health-and-Sleep-
"A data analysis project exploring how sleep patterns—duration and quality—impact physical and mental health. Using Python and data visualization to uncover correlations between sleep habits and health outcomes for better wellness insights."

use sql_project;

SELECT * FROM sql_project.`sleep health`;

-- 1. Average Sleep Duration by Age Group

SELECT 
      CASE
WHEN age < 25 THEN 'young'
WHEN age BETWEEN 25 AND 40 THEN 'adult'
WHEN age > 40 THEN 'senior'
END AS age_group,
ROUND (AVG(`Sleep Duration` ) ,2) AS AVG_SLEEP
FROM sql_project.`sleep health`
GROUP BY age;


-- 2. Stress Level vs Sleep Quality

SELECT `Stress Level`,
       ROUND(AVG(`quality of sleep` ) , 2) AS avg_sleep_quality 
FROM sql_project.`sleep health`
GROUP BY `Stress Level`
ORDER BY `Stress Level`
       
       
-- 3. Top Occupations With Low Sleep Quality


SELECT Occupation, 
       COUNT(*) AS People_Low_Sleep
FROM sql_project.`sleep health`
WHERE `Quality of Sleep` < 6
GROUP BY Occupation
ORDER BY People_Low_Sleep DESC
LIMIT 5;


-- 4. Steps vs Sleep Duration (Correlation Check)

SELECT `Daily Steps`, 
       `Sleep Duration`
FROM sql_project.`sleep health`;
