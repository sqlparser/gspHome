---
layout: page
title: "Overview of General SQL Parser"
excerpt: "A general review/summary of General SQL Parser"
permalink: gsp-overview-cn.html
---

{% include toc %}

### Introduce

General SQL Parser(GSP) is a Java/.NET library, adding powerful SQL processing
capability to your own program instantly.

#### 语法校验

GSP 最基本也是最重要的功能：对各种数据库厂商的SQL 进行语法校验，并为通过
校验的SQL创建对应的语法树。这些语法树以 *Java/C# 类*的形式存在。如果被检查的
SQL有语法错误，报告错误的位置，这时不会产生语法树。

GSP的优势在于：
1. 所有的SQL语法校验都是类库自己独立完成，不需要连接到数据库。
2. 支持多达20多种主流数据库。
3. 对SQL语法的深度支持和覆盖，包括对存储过程的支持。
4. 统一的SQL语法树，容纳各种不同数据库的SQL语法。

#### SQL语法树

GSP所有重要的功能，都是基于对SQL语法树的进一步利用。因此，熟悉并掌握
SQL语法树是使用GSP的第一步。

1. SQL语法树的各个组成部分基本和SQL语言中的语法元素一一对应。因此，熟悉
SQL语法树的最好方法是 对比某一个数据库，例如 MySQL 的 SQL 参考手册，逐一了解。

2. SQL语法树的访问/遍历 方法有两种。 一种是 从顶层的SQL语句，例如`select`开始，
逐个人工遍历其中的每一个元素，例如 `select list`, `from clause`, `where condition`等，
找到需要的SQL元素。

3. SQL语法树的访问/遍历的另一种方法是使用 `visitor` 模式，只对感兴趣的SQL元素进行处理。
   
   使用`visitor`模式，创建一个小程序`decodeSQL`，输入任意一个SQL语句，打印出对应的
   SQL语法树（即显示各SQL元素所对应的*Java/C# 类*，显示要有层次结构，便于查看）。
   这个小程序可以帮助第一次使用GSP的用户快速找到 SQL元素 对应于语法树中的哪个 *Java/C# 类*。


#### SQL语法树的使用模式

从对SQL语法树的使用模式来看，GSP所有的功能可以分为两大类：

1. 仅遍历SQL语法树，获得所需信息，不对语法树进行改动。 例如分析一个存储过程
用到了哪些表，这些表是否被 插入/更新/删除 了数据等。

2. 对语法树进行改动，然后根据新的语法树产生对应的SQL语句。例如，在执行SQL前
动态修改 where 条件。


#### 更多信息
- [深入了解SQL语法树](/gsp-overview-sql-parse-tree-cn.html) 
