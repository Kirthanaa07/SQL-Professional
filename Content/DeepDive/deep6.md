## IN and NOT IN

Sometimes theres a query in which you need to filter by a list of something that does not have an obvious filter in the database.  For example you would like to find all vehicles that have a red tone exterior.  

First you run a query to get all the exterior colors in the inventory, `SELECT DISTINCT exterior_color FROM vehicles`.  Then you choose Red, Crimson, and Maroon as matches for red tone. You could then query the database for vehilces of just those colors. 

```sql
SELECT vin, exterior_color, interior_color, floor_price, msr_price, miles_count, year_of_car
FROM vehicles v 
WHERE exterior_color IN ('Red', 'Crimson', 'Maroon');
```

Looking at the results, we may wan to eliminate cars that have orange or blue toned interiors.  That would look something like:

```sql
SELECT vin, exterior_color, interior_color, floor_price, msr_price, miles_count, year_of_car
FROM vehicles v 
WHERE exterior_color IN ('Red', 'Crimson', 'Maroon') AND interior_color NOT IN ('Fuscia', 'Aquamarine', 'Orange', 'Turquoise', 'Violet', 'Indigo', 'Teal', 'Purple', 'Blue');
```

### Practice IN and NOT IN

1.  Finance is doing some regional audits.  Since the database doesn't store any region data, they let you know that the norther midwest region is all dealerships in Wisconsin and Minnesota.  They want a report that contains the invoice number, payment method, and tax Id of each sale.

1. Write a query to get the total in sales from all dealerships except those located in California.  

##  EXISTS and NOT EXISTS

These operators work with sub-queries to test for whether the data you are looking for exists or does not exist.  For example, we can find all customers that have never made a purchase by:

```sql
SELECT c.customer_id
FROM customers c
WHERE NOT EXISTS (
    SELECT customer_id
    FROM sales s 
    WHERE c.customer_id = s.customer_id
)
```

and all those that have made a purchase by:

```sql
SELECT c.customer_id
FROM customers c
WHERE EXISTS (
    SELECT customer_id
    FROM sales s 
    WHERE c.customer_id = s.customer_id
)
```

### Practice EXISTS and NOT EXISTS

1. Find all the employees whom have never made a sale.
1. Find all the employees whom have made at lease 1 sale.

## ANY 

The `ANY` operator compares the data set to that returned by a subquery.  For example, it can by used to return the employee that had the most expensive sale by:

```sql
SELECT e.employee_id, e.first_name, e.last_name, s.price, s.dealership_id
FROM employees e 
JOIN sales s ON s.employee_id = e.employee_id
WHERE s.price = ANY (
    SELECT Max(price) 
    FROM sales s2 
    WHERE s2.dealership_id = s.dealership_id
    GROUP BY dealership_id
)
ORDER BY s.dealership_id
```

### Practice ANY

1.  Find the customer who purchased the most expensive vehicle at each dealership


## ALL

ALL filters a query based on a data set returned by a subquery.  For example, we can find all the sales above average by dealership with: 

```sql
SELECT e.employee_id, e.first_name, e.last_name, s.price, s.dealership_id
FROM employees e 
JOIN sales s ON s.employee_id = e.employee_id
WHERE s.price >= ALL (
    SELECT AVG(price) 
    FROM sales s2 
    WHERE s2.dealership_id = s.dealership_id
    GROUP BY dealership_id
)
ORDER BY s.dealership_id, s.price
```

### Practice ALL 

1. Find the customers who purchased the vehicles above average for that dealership


## Resources
- [Subqueries with Operators](https://www.sqltutorial.org/sql-subquery/)
- [Subquery Uses](https://www.dataquest.io/blog/sql-subqueries-for-beginners/)
- [WHERE IN Explained](https://blog.enterprisedna.co/sql-where-in-explained-with-examples/)
- [PostgreSQL Exists](https://www.postgresqltutorial.com/postgresql-tutorial/postgresql-exists/)
- [PostrgeSQL ANY](https://www.geeksforgeeks.org/postgresql-any-operator/})
- [PostrgeSQL ALL](https://www.geeksforgeeks.org/postgresql-all-operator/})
