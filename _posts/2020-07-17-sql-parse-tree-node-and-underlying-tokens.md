---
layout: page
title: "Overview of General SQL Parser - sql parse tree node and underlying tokens"
excerpt: "A general review/summary of General SQL Parser: sql parser tree node and underlying tokens"
permalink: gsp-sql-parse-tree-node-and-underlying-tokens-cn.html
categories:
  - get-started-cn
  - sql-syntax
---
### Node和其对应token的关系
当SQL语句用GSP解析后，每个node都含有一个起始token(startToken)和一个结束token(endToken)。组成node的token由startToken开始，到endToken结束。node中的所有token以双向链表方式建立关联。调用node的`ToString()`方法，即从startToken开始输出文本，遍历每一个token，直到endToken结束。因此，**更新node的结构必须同步跟新对应的token**，否则node的`ToString()`将不能反应更新后node的文本情况。

`TGSqlParser` parse SQL 语句时，所有token在`dosqltexttotokenlist()`中建立双向链接。

```sql
SELECT e.emp_id,e.fname,e.lname,j.job_desc
FROM scott.employee AS e,jobs AS j
WHERE e.job_id = j.job_id -- this is a comment
ORDER BY e.fname,e.lname 
```

*<补充图1 显示上面SQL的SELECT语句对应的token list，是一个双向链接的token list，图中的每个token显示：text, tokentype,tokencode 这三个内容>*

### Node setString()
给一个node设置text时，GSP会把text转换成tokens， 然后把这些token插入到node所在parse tree的整个token链表中。

因为每种数据库的词法有差别，在把text转换成tokens时，需要明确是哪种数据库。为避免每次调用`setString()`时都额外指定数据库，引入一个静态全局变：`TGSqlParser.currentDBVendor`，当创建新的`TGSqlParser`实例时，设置`TGSqlParser.currentDBVendor`的值，该值总是和最近一次创建的`TGSqlParser`实例的数据库相同。**在多线程环境中这个设计可能导致问题**

```java
TWhereClause whereClause = new TWhereClause();
whereClause.setString("where a+b>c");
```

*<补充图2 显示上例中whereClause的token list>*


### Node toString()
增、删、改node时，把该node的token list同步到整个parse tree中，那么，输出整个parse tree的文本只要简单的
从该parse tree的startToken到endToken输出文本即可。

### 当增、删、改node时，如何把该node的token同步到整个parse tree中

#### 1. 改动node的文本
因为该node在parse tree中有对应的token list，只要把这些token在整个token list的位置用新的tokens替代就行。
具体实现时，更换startToken, endToken的双向指针的指向即可。

```sql
SELECT *
FROM scott.employee
WHERE e.job_id = 1
```
*<补充图3 显示上例中token list>*

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

执行上面Java代码后，SQL语句为：
```sql
SELECT *
FROM scott.employee
WHERE e.salary > 1000
```
*<补充图4 显示上例中新的SQL的token list>*


#### 2. 删除node
parse tree中删除一个node，把对应的tokens从parse tree的token list删除即可，但为保证SQL语法的正确，可能需要删除该node前后的一些辅助token。
以该SQL为例
```sql
SELECT e.emp_id,e.fname,e.lname,j.job_desc
FROM scott.employee AS e,jobs AS j
```
如果要从select list中删除`e.emp_id`， 则`e.emp_id`后面的`,`也必须一起删除。而删除`j.job_desc`时，则`j.job_desc`之前的`,`也必须一起删除。

*<补充图5 删除e.emp_id前的SQL的token list>*

*<补充图6 删除e.emp_id后的SQL的token list>*

如果要删除`jobs AS j`中的`J`时， `AS`也必须一起删除。

*<补充图7 删除j前的SQL的token list>*

*<补充图8 删除j后的SQL的token list>*


#### 3. 增加node
增加node时，对应的tokens需要加入到parse tree的token list中，
- 同时可能需要添加辅助token，以保证SQL语法的正确。

以该SQL为例
```sql
SELECT e.emp_id,e.fname,e.lname
FROM scott.employee AS e,jobs AS j
```
当在`e.lname`后加入`j.job_desc`时，必须在`j.job_desc`前同时加入`,`，以确保语法正确。

*<补充图9 加入`j.job_desc`前的SQL的token list>*

*<补充图10 加入`j.job_desc`后的SQL的token list>*


- 增加node时同步tokens的另一个问题是，如何在parse tree的token list中找到新node的tokens的插入位置。

以该SQL为例
```sql
SELECT e.emp_id,e.fname,e.lname
FROM scott.employee AS e,jobs AS j
```
如果增加一个where clause node， 即`WHERE e.job_id = j.job_id`， 那么该node对应的tokens应该插入到当前parse tree的token list中的哪个位置? 这种问题需要GSP解决。

*<补充图11 加入`WHERE e.job_id = j.job_id`前的SQL的token list>*

*<补充图12 加入`WHERE e.job_id = j.job_id`后的SQL的token list>*


### Node toScript

从上面的介绍可知，利用`toString()`从语法树生成SQL文本时，对语法树上node做改动时，必须对底层对应的token做好同步。


利用`toScript()`从语法树生成SQL文本时，对语法树上node做改动，无需对底层对应的token做同步，但对语句中
的每一个node都要根据语法重新生成文本，即便这个node在本次操作中没有发生变化。由于GSP目前无法对所有的SQL
语法都支持重新生成文本，因此容易导致生成不正确的SQL文本。

`toScript()`的优点在于改动语法树中的node时，无需同步更新底层的对应token，特别是一些辅助token。


### Token的基本信息

#### 1. token的类型
```java
public ETokenType tokentype
```
主要的类型有：
1. `ttkeyword`, 上例中的`SELECT`，`SELECT`，`FROM`，`WHERE`，`ORDER`，`BY`。
2. `ttidentifier`,上例中的`e`，`emp_id`等。
3. `ttwhitespace`, 空格和tab。
4. `ttreturn`,换行符。
5. 各种符号，`ttperiod`,`ttcomma`等。
6. `ttsimplecomment`，`ttbracketedcomment`，注释。

#### 2. token的code
```java
public int tokencode
```
code用来表示token的编号。`ttkeyword`类型的token有唯一不同的编号。`ttidentifier`类型的token编号值相同，都为`264`。各种符号的编号就是它们的ASCII值。

#### 3. token的text
token的文本。


### Node
Node表示SQL语法中的各个元素，例如 
1. 数据库对象名，`e.emp_id`，它包含三个token`e`,`.`,`emp_id`。
2. 也可以是一个子句(clause)，例如where子句，`WHERE e.job_id = j.job_id`,它包含`ttkeyword`，`ttwhitespace`，符号，`ttidentifier`等token。
3. 也可以是一个语句，例如SELECT,包含各种SQL子句。



#### TSourceToken中支持双向链接的相关属性和方法
```java
public void setPrevTokenInChain(TSourceToken prevTokenInChain)
public void setNextTokenInChain(TSourceToken nextTokenInChain)
public TSourceToken getPrevTokenInChain()
public TSourceToken getNextTokenInChain()
```
