---
layout: page
title: "SQL parse tree node and expression modification"
excerpt: "A general review/summary of General SQL Parser: sql parser tree node and expression modification"
permalink: gsp-sql-parse-tree-node-and-expression-modification-cn.html
categories:
  - get-started-cn
  - sql-syntax
---

表达式的修改及结果。

### 一、 删除表达式的子节点

删除表达式后，可能会对这个表达式所在的整个表达式产生影响，例如：

```sql
d.cntrb_date1 >= '$From_Date$'
```
以上比较表达式，删除 d.cntrb_date1 或 '$From_Date$' 中的任意一个, 整个表达式也被删除。

根据表达式和其所在表达式的情况不同，处理的方式也不同，以下为主要情况

- 数学表达式: +,-,*,/ 和其他含有两个 operand 的数学表达式，删除其中一个 operand 后， 还会留下另外一个。
- 逻辑表达式: and, or，  删除其中一个 operand 后， 还会留下另外一个。
- 比较表达式: <, > 等， 删除其中一个 operand 后， 整个表达式也被删除。
- in, between, () 表达式， 删除其中一个 operand 后， 整个表达式也被删除。
- 其它表达式， 删除其中一个 operand 后， 整个表达式也被删除。

删除一个表达式后，如果导致父表达式也被删除，会递归处理更高级别的表达式，直到最高层的表达式。

####  1. API
TExpression.removeMe()


#### 2. 相关属性的变化
如果一个节点被删除， 那么该节点的属性：
1. getNodeStatus() 为 ENodeStatus.nsRemoved
2. getStartToken(), getEndToken() 返回 null
3. toString(), 返回 null
4. expression.getExpressionType() == EExpressionType.removed_t

判断一个节点是否被删除， 用 getNodeStatus() == ENodeStatus.nsRemoved

如果一个表达式的 left operann and right operand 都被删除， 那么该表达式的状态也处于被删除。
以上属性同样满足。

#### 3. 利用 TParseTreeNodeList.removeItem(int index) 来移除 expression list 中的 expresssion

```sql
(1,2,3,4)
```

调用
```java
expressionList.removeItem(0);
```
结果为：
```sql
(2,3,4)
```


### 二、更改表达式
```sql
d.cntrb_date1 >= '$From_Date$'
```
After set '$From_Date$' to 1 , the expression will be 
```sql
d.cntrb_date1 >= 1
```

通过以下代码实现上面的更改功能：
```java
expression.getRightOperand().setString("1");
assertTrue(expression.toString().equalsIgnoreCase("d.cntrb_date1 >= 1"));
```

### 三、增加表达式
增加表达式一般通过修改原有表达式来实现，例如：
```sql
d.cntrb_date1 >= '$From_Date$'
```
想变为：
```sql
d.cntrb_date1 >= '$From_Date$' + 1
```


通过以下代码实现上面的更改功能：
```java
expression.getRightOperand().setString(expression.getRightOperand().toString()+" + 1");
assertTrue(expression.toString().equalsIgnoreCase("d.cntrb_date1 >= '$From_Date$' + 1"));
```



### 参考代码
[testExpression](https://github.com/sqlparser/gsp_demo_java/blob/master/src/test/java/common/testExpression.java)
中的 
1. public void testRemove1()
2. public void testRemoveExprList()

[testModifyExpr](https://github.com/sqlparser/gsp_demo_java/blob/master/src/test/java/common/testModifyExpr.java)
[testModifySql](https://github.com/sqlparser/gsp_demo_java/blob/master/src/test/java/common/testModifySql.java)


