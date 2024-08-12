# Indexes

## Resources to browse before class

- [SQL Indexes](https://www.youtube.com/watch?v=fsG1XaZEa78)
- [Understanding Indexes](https://www.youtube.com/watch?v=8oBKA4hU4xM)
- [PosgreSQL Indexes](http://postgresguide.com/performance/indexes.html)

<br>

## Why Indexes?
Indexes are how we optimize our database. We use them to make retrieving data faster and efficient. Imagine a table with 2 million student records. If we were to query all students with the last name, "Cooper" in the Students table we would initiate a retrieval of all those students records. The problem begins in the time it takes to search for the records with "Cooper". The database will search all 2 million records until it finds all occurrences of "Cooper". This is time consuming and can be resource intensive. 

Enter, Indexes! Indexes improve the time it takes to find records. Instead of looking through ALL records, indexes allow us to search much like with indexes in the back of a book. Book indexes tend to be alphabetized making it easier for the search process. The same is true with creating an index in SQL. The data is sorted making it easier to find, it now only needs to look for records that start with "C" or "Co" or "Coo" and the search is narrowed down thus making it faster. This is all happening behind the scenes and is not usually visible to the user.

Indexes typically make siginificant improvements on larger databases where large datasets can take longer to query.

## Creating an index
Creating an index is done using the `CREATE INDEX` statement. We will want to specify a meaningful name for our index, usually including the field name(s) we are applying the index to.

Naming example:
```idx_field_name```

We will then need to define the table on which the index resides as well as the actual column name(s) that the index should save. It's important to note, that the order in which you place these fields will modify how the search actually occurs. (i.e. If you have *last_name* and *first_name* fields, the search will filter with the *last_name* first and then filter again using the *first_name* second.)

Creating an index Example:
```sql
CREATE INDEX index_name ON table_name [USING method]
(
    column_name [ASC | DESC] [NULLS {FIRST | LAST }],
    ...
);
```

## Practice: Database Performance

Let's take a look at how some of our queries perform? Take notes of how each query performs. Then create indexes for each query below. Rerun your queries to see if they improve. If they do not improve, why?

1)
```sql 
    SELECT * from Employees WHERE employee_type_id = 1
```
2)
```sql 
    SELECT * from Sales WHERE dealership_id = 500;
```
3)
```sql 
    SELECT * from customers WHERE state = 'CA';
```
4)
```sql 
    SELECT * from vehicles where year_of_car BETWEEN 2018 AND 2020;
```
5)
```sql 
    SELECT * from vehicles where floor_price < 30000;
```
