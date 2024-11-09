# HR Database Queries

A collection of SQL queries for analyzing employee data in an HR database. These queries provide insights into employee information, departmental statistics, salary analysis, and management structures.

## Table of Contents
- [Features](#features)
- [Database Schema](#database-schema)
- [Query Examples](#query-examples)
- [Prerequisites](#prerequisites)
- [Usage](#usage)

## Features
- Department and employee analytics
- Salary analysis and market corrections
- Management hierarchy visualization
- Location-based employee distribution
- Job category analysis

## Database Schema
The queries work with the following main tables:
- `employees`
- `departments`
- `jobs`
- `locations`
- `countries`

## Query Examples

### Department Analysis
```sql
SELECT 
  d.department_name,
  COUNT(e.employee_id) AS employee_count,
  AVG(e.salary) AS avg_salary
FROM employees e
JOIN departments d ON e.department_id = d.department_id
GROUP BY d.department_name;
```

### Salary Market Correction
```sql
WITH employee_job_details AS (
  SELECT
    e.employee_id,
    e.first_name,
    e.last_name,
    d.department_name,
    FLOOR(DATEDIFF(CURDATE(), e.hire_date) / 365) AS years_experience,
    e.salary AS current_salary,
    j.max_salary
  FROM employees e
  JOIN jobs j ON e.job_id = j.job_id
  JOIN departments d ON e.department_id = d.department_id
)
```

## Prerequisites
- MySQL 5.7 or higher
- Access to HR database schema
- Basic SQL knowledge

## Usage
1. Clone this repository
2. Connect to your MySQL database
3. Execute the queries using your preferred SQL client
4. Modify the queries as needed for your specific use case

## Contact
[Akhtar Al - (https://www.linkedin.com/in/akhtarali07/)
Project Link: (https://github.com/akhtarali007/Oracle-HR-Database-SQL)
