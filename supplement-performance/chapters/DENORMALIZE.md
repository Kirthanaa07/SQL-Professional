# Denormalization

Denormalization is a strategy used on a previously-normalized database to increase performance. 
In order to improve the read performance, we can denormalize the database. The disadvantage is that write performance will be impacted.

## Resources to Browse Before Class

- [Video: What is Database Denormalization in DBMS](https://www.youtube.com/watch?v=mVHrVj7IXmU)
- [Video: Database Normalization & Denormalization](https://www.youtube.com/watch?v=sGJgeO3kpzI)
- [Video: What is Denormalization?](https://www.youtube.com/watch?v=W8U21XIJqAc)
- [When and How You Should Denormalize a Relational Database](https://rubygarage.org/blog/database-denormalization-with-examples)
- [Difference Between Normalization and Denormalization](https://www.tutorialspoint.com/difference-between-normalization-and-denormalization)
- [Denormalization in Databases](https://www.geeksforgeeks.org/denormalization-in-databases/)

## Why Denormaliztion?

In a normalized database, we store data in separate logical tables and attempt to minimize redundant data. But if our data lives in separate tables, that means data retrieval usually has a lot of joins. And joins can be expensive, especially when the amount of data you have in the tables is large.

## When do we denormalize?

Usually denormalization is done after normalization. Meaning we try to make sure our database satisfies the normal forms and there is no redundancy first. Then, based on performance, we might denormalize certain parts of the database. This is where the many tools we have talked about in this book are useful. Are there any tables that from which we retrieve data at a high frequency? Are there any queries that are slow? Do we have tables that we mostly do a lot of read operations on and less write operations?

## Advantages & Disadvantages

Ideally we want to find a balance between normalization and denormalization. We want a data with lesser redundancies and consistent data. But we also want high performance. Because the biggest advantage of denormalization is the increase in performance. The disadvantage is that by denormalizing the database, we are allowing for some redundancy in the data and agreeing to lower performance for our write operations.


## Practice: Carnival

1. One of the main parts of our database that we normalized was Vehicles, Vehicle Body Types, Makes and Models. Create a new table for the denormalized data and import VehiclesTypes.csv. Use EXPLAIN to evaluate the performance costs of reads and writes for the normalized data and the denormalized data.

- How often do you think we will be performing reads and writes for this data?
- Is it worth denormalizing the data? If so, why?
