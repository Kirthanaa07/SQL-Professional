## Additional Concepts in Data Structures
[PostgreSQL CRASH COURSE](https://www.youtube.com/watch?v=zw4s3Ey8ayo)
<br>
*first 22 min talk about CREATE and INSERT

## Advanced Table Creation
[Advance Options: How to create tables in PostgreSQL](https://blog.devart.com/create-table-in-postgresql.html)

## Advanced Database Creation
[Advanced Options for Create Database](https://www.postgresql.org/docs/current/sql-createdatabase.html)

## Advanced INSERTING
[Inserting from another Table](https://www.youtube.com/watch?v=PnFqsB5nb1U)


### DROP
The DROP command is used to remove an entity from the database structure.  Based on what's been covered thus far, DROP is used to remove a Database or Table.  Once you use the `DROP` command, that entity and all the data associated with it are removed.  

Example: 
```
DROP table students;
```
This will remove the table and all the data in the  table.  

[DROP Table Reference](https://www.tutorialspoint.com/postgresql/postgresql_drop_table.htm)

[DROP Database Reference](https://www.tutorialspoint.com/postgresql/postgresql_drop_database.htm)

### ALTER

The `ALTER` command is used to change the structure of a Table.  This can include:
- Add or remove a column
- Changing the datatype of a column
- Add or remove a constraint

Example:
```
ALTER TABLE Students ADD reading_level VARCHAR(12);
```
This will add a column named `reading_level` to the Students table.

More ways to alter a table can be found: 

[ More details on ALTER Table](https://www.tutorialspoint.com/postgresql/postgresql_alter_command.htm)

### CHECK Constraint

 The `CHECK` Constraint can be added to a column to make specific value requirements.  Some examples would be to check that a number is above zero (salary for example) or an end date is after a start date.  

 Example with the students table:

 ```SQL
 CREATE TABLE students (
	student_id serial PRIMARY KEY,
	first_name VARCHAR ( 50 )  NOT NULL,
	last_name VARCHAR ( 50 ) NOT NULL,
	email VARCHAR ( 255 ) UNIQUE NOT NULL,
    date_of_birth DATE CHECK (date_of_birth > '1900-01-01'),
	created_on TIMESTAMP NOT NULL,
    last_login TIMESTAMP CHECK last_login > created_on
);
```
In this example, an error will occur if the `date_of_birth` is before Jan 1, 1900 or the `last_login` is before the `created_on` value.  

What errors would occur from the below `INSERT` and how would you fix them?

```SQL
INSERT INTO students (first_name, last_name, email, date_of_birth, created_on, last_login) 
VALUES ('Ruby', 'Davis', 'r.davis@fake.com', '1899-08-07', '2021-05-06', '2020-10-23');
```
[More information on CHECK constraint](https://www.postgresqltutorial.com/postgresql-tutorial/postgresql-check-constraint/)
## Practice

Using the Products and Customer Orders ERD from the previous deep dive, do the following:

- Write and Execute CREATE TABLE statements for all the entities.  You may use the default "postgres" database that is installed with PostgreSQL or create a new database for practice problems.
    - Make sure all FKs are set appropriately.
- INSERT some data into the tables.
- Pick a table to CREATE a second version of and INSERT some data.  Take the data from this second table and INSERT it into the other table with a SQL statement.
    - How would you insert only part of the data?
- ALTER one or more tables
    - add and/or remove columns
    - change the datatype of a column
    - add and/or remove constraints on a column
- Add a `CHECK` Constraint to one or more columns.  INSERT some data into this new table and make sure it meets the criteria.

