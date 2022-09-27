# Week 2 Review

# SQL

## Intro to SQL
- Database: A tool that allows us to input, manage, organize, store, and retrieve data
    - Traditionally databases are organized into tables in the form of rows and columns
    - The goal of any database is to persist information
- SQL (Structured Query Language)
    - SQL is a standard for how to construct a RDBMS (Relational Database Management System)
        - RDBMS: A system for creating relational databases and interacting with them
            - RDBMS provide and maintain security, accuracy, integrity, and consistency of data
        - Relational database: databases that are used to store information where tables will have connections/references/relationships with each other
- SQL Dialects
    - SQL is a language standard, but not a direct implementation of a particular language
    - Dialects are actual implementations of the SQL standard
    - Each dialect has slightly different syntax, keywords, conventions, etc. based on its own implementation
    - Examples
        - PostgreSQL
        - Firebird
        - IBM Db2
        - MS SQL
        - MySQL
        - MariaDB
        - etc.
    - We are using Postgres becuase it is powerful, convenient, and FREE

## SQL Sublanguages
- Data Definition Language
    - Defines the overall structures and is concerned with the creation, alteration, and deletion of structures
        - Structures include: The database itself, tables, schemas, etc.
        - Schemas: term has two slightly different meanings depending on context
            - Conceptual context: A description of the structures that make up the database
            - DDL context: a subdivision of a database that collects tables into the same "area" of the database
                - Analogous to Java packages containing Classes
    - DDL Commands
        - CREATE: This is used to create a table or other database structures
        - ALTER: Changes an existing database structure such as adding a clumn to a table
        - DROP: Removes a database structure
        - TRUNCATE: Removes all data from a structure, generally a table, but leaves the structure itself
- Data Manipulation Language (DML)
    - This is about handling data inside the tables
    - These are often referred to as SQL's CRUD functionalities
        - CRUD: Create, Read, Update, Delete
    - DML Commands
        - INSERT: adds a new record to a table
        - SELECT: reads information from a table without changing it (used for data retrieval, often known as "queries")
        - UPDATE: changes the value of data already present in the database
        - DELETE: removes a row/record or multiple rows/records at once, possible to use DELETE to achieve same functionality as TRUNCATE, but not recommended
- Data Query Language (DQL)
    - This is a highly debated sublanguage
    - Some schools of thought say that DQL is a separate sublanguage from DML
    - Others say it doesn't exist
    - Or some classify it as a sub-sublanguage
    - Command: SELECT (see SELECT in DML above)
- Data Control Language (DCL)
    - Security functionality for who and what can access your data with what permissions. It usually revolves around users, granting users access to just querying (read-only access), while others can use all DML statements but no DDL, etc.
    - Commands: GRANT, REVOKE
- Transaction Control Language (TCL)
    - Represents control over the functionality for transactions. A transaction is a group of DML commands that need to either all run or all fail together
    - Commands:
        - COMMIT: will end a transaction after ensuring all changes can be made successfully
        - SAVEPOINT: sets the state of the database we will return to if a following command should fail. When we START or BEGIN a transaction, the savepoint is automatically set
        - ROLLBACK: aborts transaction returning to a savepoint
        - START/BEGIN: dialect dependent. Indicates the following commands are part of a transaction and sets the initial SAVEPOINT

## Postgres Datatypes
- Datatypes are consistent between SQL dialects
- Most dialects will have datatypes that hold similar values, but might be named DIFFERENTLY
- Datatypes are constraints placed on a column
- Postgres Common Datatypes
    - BOOLEAN: allowed to be null/empty as well as true/false
    - VARCHAR(x): Variable number of characters like Strings in Java. X is the maximum number of characters allowed
    - INTEGER: Whole number integer values
    - NUMERIC(x, y): Floating point numbers, "x" is the precision which represents the number of digits allowed. "y" is the scale which represent how many of those digits come after the decimal
    - DATE: Calendar Date
    - TIMESTAMP: Price moment in time

## SQL Constraints
- Constraints are rules or conditions that enforce consistency on the values of a column. They also can be used to define relationships between tables. They can be attached to a single column or multiple columns
- Examples:
    - UNIQUE: no duplicate values in the column
        - NULLS are not counted
    - NOT NULL: a column that cannot have a NULL value. When inserting a new record, the column must be filled or the INSERT statement will fail
    - CHECK: this allows for a logical check that can be defined to further constrain the column. You can CHECK a column is never less than 0, to ensure no negative values, for example
    - PRIMARY KEY (PK): Combines the UNIQUE and NOT NULL to ensure this value is unique to each record in the table and thus every record can be individually accessed/referenced in that table
        - The PK is used to serve as a unique identifier for a record
    - FOREIGN KEY (FK): Indicates a column in one table references a value in another table. This is how relationships are created between tables
        - Postgres uses REFERENCES to establish FKs

## Cardinality/Multiplicity
- 3 types of multiplicity
    - 1:1 (one to one)
        - An individual record in one table is associated with a single record in another table
        - UNIQUE FK column
        - The FK can be on either table
    - 1:n (one to many) / n:1 (many to one)
        - An individual record in one table can be referenced by multiple records in another table
        - Achieved by having a FK column that is not-unique in the "many" table
        - ex. User table, Reimbursements table
            - A user can have many reimbursements
            - Reimbursement table will have a FK column to refer to the user each reimbursement belongs to
    - n:n (many to many)
        - An individual record may be associated with many records in another table, and records in that table may be associated with many records in the first table
        - The use of a third table, called a junction table, can be used to establish the many to many relationship

## SQL Joins
- When creating a query (SELECT statement), you can combine multiple tables based on a logical relationship between columns. The majority of the time it is a FK to PK relationship
- Joins create a temporary table that displays information requested across tables
- Join Types
    - INNER JOIN: selects records to display only if there is matching data from both tables
    - LEFT JOIN: The first table will display all records and any matching data from the right table will be displayed. IF a record has no relation from the left table, the right table will appear as null
    - RIGHT JOIN: Same as left but reverses the tables
    - OUTER JOIN (FULL): Shows all records from both tables, combining where there is a relationship
    - SELF JOINs: a table can be joined with itself. Ex. employees table may have a FK to the employee's boss id

## SQL Subqueries
- Subqueries are queries made inside other queries. Since a SELECT statement returns a temporary table, you can then run an additional query on the returned temporary table
- In order to avoid ambiguity in these types of situations, "aliases" are often used
    - Alias: a temporary name assigned to a table to easily identify the table (uses the AS keyword)

## SQL Set Operations
- These are ways to manipulate the temporary tables returned by a query statement
- They do not make changes to the underlying data
- Commands
    - ORDER BY: sorts the returned records based on the values in a column or columns
        - ASC (ascending) or DESC (descending) are built in functionalities to determine the order in which the data is presented
    - GROUP BY: take data in the table and group the values that are having an aggregate function performed on them; the function then returns for that group or that subsection of the table instead of the whole table
        - HAVING: is used with GROUP BY to determine the condition that defines the groups
    - UNION: will stack tables together. Will match tables with the same number of columns into a single table, putting records from both into that single table

## SQL Scalar and Aggregate Functions
- Pre-built functions in an SQL dialect. All SQL dialects will have at least some of these built in
- Some dialects will have the ability to create custom functions in a programmatic expansion to SQL (Postgres has PLpg/SQL), which are different than the functions we are talking about
- Scalar Functions
    - These are functions that act on each record in a table and return a value for them individually
    - Thus, we can say they return a value for each record
    - Examples
        - UPPER(): makes VARCHAR all uppercase
        - LOWER(): makes VARCHAR all lowercase
        - FLOOR(): makes a floating number into a whole number by rounding down
        - CEIL(): makes a floating number into a whole number by rounding up
        - ROUND(): rounds a floating number to the nearest integer
- Aggregate Functions
    - These take multiple records and return a single value. These include lots of mathematical functions
        - SUM()
        - AVG()
        - MIN()
        - MAX()
        - COUNT()