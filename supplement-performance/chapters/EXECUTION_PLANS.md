# Execution Plans

There are some tools that come with Postgres that allow us to analyze how long it takes to execute a PostgreSQL statement.

## Resources to Browse Before Class

- [PostgreSQL: EXPLAIN Documentation](https://www.postgresql.org/docs/current/sql-explain.html)
- [How to identify slow queries in PostgreSQL](https://dev.to/pythonmeister/how-to-identify-slow-queries-in-postgresql-4igk)
- [Explaining Explain](https://wiki.postgresql.org/images/4/45/Explaining_EXPLAIN.pdf)
- [Explaining Explain](https://www.slideshare.net/xzilla/explaining-explain-227529779)
- [Understanding PostgreSQL Query Performance](https://pgdash.io/blog/understanding-postgres-query-performance.html)

## EXPLAIN

The EXPLAIN command can be run with any SQL statement. Behind the scenes, is your PostgreSQL planner, whose task is to create an optimal execution plan for a given query. The EXPLAIN command lets you view the execution plan picked by the PostgreSQL planner. It displays the tables that will be referenced, how your joins pull in the data, etc.

Along with displaying the tables that will be traversed, this command will also show the estimated execution cost, or how long the planner thinks it will take to run the SQL statement. Specifically, the command gives you the start-up cost before the first row can be returned and the total cost to return all the rows.

Because it just shows you the plan that will be followed if the SQL statement is executed, it will not do anything to your database. This means the statement is not actually executed and no changes to the database are made.

```sql
EXPLAIN SELECT
	d.business_name,
	et.name
FROM dealerships d
LEFT JOIN dealershipemployees de
	ON d.dealership_id = de.dealership_id
INNER JOIN employees e
	ON de.employee_id = e.employee_id
RIGHT JOIN employeetypes et
	ON e.employee_type_id = et.employee_type_id;
```


## EXPLAIN ANALYZE

ANALYZE is a parameter that you can specify with your EXPLAIN command. This will carry out the command and show the actual run times and other statistics. If this parameter is not provided, it defaults to FALSE.

```sql
EXPLAIN ANALYZE SELECT
	d.business_name,
	et.name
FROM dealerships d
LEFT JOIN dealershipemployees de
	ON d.dealership_id = de.dealership_id
INNER JOIN employees e
	ON de.employee_id = e.employee_id
RIGHT JOIN employeetypes et
	ON e.employee_type_id = et.employee_type_id;
```
