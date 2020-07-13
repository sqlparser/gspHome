---
layout: page
title: "Overview of General SQL Parser - sql parse tree node and underlying tokens"
excerpt: "A general review/summary of General SQL Parser: sql parser tree node and underlying tokens"
permalink: gsp-sql-parse-tree-node-and-underlying-tokens-cn.html
categories:
  - get-started-cn
---

`TGSqlParser` parse SQL 语句时，所有token在`dosqltexttotokenlist()`中建立双向链接。


#### TSourceToken中支持双向链接的相关属性和方法
```java
public void setPrevTokenInChain(TSourceToken prevTokenInChain)
public void setNextTokenInChain(TSourceToken nextTokenInChain)
public TSourceToken getPrevTokenInChain()
public TSourceToken getNextTokenInChain()
```


#### TParseTreeNode利用双向链接进行SQL文本输出
```java
public String toString(boolean isModified)
```