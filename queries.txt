--Join GDP and public school student count.
SELECT  
	gdp_info.REF_DATE AS 'Start of School Year',
	gdp_info.GEO AS 'Region',
	gdp_info.VALUE AS 'GDP',
	SUM(student_population.VALUE) AS 'Total Students'
FROM student_population
	JOIN gdp_info ON SUBSTR(student_population.REF_DATE,1,4) = gdp_info.REF_DATE
WHERE gdp_info.Estimates = 'Gross domestic product at market prices'
GROUP BY 1, 2
ORDER BY 2, 1;
