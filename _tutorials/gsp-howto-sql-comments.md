---
layout: page
title: "How to process commnets used in the SQL scripts"
categories:
  - "How to"
---

Comments used in the SQL script clarify the purpose or effect of the SQL statements. It will be ignored by the database server during the execution.

#### Single Line Comments

Single line comments start with --. 

Any text between -- and the end of the line will be ignored (will not be executed).


#### Multi-line Comments

Multi-line comments start with /* and end with */.

Any text between /* and */ will be ignored.


#### Database vendor extension to the ANSI/ISO standard

* Informix, Braces ( { } ) are the Informix extension to the ANSI/ISO standard.
* MySQL, From a # character to the end of the line.


#### Use comments in a SQL statement to pass instructions, or hints, to the database

* Oracle hint, 
```sql
{DELETE|INSERT|SELECT|UPDATE} /*+ hint [text] [hint[text]]... */

or

{DELETE|INSERT|SELECT|UPDATE} --+ hint [text] [hint[text]]...
```


* MySQL extension, 
```sql
/*! MySQL-specific code */ 
```


Reference:
* Informix, https://www.ibm.com/support/knowledgecenter/en/SSGU8G_12.1.0/com.ibm.sqls.doc/ids_sqs_0210.htm
* MySQL, https://dev.mysql.com/doc/refman/8.0/en/comments.html

 
 