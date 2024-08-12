## Additional Practice
1. Find the average in sales for employee number 614
  - Bonus: Add the employee's first and last name to the above query
1. Find the First vehicle sold by Carnival.
  - Bonus: Add the make and model of the vehicle
    
## HAVING

`HAVING` is used to filter on a group or aggregate.  [More information on Having](https://www.postgresqltutorial.com/postgresql-tutorial/postgresql-having/)

For example
```SQL
SELECT SUM(msr_price) , vehicle_type_id
FROM vehicles
GROUP BY vehicle_type_id
HAVING SUM(msr_price) > 7000000
ORDER BY SUM(msr_price) 
```

### Practice Problems

1. Find the vehicle types that have an average msr_price between $17,300 and $17,800.
1. Find the Average miles on cars by each year they were made.  List the Average miles and the year for years where the average is under 200.
    - BONUS: ROund to 2 decimal places.

## Math Functions

[Math Functions with Examples](https://www.postgresqltutorial.com/postgresql-math-functions/)

Review the above example and try it out.  For example, you can find the Absolute Value of -12 by: `SELECT ABS(-12)`.

1. Find the cube root of 8.
1. Find the Ceiling value of 1.02.
1. Convert pi radians to degrees without using any numbers in your query.
1. Divide 8 by 2.  
1. Round 101.146794834 to 5 decimal places
1. Return a random integer from 0 to 100.  
1. Return a random integer from 0 to 99.




