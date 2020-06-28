---
layout: page
title: "Overview of General SQL Parser - sql parse tree"
excerpt: "A general review/summary of General SQL Parser: sql parser tree"
permalink: gsp-overview-sql-parse-tree-cn.html
categories:
  - get-started-cn
---

{% include toc %}

### SQL语法树

GSP所有重要的功能，都是基于对SQL语法树的进一步利用。因此，熟悉并掌握
SQL语法树是使用GSP的第一步。

SQL语法树的各个组成部分基本和SQL语言中的语法元素一一对应。因此，熟悉
SQL语法树的最好方法是 对比某一个数据库，例如 MySQL 的 SQL 参考手册，逐一了解。


#### 一些重要的SQL语法树中的类
1. `TSelectSqlStatement`, select 语句。
2. `TDeleteSqlStatement`, delete 语句。
3. `TInsertSqlStatement`, insert 语句。
4. `TUpdateSqlStatement`, update 语句。
5. `TObjectName`, 表示数据库对象，例如：`table`, `column`,`function` 等的名称。
6. `TExpression`, SQL中的表达式。
7. `TFunctionCall`, SQL中的函数。
8. `TConstant`,  SQL中的常量，例如 字符串、数字等。
9. `TParseTreeNode`, 所有语法树中节点的父类。
10. `TSourceToken`, SQL 文本在形成语法树前，Lexer先把文本转换为token。


#### 相关 Demo
1. [手工方式遍历语法树](https://github.com/sqlparser/gsp_demo_java/tree/master/src/main/java/demos/analyzescript)
2. [遍历表达式](https://github.com/sqlparser/gsp_demo_java/tree/master/src/main/java/demos/expressionTraverser)
3. [采用Visitor模式遍历语法树](https://github.com/sqlparser/gsp_demo_java/tree/master/src/main/java/demos/visitors)


#### 用来测试的SQL
1. [w3schools SQL Tutorial](https://www.w3schools.com/sql/sql_intro.asp)
2. [SQL Server](https://docs.microsoft.com/en-us/sql/t-sql/queries/select-transact-sql?view=sql-server-ver15)
3. [Oracle](https://docs.oracle.com/cd/B19306_01/server.102/b14200/toc.htm)
5. [MySQL](https://dev.mysql.com/doc/refman/8.0/en/select.html)

#### 更多信息
- [GSP 基本信息](/gsp-overview-cn.html) 
- [SQL语法树：深入了解](/gsp-overview-sql-parse-tree-cn.html) 
- [SQL语法树：生成对应的SQL语句](/gsp-sql-parse-tree-to-query-cn.html)
- [SQL语法树：改动语法树](/gsp-sql-parse-tree-manipulation-cn.html) 