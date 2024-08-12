## Case Statements

Sometimes in SQL, a conditional (IF/ELSE) is needed to return some data.  To do this, a `CASE` statement is used.  

An example, we can return whether a vehicle is expensive based on some logic where the price is > $30,000 with 

```sql
SELECT 
     vehicle_id,
     floor_price,
     CASE 
          WHEN floor_price > 30000 THEN 'Expensive'
          ELSE 'Cheap' 
     END AS "Is Expensive?"
FROM vehicles
```

## Practice

1. Return a list of cars and indicate if the interior color matches the exterior
1. Return a list of vehicles and what region they are in.  If the vehicle is not in a region, the return "No Region".  The regions are defined as follows:
    - SouthEast Region: Florida, Louisiana, West Virginia, Alabama
    - Upper MidWest: Iowa, Wisconson, Minnesota
    - New England: New York, New Jersey, Massachusetts
    - MidWest: Indiana, Ohio, Michigan, Illinois
    - West: California, Nevada


## Additional Resources




[POSTGRES CASE](https://www.postgresqltutorial.com/postgresql-tutorial/postgresql-case/)