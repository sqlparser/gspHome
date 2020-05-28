---
layout: page
title: "Overview of General SQL Parser - sql parse tree to query"
excerpt: "A general review/summary of General SQL Parser: sql parser tree to query"
permalink: gsp-sql-parse-tree-to-query-cn.html
---

{% include toc %}

从SQL语言的语法可知，一个SQL语句包含多个clauses，每个clause又包含一个或多个子clauses，依次递归。

The General SQL Parser(GSP) 遵循SQL语法规则，为SQL语句生成一棵对应的语法树，树上的节点（node）对应于SQL语法中的clause。反之，也可以为一棵SQL语法树生成对应的SQL语句。


### SQL语句、Tokens、语法树
1. SQL语句为一段文本，以字母为最小单位，线性存储。
2. Tokens，按照SQL语言的**词法**规则，lexer把SQL语句分解为以token为最小单位的token流。线性存储。
3. SQL语法树，parser读入token流，按照SQL语言的**语法**规则，生成node，并把这些node以层次结构形成语法树。


### Token流和语法树的关系
1. 每个node对应token流中的部分连续的token。start token表示该node的起始token，end token表示该node的结束token。
2. 父node包含所有子node的token。
3. 处于同一层级的node的token不会有重叠。
4. token以双向链表线性存储，node是分层的树型存储。 

### 从语法树生成SQL语句的方法
1. 方法1， 从语法树node对应的token流直接拼接文本，生成SQL语句。简单快速。
2. 方法2，根据语法树node的语法含义，每个node产生对应的SQL文本，父node的文本由子node的文本拼接而成，需要逐个node处理。如果某些node的语法信息不完整，会导致整个SQL语句文本生成的失败。
3. 方法3，有些node直接从对应的token流生成文本，有些node根据语法信息拼接SQL文本。这种方法是方法1和2的混合。


### 语法树可能的变动形式及对应SQL语句的产生方式
1. 由parser生成的语法树，完全没有变动。这时语法树的node和对应的token流也未作任何变动。直接由token流来生成SQL语句。（方法1）。
2. 完全手动从零开始创建语法树。
3. 由parser生成的语法树，用户根据需要，对其中的某些node进行了增、删、改操作。


### 从语法树生成SQL语句的具体实现

GSP演化到现在，有三个版本的实现。

#### 版本1的实现
该实现采用上面说的方法1，即从语法树node对应的token流直接生成SQL语句。对语法树的node进行改动时必须同步更新对应的token流，但如果这个同步维护的不好，容易导致出错。这个版本适合语法树没有变动，或node很少变动的情况。

#### 版本2的实现
该实现采用上面说的方法2。根据语法树每个node的语法含义，逐个产生对应的SQL文本，从顶层node开始，逐个node进行遍历，拼接SQL文本。这种实现的优点是逻辑清晰，节点变动时无需考虑对应的token流。但由于SQL语言本身的复杂及node类型繁多，如果有一个node类型尚未支持，整个SQL语句无法正确生成。

#### 版本3的实现
该实现是版本1的增强版本，从token流生成SQL语句。在操作语法树的同时更新对应的token流，token流采用双向链表，整棵语法树的token流始终保持完整。这种实现可以配合`visitor`模式，
只对感兴趣的node进行处理，并更新对应detoken流，其他node因为对应的token流未受影响，所有妨碍整个SQL语句的生成。

在同一次遍历处理过程中，处理的node不能重叠，即如果处理了父node，子node就无法处理，因为对应的token流在处理父node时已经完全更改。
只有在新的SQL语句产生后，由此产生一棵新的语法树，再次重复以上过程，直到所有所有需要大node都被处理。

#### 更多信息
- [GSP 基本信息](/gsp-overview-cn.html) 
- [SQL语法树：深入了解](/gsp-overview-sql-parse-tree-cn.html) 
- [SQL语法树：生成对应的SQL语句](/gsp-sql-parse-tree-to-query-cn.html)
- [SQL语法树：改动语法树](/gsp-sql-parse-tree-manipulation-cn.html) 
