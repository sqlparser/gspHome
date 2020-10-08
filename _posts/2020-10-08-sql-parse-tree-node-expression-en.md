---
layout: page
title: "SQL parse tree node and expression modification"
excerpt: "A general review/summary of General SQL Parser: sql parser tree node and expression modification"
permalink: gsp-sql-parse-tree-node-and-expression-modification.html
categories:
  - get-started
  - sql-syntax
---

How to modify and rebuild expression.

## 1. remove a sub-node of an Expression

After removing a sub-node of an expression, the whole expression maybe affected. Take this SQL for example:

```sql
d.cntrb_date1 >= '$From_Date$'
```
remove either d.cntrb_date1 or '$From_Date$', the whole expression will be removed as well.

According to the different kind of expression, the result will be different after removing a sub-node.

- Math expression: +,-,*,/ and other expression with two operands, after removing one operand, the other will be remain unchanged.
- Logical expression: and, or，  after removing one operand, the other will be remain unchanged.
- Comparison expression: <, > , after removing one operand, the whole expression will be remove.
- in, between, () expression:  after removing one operand, the whole expression will be remove.
- Other kind of expression:  after removing one operand, the whole expression will be remove.

After the removal of the sub-node, if the whole parent expression is removed as well, the processing will be executed recursively until the top-level expression.


###  1.1 API
Call TExpression.removeMe() to remove an expression itself.



### 1.2 using TParseTreeNodeList.removeItem(int index) to remove the sub-expression in the expression list

```sql
(1,2,3,4)
```

After calling
```java
expressionList.removeItem(0);
```

The result is:
```sql
(2,3,4)
```


## 2. Modify the expression

```sql
d.cntrb_date1 >= '$From_Date$'
```
After set '$From_Date$' to 1 , the expression will be 
```sql
d.cntrb_date1 >= 1
```

The java code to achieve this:
```java
expression.getRightOperand().setString("1");
assertTrue(expression.toString().equalsIgnoreCase("d.cntrb_date1 >= 1"));
```

## 3. Add a new expression

If we like to change
```sql
d.cntrb_date1 >= '$From_Date$'
```
to:
```sql
d.cntrb_date1 >= '$From_Date$' + 1
```


Here is the Java code:
```java
expression.getRightOperand().setString(expression.getRightOperand().toString()+" + 1");
assertTrue(expression.toString().equalsIgnoreCase("d.cntrb_date1 >= '$From_Date$' + 1"));
```



### Reference Java code
[testExpression](https://github.com/sqlparser/gsp_demo_java/blob/master/src/test/java/common/testExpression.java)

1. public void testRemove1()
2. public void testRemoveExprList()

[testModifyExpr](https://github.com/sqlparser/gsp_demo_java/blob/master/src/test/java/common/testModifyExpr.java)
[testModifySql](https://github.com/sqlparser/gsp_demo_java/blob/master/src/test/java/common/testModifySql.java)
