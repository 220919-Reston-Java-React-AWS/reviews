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
