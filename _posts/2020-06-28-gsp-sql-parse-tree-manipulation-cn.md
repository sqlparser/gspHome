---
layout: page
title: "Overview of General SQL Parser - sql parse tree manipulation"
excerpt: "A general review/summary of General SQL Parser: sql parser tree manipulation"
permalink: gsp-sql-parse-tree-manipulation-cn.html
categories:
  - get-started-cn
---

{% include toc %}

对SQL语法树的改动可以分类为：

1. 对已有node进行修改，用 `TParseTreeNode.setText()` 来实现。
该方法会同时更新node在token chain中对应的token。

2. 把node从树上删除，需使用相关的方法。 然后调用`TParseTreeNode.removeFromTokenChain()`把node在token chain中的token移除。

3. 在语法树上添加新的node，需使用相关方法把node添加到语法树上。然后用`TParseTreeNode.addToTokenChain(TSourceToken anchorToken, boolean beforeAnchorToken)`
在anchorToken后插入该node的token流。如果 `beforeAnchorToken = true`，在anchorToken前插入。以达到同步token流的目的。
一般由parent node决定 anchorToken, 即本 node token的插入位置。


#### 更多信息
- [GSP 基本信息](/gsp-overview-cn.html) 
- [SQL语法树：深入了解](/gsp-overview-sql-parse-tree-cn.html) 
- [SQL语法树：生成对应的SQL语句](/gsp-sql-parse-tree-to-query-cn.html)
- [SQL语法树：改动语法树](/gsp-sql-parse-tree-manipulation-cn.html) 