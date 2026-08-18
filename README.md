# MySQL Employee Database – Querying and Analysis
 
## 📌 Project Overview
 
This project demonstrates the use of SQL queries to retrieve, filter, sort, group, and analyze employee data in MySQL.
 
The following SQL operations were performed:
 
- DISTINCT
- Aliases using AS
- WHERE clause and operators
- UPDATE
- ORDER BY
- LIMIT
- Aggregate Functions
- GROUP BY
- HAVING
- INNER JOIN
- LEFT JOIN
- RIGHT JOIN
## 🛠️ Tools Used
 
- MySQL
- MySQL Workbench
## 📂 SQL Queries Performed
 
### 1. DISTINCT Values
 
**Retrieve distinct salaries from the Employees table**
 
```sql
SELECT DISTINCT salary
FROM employees;
```
 
### 2. Alias (AS)
 
**Provide aliases for age and salary**
 
```sql
SELECT age AS Employee_Age,
       salary AS Employee_Salary
FROM employees;
```
 
### 3. WHERE Clause & Operators
 
**Retrieve employees with a salary greater than ₹50,000 and hired before January 1, 2016**
 
```sql
SELECT employee_name, salary, hire_date
FROM employees
WHERE salary > 50000
  AND hire_date < '2016-01-01';
```
 
**Find the employee whose designation is missing**
 
```sql
SELECT *
FROM employees
WHERE designation IS NULL;
```
 
**Update the missing designation to "Data Scientist"**
 
```sql
UPDATE employees
SET designation = 'Data Scientist'
WHERE designation IS NULL;
```
 
### 4. Sorting and Grouping Data
 
**ORDER BY — Sort employees by Department ID in ascending order and Salary in descending order**
 
```sql
SELECT employee_name, department_id, salary
FROM employees
ORDER BY department_id ASC, salary DESC;
```
 
**LIMIT — Display the first 5 employees hired in the year 2018**
 
```sql
SELECT employee_name, hire_date
FROM employees
WHERE YEAR(hire_date) = 2018
LIMIT 5;
```
 
### 5. Aggregate Functions
 
**Calculate the sum of all salaries in the Finance department**
 
```sql
SELECT SUM(salary) AS Total_Salary
FROM employees
WHERE department_id = 7;
```
 
> **Note:** Update the `department_id` based on the ID assigned to the Finance department in your table.
 
**Find the minimum age among all employees**
 
```sql
SELECT MIN(age) AS Minimum_Age
FROM employees;
```
 
### 6. GROUP BY
 
**List the maximum salary for each location**
 
```sql
SELECT location_id,
       MAX(salary) AS Maximum_Salary
FROM employees
GROUP BY location_id;
```
 
**Calculate the average salary for each designation containing the word "Analyst"**
 
```sql
SELECT designation,
       AVG(salary) AS Average_Salary
FROM employees
WHERE designation LIKE '%Analyst%'
GROUP BY designation;
```
 
### 7. HAVING
 
**Find departments with less than 3 employees**
 
```sql
SELECT department_id,
       COUNT(*) AS Employee_Count
FROM employees
GROUP BY department_id
HAVING COUNT(*) < 3;
```
 
**Find locations with female employees whose average age is below 30**
 
```sql
SELECT location_id,
       AVG(age) AS Average_Age
FROM employees
WHERE gender = 'Female'
GROUP BY location_id
HAVING AVG(age) < 30;
```
 
## 🔗 Joins
 
### 1. INNER JOIN
 
**List employee names, their designations, and department names where employees are assigned to a department**
 
```sql
SELECT e.employee_name,
       e.designation,
       d.department_name
FROM employees e
INNER JOIN departments d
ON e.department_id = d.department_id;
```
 
### 2. LEFT JOIN
 
**List all departments along with the total number of employees in each department**
 
This query also includes departments with no employees.
 
```sql
SELECT d.department_id,
       d.department_name,
       COUNT(e.employee_id) AS Employee_Count
FROM departments d
LEFT JOIN employees e
ON d.department_id = e.department_id
GROUP BY d.department_id, d.department_name;
```
 
### 3. RIGHT JOIN
 
**Display all locations along with employee names assigned to each location**
 
Locations without employees will display NULL for the employee name.
 
```sql
SELECT l.location_id,
       l.location,
       e.employee_name
FROM employees e
RIGHT JOIN location l
ON e.location_id = l.location_id;
```
 
## 📊 Key SQL Concepts Practiced
 
| SQL Concept | Purpose |
|---|---|
| DISTINCT | Removes duplicate values |
| AS | Provides aliases for columns |
| WHERE | Filters rows based on conditions |
| UPDATE | Modifies existing data |
| ORDER BY | Sorts query results |
| LIMIT | Restricts the number of rows returned |
| SUM() | Calculates the total |
| MIN() | Finds the minimum value |
| MAX() | Finds the maximum value |
| AVG() | Calculates the average |
| COUNT() | Counts records |
| GROUP BY | Groups rows with similar values |
| HAVING | Filters grouped results |
| INNER JOIN | Returns matching records from both tables |
| LEFT JOIN | Returns all records from the left table |
| RIGHT JOIN | Returns all records from the right table |
 
## 🎯 Learning Outcome
 
Through this assignment, I practiced querying and analyzing data using MySQL. I gained hands-on experience with:
 
- Filtering and sorting data
- Aggregate functions
- Grouping data using GROUP BY
- Filtering grouped data using HAVING
- Using WHERE conditions
- Working with INNER JOIN, LEFT JOIN, and RIGHT JOIN
This assignment helped strengthen my understanding of how relational databases can be queried to extract meaningful insights from employee, department, and location data.
 
## 👩‍💻 Author
 
**Revathi**
Aspiring Data Analyst
