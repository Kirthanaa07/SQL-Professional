# Subqueries

## Background Information
This chapter covers how to use subqueries to enhance your query filtering.  Subqueries are essentially queries nested inside of a larger query.

- Subqueries can occur in SELECT, FROM and WHERE clauses.
- They can be nested inside of SELECT, INSERT, UPDATE and DELETE statements.
- A subquery is sometimes referred to as the inner query while the statement containing the subquery is called the outer query.
- The inner query executes first so that it's results can be passed to the outer query.


## Subqueries in the SELECT clause

Example:

```sql
SELECT column_name1 , column_name2,
 (SELECT AVG(column_name) 
   FROM table1 WHERE column_name OPERATOR value) AS column_name3 
FROM   table1;
```

Real Life example:
```sql
-- This statement finds the final grade for a student based on the sum of their assignment scores.
SELECT s.student_id, s.FirstName, s.LastName, 
(
     SELECT sum(score)
     FROM assignments
     WHERE assignments.student_id = s.student_id
) AS final_grade 
  FROM students s; 
```

<br>

## Subqueries in the WHERE clause

Example:

```sql
SELECT column_name , column_name
FROM   table1 , table2
WHERE  column_name OPERATOR
   (SELECT column_name , column_name
   FROM table1 , table2 
   WHERE column_name OPERATOR value)
```

Real Life example:
```sql
-- This statement finds all teachers whose salaries are greater than the average salary of all teachers.
SELECT teacher_id, first_name, last_name, salary
FROM teachers
WHERE
salary > (SELECT AVG(salary) FROM teachers);
```

<br>


## Subqueries in the FROM clause

Example:

```sql
SELECT t.column_name , t.column_name
FROM   (SELECT t.column_name , t.column_name
   FROM table1 t)

   
```

Real Life example:
```sql
-- This statement retrieves all of the fields of the the teacher table with the use of a subquery in the FROM clause.
SELECT t.first_name, t.last_name FROM (SELECT t.first_name, t.last_name FROM teachers t);
```

<br>

## Practice 
Use Sub-Queries to do the following

1. Find the total number of sales each employee made
1. Find the average in sales for each employee
1. Return a list of sales where the sale price was lower than average
1. Return a list of sales, that includes the average sale price from the employee who made that sale.  The query should at mimimun return the employees name (first and last), the sale price of the car the the average sale price of the employee who made the sale.



## Additional Resources

- [Subquery Examples](https://www.youtube.com/watch?v=GpC0XyiJPEo)
- [Subquery Introduction](https://w3resource.com/PostgreSQL/postgresql-subqueries.php)
- [Posgresql Subquery](https://www.postgresqltutorial.com/postgresql-subquery/)
- [Subquery Examples](https://learnsql.com/blog/sql-subquery-examples/)
