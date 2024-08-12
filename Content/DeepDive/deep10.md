### Using Variables in a Stored Procedure

Sometimes, in a stored procedure you need to have a variable to hold some information.  You can create a variable using `DECLARE` before the `BEGIN` portion in a Stored Procedure.  It would look something like:

```
CREATE OR REPLACE PROCEDURE GetMake(IN p_vehicleId INT, INOUT o_make TEXT)
LANGUAGE plpgsql
AS $$
DECLARE
   vehicleMake TEXT;
BEGIN 
  SELECT vt.make INTO vehicleMake
  FROM vehicles v
  JOIN vehicleTypes vt ON vt.vehicle_type_id = v.vehicle_type_id
  WHERE v.vehicle_id = p_vehicleId;

  IF vehicleMake IS NOT NULL THEN
    o_make := vehicleMake;
  END IF;

END $$;
```

In this procedure, it returns the make of a vehicle.  For example:

`CALL GetMake(3, 'no make');`

returns "Mazda" (unless you've updated vehicle_id 3).

If the vehicle is not found in the system or does not have a make, then it will return the string passed into the procedure.  For example:

`CALL GetMake(200021233, 'no make');`

returns "no make".

### IN, OUT, & INOUT

Stored Procedures and Functions take three types of parameters, `IN`, `OUT`, and `INOUT`. `IN` is the default and is a parameter that is used only in the code block of the stored procedure or function.  

`OUT` is the opposite of `IN`.  It is returned from the Stored Procedure of Function.

`INOUT` is a combination of `IN` and `OUT` which does both the IN and OUT processes.  An `INOUT` is needed to pass a variable in, change it and return the new variable. 

An example of using an `OUT`is below.  Notice that when calling the stored procedure, a value for the `OUT` must be passed in. This can be any `INT` or `NULL`.

```SQL
CREATE OR REPLACE PROCEDURE add_numbers (
	IN a int, 
	IN b int,
	OUT total int
	)
LANGUAGE plpgsql
AS $$
BEGIN 
	total := a + b;
END 
$$;

-- To call the stored procedure, you need a value for the `OUT`
CALL add_numbers(1, -7, NULL);

```

### Practice
1. Create a Stored Procedure that takes a vehicle_id and returns the model of the vehicle.
1. Create a Stored Procedure that takes a vehicle_id and returns the model of the vehicle or a string that was passed in as a parameter if the vehicle does not exist.

### Resources

[IN OUT INOUT](https://www.postgresqltutorial.com/postgresql-plpgsql/plpgsql-function-parameters/)

[Variables](https://www.geeksforgeeks.org/postgresql-variables/)
