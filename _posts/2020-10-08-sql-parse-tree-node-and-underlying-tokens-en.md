---
layout: page
title: "SQL parse tree node and underlying tokens"
excerpt: "A general review/summary of General SQL Parser: sql parser tree node and underlying tokens"
permalink: gsp-sql-parse-tree-node-and-underlying-tokens.html
categories:
  - get-started
  - sql-syntax
---

This document explains how to use the GSP library to parse an existing SQL script, then modify the SQL parse tree, and rebuild the whole SQL using **TParseTreeNode.toString()** method.

> If you build a SQL parse tree from the scratch(Not from the existing SQL), and then generate SQL text from this parse tree, then **TParseTreeNode.toScript()** is the better choice.

## 1. TParseTreeNode setString()
Change the text of a SQL clause or the whole SQL statement.

Take this SQL for example:

```sql
SELECT *
FROM scott.employee
WHERE e.job_id = 1
```

We like to change the condition in the where clause from `e.job_id = 1` to `e.salary > 1000`.

Below is the Java code illustrates how to achieve this.
```java
sqlparser.sqltext = "SELECT *\n" +
        "FROM scott.employee\n" +
        "WHERE e.job_id = 1";
		
sqlparser.parse();

TSelectSqlStatement select = (TSelectSqlStatement)sqlparser.sqlstatements.get(0);
TWhereClause whereClause = select.getWhereClause();

whereClause.getCondition().setString("e.salary > 1000");

System.out.println(select.toString());
```

After running the above Java code, the output is:
```sql
SELECT *
FROM scott.employee
WHERE e.salary > 1000
```



## 2. remove a node
### Call **setXXX()**  method from the parent node and pass **null** as input parameter, will remove the SQL clause from the parent node.

This Java code will remove where clause from the select statement.

```java
sqlparser.sqltext = "SELECT * FROM TABLE_X where a>1 order by a";
		
sqlparser.parse();

select.setWhereClause(null);

System.out.println(select.toString());
```

### Call **removeItem(int index)** of `TParseTreeNodeList` will remove an item from the node list.

This Java code will remove column `b` from the order by clause.
```java
sqlparser.sqltext = "SELECT * FROM TABLE_X order by a,b";
		
sqlparser.parse();

select.getOrderbyClause().getItems().removeItem(1);

System.out.println(select.toString());
```


## 3. update a node
Please node's **setString()** method.

```java
TGSqlParser parser = new TGSqlParser(EDbVendor.dbvoracle);
parser.sqltext = "SELECT A.COLUMN1, B.COLUMN2 from TABLE1 A, TABLE2 B where A.COLUMN1=B.COLUMN1";
parser.parse();
TSelectSqlStatement select = (TSelectSqlStatement)parser.sqlstatements.get(0);

select.getWhereClause.setString("where a>2");

System.out.println (select.toString());
```


## 4. add a new node
Call **setXXX()**  method from the parent node and pass the new node as a paremeter.
In order to add a new node, we must know the parent node of this new added node.

Take this SQL for example, `TCustomSqlStatement.getWhereClause()` returns null.
```sql
SELECT emp_id,salary+100 FROM emp
```
In order to add where clause for this SQL, below is the Java:

```java
//create a new node
TWhereClause whereClause = new TWhereClause();
whereClause.setString("where a>2");

//link this new created node in the SELECT statement
select.setWhereClause(whereClause);
```

Then, we will get the new SQL like this:
```sql
SELECT emp_id,salary+100 FROM emp where a>2
```

steps to add a new node:
- create a node, `new TParseTreeNode()`, then call `TParseTreeNode.setString()` to set the text of this node.
- call `setXXX(TParseTreeNode)` from the parent node, and pass the new created node as parameter.

## APIs available to modify the parse tree

- TParseTreeNode.setString(String sqlSegment), update the text of a node.
- TParseTreeNodeList.removeItem(int index), All decendant class of TParseTreeNodeList can use this method to remove a sub-node.
- TCustomSqlStatement.setOutputClause(TOutputClause outputClause)
- TCustomSqlStatement.setResultColumnList(TResultColumnList resultColumnList)
- TCustomSqlStatement.setReturningClause(TReturningClause returningClause)
- TCustomSqlStatement.setTargetTable(TTable targetTable)
- TCustomSqlStatement.setTopClause(TTopClause topClause)
- TCustomSqlStatement.setWhereClause(TWhereClause newWhereClause)
- TCustomSqlStatement.setWhereClause()
- TCustomSqlStatement.setWhereClause()
- all TSelectSqlStatement.setXXX() method.


## use visitor pattren to search and modify node
Since there are lots of nodes in a parse tree node, and you may only need to modify some specific node type.
So, use visitor to search and modify a specific type node is very convenient.

Please find how to search datatype, function, SQL statement and modify it here:
[Java demo](https://github.com/sqlparser/gsp_demo_java/tree/master/src/main/java/demos/visitors)

