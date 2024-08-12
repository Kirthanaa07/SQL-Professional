## Functions

In POSTGRESQL, functions are very similar to Stored Procedures.  Both are a set of instructions for executing logic on a database.  Functions are unique in that they can be called from within a query.  

Here are some other differences between Stored Procedures and Functions

**Return Value**

>  <u>Functions</u> Must return a value. Functions in PostgreSQL are designed to return either a single value (scalar) or a set of rows.

> <u>Stored Procedures</u> Do not return a value. Instead, they are used to perform actions such as modifying database tables, invoking other procedures, etc.

**Usage in SQL Statements**

> <u>Functions</u> Can be used in a SELECT statement or other SQL statements anywhere an expression is allowed. This is because they return a value.

> <u>Stored Procedures</u> Cannot be used directly in SQL statements like SELECT. They are invoked using the CALL statement.

**Transaction Control**

> <u>Functions</u> Cannot execute transaction control statements like COMMIT or ROLLBACK. Functions are assumed to be part of the transaction that calls them.

> <u>Stored Procedures</u> Can execute transaction control statements. They can start and commit/rollback their transactions.
Language:

> </u>Functions and Stored Procedures</u> Both can be written in various languages, including SQL, PL/pgSQL (PostgreSQL’s procedural language), C, Python, etc.

**Parameter Modes**

> <u>Functions</u> Primarily support input parameters.

> <u>Stored Procedures</u> Support input (IN), output (OUT), and input/output (INOUT) parameters, offering more flexibility for returning values.

**VOLATILE, STABLE, and IMMUTABLE properties**

> <u>Functions</u> Can be defined with these properties to indicate how often they return different results when called with the same arguments.

> <u>Stored Procedures</u> Do not have these properties since they do not return a value directly.

**Performance Considerations**

> <u>Functions</u> Often used for computational tasks and can be optimized by the planner for better performance.

> <u>Stored Procedures</u> More suitable for complex business logic involving multiple operations or transactions.

**Trigger Usage**

> <u>Functions</u> Can be called from database triggers.

> <u>Stored Procedures</u> Generally, not used with triggers.

**Invocation Syntax**

> <u>Functions</u> Invoked as part of an expression, like SELECT my_function(arg1, arg2);

> <u>Stored Procedures</u> Invoked using the CALL statement, like CALL my_procedure(arg1, arg2);

**Use Cases**

> <u>Functions</u> Ideal for calculations, data format conversions, and other operations that return a value.

> <u>Stored Procedures</u> Better suited for operations that require multiple steps, error handling, transaction management, or procedural logic.

### Example

Create a function that returns a 10% increase on the msr_price of a vehicle.

```
CREATE OR REPLACE FUNCTION get_price_with_increase(p_vehicle_id INT)
RETURNS NUMERIC AS $$
DECLARE
    vehiclePrice NUMERIC;
BEGIN
    -- Query to get the price of the vehicle
    SELECT msr_price INTO vehiclePrice
    FROM vehicles
    WHERE vehicle_id = p_vehicle_id;

    -- Check if the vehicle exists and price is not null
    IF vehiclePrice IS NULL THEN
        RAISE EXCEPTION 'Vehicle not found or price is not set';
    END IF;

    -- Return the price increased by 10%
    RETURN vehiclePrice * 1.10;
END;
$$ LANGUAGE plpgsql;
```

Using the function:
- To return the single value using a vehicle_id

    - `SELECT get_price_with_increase(1)`
- As part of a query to return multiple vehicles with the increased price
    ```SQL
    SELECT 
        get_price_with_increase(vehicle_id) AS "Increased 10%",
        msr_price ,
        vehicle_id
    FROM vehicles ;
    ```
## Practice

Carnival has switched to a static 10% commission on each sale and wants to have a way in the database to calculate the commission for:

- each sale
- each employee
- each employee for each month  

Create Functions, queries and/or stored procedures that accomplish this.


## Resources
[Create Function](https://www.postgresqltutorial.com/postgresql-plpgsql/postgresql-create-function/)

[Functions Vs. Stored Procedures](https://www.commandprompt.com/education/procedures-vs-functions-in-postgresql/)