---
layout: page
title: "How to process commnets used in the SQL scripts"
categories:
  - "How to"
---

Comments used in the SQL script clarify the purpose or effect of the SQL statements. It will be ignored by the database server during the execution.
Single line comments start with --. Multi-line comments start with /* and end with */. Some databases have their extension the ANSI/ISO standard,
Braces ( { } ) are the Informix extension to the ANSI/ISO standard. MySQL also start a line comment from a # character to the end of the line.

Oracle uses comments in a SQL statement to pass instructions, or hints, to the database.
	
	```sql
	{DELETE|INSERT|SELECT|UPDATE} /*+ hint [text] [hint[text]]... */

	or

	{DELETE|INSERT|SELECT|UPDATE} --+ hint [text] [hint[text]]...
	```

MySQL Server supports some variants of C-style comments. These enable you to write code that includes MySQL extensions, but is still portable, by using comments of the following form:

	```sql
	/*! MySQL-specific code */ 
	```
	
### SQL comment in GSP

After parsing the SQL script, single/Multi line comment is not included in the syntax tree like other SQL clauses which makes
it difficult to link the comment to a specific SQL clause. However, it's still possible to get some useful information 
by using the __TParseTreeNode.getLineNo()__ and  __TParseTreeNode.getColumnNo()__, and __TSourceToken.lineNo__ and __TSourceToken.columnNo__

Reference:
* Informix, https://www.ibm.com/support/knowledgecenter/en/SSGU8G_12.1.0/com.ibm.sqls.doc/ids_sqs_0210.htm
* MySQL, https://dev.mysql.com/doc/refman/8.0/en/comments.html

 
 