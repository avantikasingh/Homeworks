For Q5:
There are three common table expressions (CTEs): 
EmployeesJoined to calculate the count of employees who returned to work, 
EmployeesLeft to calculate the count of employees who left the company, 
and TotalEmployees to calculate the total count of employees on each floor.

These CTEs are joined to calculate the turnover rate for each floor during the specified date range.
The LEFT JOIN ensures that even floors with no employee turnover during the period are included in the result.
The turnover rate calculation involves table division, as we divide the left_count by the total_count and multiply by 100 to get the percentage.