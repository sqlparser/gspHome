---
layout: page
title: "SQL script rewrite using General SQL Parser"
categories:
  - "How to"
---

After successfully parse a SQL script, You can modify the Parse Tree Nodes (PTN) of the input SQL script
which is created by General SQL Parser(GSP) to generate the new SQL script as needed.

In order to achieve this, GSP does the folowing things for you:

- Parse SQL text and build the PTN tree.
- Provide a set of APIs used to manipulate the PTN.
- Provede the toScript() method to generate the new SQL text based on the modified PTN automatically.

What you need to do is:

- Use the APIs provided by the GSP to add/delete/modify the PTN as needed.
    Something like add a new search condition in where clause, remove a column in select list,
	add a new join table in from clause and etc.
	
### Typical use cases that use script rewrite technology

##### Check and modify SQL before executing by the DB

Before the SQL script fromt the client side to be executed by the database server, we may need to
check the SQL to see is there any unnessary columns had been selected in the result set,
or is there any important search conditions are missed in the where clause. Then, we can remove
the column in the select list and add additional search condition in the where clause by using 
this SQL script rewrite technoloy.

##### SQL run against different kinds of databases

How to keep your application unchanged after switch the backend database from one to another?  Such as switch from SQL Server to MySQL.
With this SQL script rewrite technoloy, we can dynaimcally generate the SQL script with the correct SQL syntax based on the backend database.