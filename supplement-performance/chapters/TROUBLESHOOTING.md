# Troubleshooting

Most of you are familiar with the term troubleshooting. It essentially means to idenitifying a problem, learning more about what may be causing the problem and eventually coming with a plan that will resolve the problem. When it comes to databases, usually you are troubleshooting scalability and performance related issues. Database troubleshooting is a very broad topic but we are hoping to introduce the concept to you so that you can continue to look into further on your own.

## Resources to Browse Before Class

- [Top 5 Ways To Improve Your Database Performance](https://www.eversql.com/5-easy-ways-to-improve-your-database-performance/#:~:text=If%20you're%20having%20trouble,possible%20solution%20is%20data%20defragmentation.&text=The%20defragmentation%20of%20the%20disk,overall%20query%20and%20database%20performance.)
- [Top 5 Causes of Poor Performance](https://learn.percona.com/hubfs/Collateral/Solution_Briefs/Solution_Top_5_Causes_Poor_Performance.pdf)
- [Steps to Troubleshooting SQL Server](https://www.databasejournal.com/features/mssql/article.php/3899851/Nine-Steps-to-Troubleshooting-SQL-Server-problems.htm)
- [Troubleshooting SQL Server](https://www.red-gate.com/library/troubleshooting-sql-server-a-guide-for-accidental-dbas)
- [3 WAYS TO DETECT SLOW QUERIES IN POSTGRESQL](https://www.cybertec-postgresql.com/en/3-ways-to-detect-slow-queries-in-postgresql/#:~:text=A%20more%20traditional%20way%20to,and%20know%20where%20to%20look.)
- [Postgresql Wiki: Slow Query Questions](https://wiki.postgresql.org/wiki/Slow_Query_Questions)
- [PostgreSQL Performance Identifying Hot and Slow Queries](https://www.virtual-dba.com/postgresql-performance-identifying-hot-and-slow-queries/)
- [A DBA guide to SQL Server performance troubleshooting](https://www.sqlshack.com/dba-guide-sql-server-performance-troubleshooting-part-1-problems-performance-metrics/)

## Monitoring

Monitoring the performance of your database is the best way to identify if there are issues that we need to troubleshoot. There are a few tools that come with PostgreSQL for this purpose.

## Database Design

Database normalization is the process of making sure the database adheres to the normal forms. In certain situations, denormalizing a database will actually speed up the performance of the database. Part of the database design process is trying to find a balance between normalizing the database and providing high performance.

## Query Optimization

The process of identifying the queries and/or stored procedures that are slow and refactoring those queries to enhance performance.

## Indexing

By indexing the data that is most often retrieved, we can speed up the data retrieval process, making our database more efficient.
