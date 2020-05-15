---
layout: page
title: "Overview of General SQL Parser"
excerpt: "A general review/summary of General SQL Parser"
permalink: gsp-overview.html
---

{% include toc %}

### Introduce

General SQL Parser(GSP) is a Java/.NET library, adding powerful SQL processing
capability to your own program instantly.

The basic but important feature is validating the SQL syntax OFFLINE which
means no database connection is needed. After checking the SQL syntax, the SQL 
query will be decoded into parse tree nodes that organized in a hierarchical 
structure and represented by the Java/C# class.

In order to take advantage of the features provided by the GSP, 
The first thing you need to know is the name of various parse tree nodes 
which usually map to the element of a SQL query such as select list, 
from clause, where clause and etc. 
(SQL element means parts of a SQL query text, while parse tree node means the 
related Java/C# class. This two terms usually means same thing and will be used accordingly)

Once you know the name of a SQL element, the second thing is searching this SQL
element in the parse tree. Or iterating all elements.

After finding the SQL element, you may manipulating the element based on your 
requirement and then rebuild the SQL from from the parse tree.

Combining the above three steps, the magic things begin.
you can do lots of things such as format a mess SQL code, analyze column lineage
among sql scripts, modify the where condition only the fly before excution, 
avoid SQL Injection by checking the SQL before execution, find out tables
have Create, Read, Update, Delete and Insert operations against them, translate
SQL dialect between different databases, and etc.


#### Get familiar with the SQL elements and the corresponding Java/C# class
GSP includes hundreds of classes that used to represent the various SQL elements, 
for example, `TSelectSqlStatement` represents SELECT statement, `TWhereClause`
represents where clause, `TCreateProcedureStmt` represents the stored procedures.

The *API Reference* includes all the classes with the detailed explanation.

There is a *little utility* that can you feed the SQL query and generate corresponding
classes which is quite helpful when you need to know the related class of a 
specific SQL element.


#### Iterate the parse tree and find the required SQL element
There are two ways you can find the SQL element by iterating the parse tree. 

1. Start from a class that represents a SQL statement such as `TSelectSqlStatement`,
then checking every property of this class that reprsent a SQL element,   
and checking property of this SQL element class recursively till to a leaf element
such as a column name represented by `TObjectName`.

2. Use visitor pattern to iterate the parse tree automatically.
If you are only interested in some type parse tree nodes, for example, you only 
want to find out all built-in functions used in the SQL query. You can create a
visitor that only implement the method to handle the node with type of `TFunctionCall`. 
and then pass the visitor to the `accept()` method of the root node of the parse tree.


#### Modify the parse tree and rebuild the SQL query
You can add node to the parse tree, modify node in the parse tree, delete
node from the parse tree as well. After the change of the parse tree, a new
SQL query can be generated automatically by caling the `toScript()` method
of the root node.


The things GSP can do for you can be divided into two categories, one is gathering 
the necessary information from the parse tree, for example, get know which table is 
inserted and which table is updated. The second is manipulating the parse tree after
finding the target SQL element and rebuild the SQL query.

##### Gathering the information
- Offline SQL syntax check. Validates SQL syntax without connecting to a database.
- Extract table column from SQL.
  Scan, analyze SQL scripts and stored procedures to find relationship between 
  table and column in various clauses like where, join condition and etc.
- Data lineage and impact analysis  
- Anti SQL injection
- Fully output of the SQL syntax tree in XML
 
##### Manipulating the SQL query
- SQL rewrite technology
- SQL converter among the major database vendors
- SQL formatter. Produce clean SQL layout to improve SQL readability.

#### Highlists of the library
1. supports the most syntax of SQL dialect of more than 20 major database vendors
2. SQL from different database represented in a uinform structure
3. This library is build from the groud up, no third party library is used.
4. Including a powerful column-level lineage tool.


### Not a programmer, but need to get the job done?
