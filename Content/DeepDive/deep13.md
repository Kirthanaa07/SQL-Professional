# Mutable and Immutable Data

Immutable data is information that should never be updated.

Mutable data is the opposite. Information that is expected to change over time.

It is important to think about and discuss which information in your database will mutate over time and which should not. Relational databases are mutable by nature, which means that it is possible for any value to change, given that it doesn't violate any constraints that you have defined.

## Immutable Example

Imagine that you are designing a financial database that keeps track of customers and their bank accounts.

### Customer Table

|id|first_name|last_name|ssn|address|
|--|--|--|--|--|
|1|Mark|Williams|331-03-2019|100 Mulberry Way|
|2|Denise|McIntyre|501-30-1022|404 Main St|
|3|Jamal|Akton|177-35-5521|542 Cider Ave|
|4|Mikayla|Appleton|209-99-8711|58 Fiona Way|

Which of these fields are possible to change over time?

1. Last name
1. Address

Which of these fields will likely not change over time?

1. Social security number
1. First name

### Account Table

|id|acct_num|customer_id|date_opened|
|--|--|--|--|
|1|48578934590432|2|1998-05-04|
|2|94375848982882|1|2015-07-29|
|3|42582959194741|4|2004-11-12|
|4|49578594482784|3|2002-01-20|

Which of these fields are possible to change over time?

1. None

Which of these fields will likely not change over time?

1. All of them

What if the customer closes their account to create another one? Should you simply update the existing record with the new account number and date? Absolutely not, because all of their past transactions on the original account are no longer tied to a unique record in the Account table.

## Practice

- Pick some Carnival tables.  Which data points are Mutable and which are Immutable?

# Constraints

In PostgreSQL, constraints are used to define rules that the data in tables must follow. Here are the main types of constraints you can use:

**Check Constraints** These constraints ensure that a specific condition is true for data in a column. For example, you can use a check constraint to ensure that a numeric value is positive.

**Not-Null Constraints** This constraint specifies that a column cannot have null values, ensuring that data is always entered into that column.

**Unique Constraints** They make sure that data in a column, or a group of columns, is unique across all the rows in a table. This is helpful for maintaining the uniqueness of data like product IDs or email addresses.

**Primary Key Constraints** A primary key is a unique identifier for rows in the table. It's a combination of a unique constraint and a not-null constraint. A table can have only one primary key.

**Foreign Key Constraints** These establish a relationship between two tables. A foreign key in one table points to a primary key in another, ensuring referential integrity.

**Exclusion Constraints** These constraints ensure that if any two rows are compared on specified columns or expressions using specified operators, at least one of these comparisons will return false or null.

Implementing these constraints helps maintain data integrity and consistency in your PostgreSQL databases. For more detailed information, you can visit the PostgreSQL documentation on constraints here.