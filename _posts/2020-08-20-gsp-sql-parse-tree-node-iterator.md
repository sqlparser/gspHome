---
layout: post
title: "Iterator interface implmented in TParseTreeNode and Iterable interface implmented in TParseTreeNodeList"
categories:
  - gsp-api
---

Iterator interface implmented in TParseTreeNode is used to iterates the all source tokens of the parse tree node.

```java
public abstract class TParseTreeNode implements Visitable,Iterator<TSourceToken>
```

Iterable interface implmented in TParseTreeNodeList is used to iterates all the parse tree nodes included in this list.

```java
public class TParseTreeNodeList<T extends TParseTreeNode> extends TParseTreeNode implements Iterable<T> 
```

Iterable interface implmented in TStatementList is used to iterates the all the sql statements included in this list.
```java
public class TStatementList extends TParseTreeNode implements Iterable<TCustomSqlStatement> 
```

Let take this SQL for example:

```sql
SELECT e.employee_id,
       e.last_name,
       e.department_id
FROM   employees e,
       departments d
;

SELECT e.employee_id,
       e.last_name,
       e.department_id
FROM   employees e
       JOIN departments d
         ON e.department_id = d.department_id 
```

Print the type of all sql statements:
```java
for (TCustomSqlStatement sqlStatement:sqlparser.sqlstatements) {
	System.out.println(sqlStatement.sqlstatementtype);
}
```

Since TParseTreeNodeList is subclass of TParseTreeNode, so TParseTreeNodeList support both Iterable and Iterator interface.
Please aware that Iterator interface is used to get all source tokens belong to this node like this: 
```java
while(sqlStatement.tables.hasNext()){
	System.out.println(sqlStatement.tables.next().toString());
}
```

While Iterable interface is used to get parse tree node in the list:
```java
for(TTable table:sqlStatement.tables){
	System.out.println(table.getTableType());
}
```