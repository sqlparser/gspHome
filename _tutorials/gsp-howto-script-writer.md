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
	
{% include toc %}
	
### Scenarios that use the script rewrite technology

##### Check and modify SQL before executing by the DB

Before the SQL script fromt the client side to be executed by the database server, we may need to
check the SQL to see is there any unnessary columns had been selected in the result set,
or is there any important search conditions are missed in the where clause. Then, we can remove
the column in the select list and add additional search condition in the where clause by using 
this SQL script rewrite technology.

##### SQL run against different kinds of databases

How to keep your application unchanged after switch the backend database from one to another?  Such as switch from SQL Server to MySQL.
With this SQL script rewrite technoloy, we can dynaimcally generate the SQL script with the correct SQL syntax based on the backend database.

##### Migrate from one database vendor to another

One of the most important things to do when migrate from one database to another is to migrate the SQL and PL/SQL as well.
Using the GSP along with the script rewrite technology, you can scan all the SQL and PL/SQL to find out how many SQL is not compatible to
the new database platform that need to be modified, then use the script rewrite technology to rewrite some SQL and PL/SQL automatically,
Finally, you have to deal with some SQL and PL/SQL by hand that can't be rewrited automatically.


### Script rewrite detail

There are lots of types of parse tree node, such as statement node, clause node, expression node, literal node and more.
Usually, the parse tree node are created by the parser of GSP during the parsing process, those parse tree nodes then build up a 
parse tree which is a SQL statement node.

During the rewrite process, you may create parse node manually and then add it to the parse tree to add new SQL element to the original SQL script.

Since GSP already created the parse tree for you, then, how to create parse tree node manually is the first thing you need to know.

#### Basic parse tree nodes

Following are the most used parse tree node type which you will use during the script rewrite process.

- **`TSourceToken`**

	The input SQL script will be turned into a list of tokens by the lexer of GSP. Each token is represented by a `TSourceToken` object.

	Java code to create a new source token:
	```java
	TSourceToken st = new TSourceToken("AToken");
	```
	
	C# code to create a new source token:
	```csharp
	TSourceToken st = new TSourceToken("AToken");
	```

- **`TObjectName`**

	This class is used to represents various database object such as table, column, index and so on.

	Java code to create a new object name:
	```java
		// use new constructor to create an object name
		TObjectName tableName = new TObjectName(new TSourceToken("ATable"), EDbObjectType.table);
		assertTrue(tableName.toScript().equalsIgnoreCase("ATable"));

		TObjectName columnName = new TObjectName(new TSourceToken("ATable"),new TSourceToken("AColumn"), EDbObjectType.column);
		assertTrue(columnName.toScript().equalsIgnoreCase("ATable.AColumn"));

		// use parseObjectName() method to create a three parts object name
		TGSqlParser sqlParser= new TGSqlParser(EDbVendor.dbvmssql);
		columnName = sqlParser.parseObjectName("scott.emp.salary");
		assertTrue(columnName.toScript().equalsIgnoreCase("scott.emp.salary"));
	```
	
	C# code to create a new object name:
	```csharp
		// use new constructor to create an object name
		TObjectName tableName = new TObjectName(new TSourceToken("ATable"), EDbObjectType.table);
		Assert.IsTrue(tableName.ToScript().Equals("ATable", StringComparison.CurrentCultureIgnoreCase));

		TObjectName columnName = new TObjectName(new TSourceToken("ATable"), new TSourceToken("AColumn"), EDbObjectType.column);
		Assert.IsTrue(columnName.ToScript().Equals("ATable.AColumn", StringComparison.CurrentCultureIgnoreCase));

		// use parseObjectName() method to create a three parts object name
		TGSqlParser sqlParser = new TGSqlParser(EDbVendor.dbvmssql);
		columnName = sqlParser.parseObjectName("scott.emp.salary");
		Assert.IsTrue(columnName.ToScript().Equals("scott.emp.salary", StringComparison.CurrentCultureIgnoreCase));
	```

**Watch out!** There are 2 methods to generate SQL text from parse tree node: `toString()` and `toScript()`.
`toString()` is used when the parse tree node is created by the parser and was not modified manually.
`toScript()` is used when the parse tree node is created manually or the parse tree node was modified.
{: .notice--warning}
	
- `TConstant`
- `TFunctionCall`
- `TExpression`
- `TSelectSqlStatement`

