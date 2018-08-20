---
layout: page
title: "How to process commnets used in the SQL scripts"
excerpt: "Parsing of comments and accessing of the block and inline comments of a SQL script"
categories:
  - "How to"
---

Comments used in the SQL script clarify the purpose or effect of the SQL statements. It will be ignored by the database server during the execution.
Single line comments start with `--`. Multi-line comments start with `/* and end with */`. Some databases have their extension the ANSI/ISO standard,
Braces `( { } )` are the Informix extension to the ANSI/ISO standard. MySQL also start a line comment from a `#` character to the end of the line.

Oracle uses comments in a SQL statement to pass instructions, or hints, to the database.
	
	```
	{DELETE|INSERT|SELECT|UPDATE} /*+ hint [text] [hint[text]]... */
	or
	{DELETE|INSERT|SELECT|UPDATE} --+ hint [text] [hint[text]]...
	```

MySQL Server supports some variants of C-style comments. These enable you to write code that includes MySQL extensions, but is still portable, by using comments of the following form:

	```
	/*! MySQL-specific code */ 
	```
	
### SQL comment in GSP

After parsing the SQL script, single/Multi line comment is not included in the syntax tree like other SQL clauses which makes
it difficult to link the comment to a specific SQL clause. However, it's still possible to get some useful information 
by using the __TParseTreeNode.getLineNo()__ , __TParseTreeNode.getColumnNo()__, __TSourceToken.lineNo__,  __TSourceToken.columnNo__.

Comment inside SQL script is recoginzed as a source token(`TSourceToken`) by GSP with `tokentype` set to `ttsimplecomment` or `ttbracketedcomment`, 
so you can find comment inside a SQL statement by iterating the `TCustomSqlStatement.sourcetokenlist` or `TGSqlParser.getSourcetokenlist()` 
if you need to find comment in the whole SQL script.

Reference:
* Informix, https://www.ibm.com/support/knowledgecenter/en/SSGU8G_12.1.0/com.ibm.sqls.doc/ids_sqs_0210.htm
* MySQL, https://dev.mysql.com/doc/refman/8.0/en/comments.html

 
 