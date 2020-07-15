---
layout: page
title: "General SQL Parser and SQLFrog"
categories:
  - sql-syntax
  - get-started-cn  
---

GSP在SQLFrog项目中的应用

### SQLFrog的两种工作模式
1. scan模式，仅找出需要转换的SQL语法和语义，给出报告，不做转换。
2. convert模式，找出需要转换的SQL语法和语义，并做转换。

scan为默认模式。

### SQLFrog和GSP的关系
SQLFrog的底层实现依赖GSP的解析能力、visitor模式、语法树改动、语法树到SQL文本的生成技术。


### 使用GSP的visitor模式
顶层SQL语句应用某种类型node的visitor后，可以快速高效的访问语句中所有该类型的node。

下面这段代码示例访问所有`TObjectName`类型的node。在同一个visitor中，我们可以同时处理多个类型的node，根据实际的业务需求决定。

```java
int ret = sqlparser.parse();
if (ret == 0){
    objectNameVisitor objectNameVisitor = new objectNameVisitor();
    for(int i=0;i<sqlparser.sqlstatements.size();i++){
        TCustomSqlStatement sqlStatement = sqlparser.sqlstatements.get(i);
        sqlStatement.acceptChildren(objectNameVisitor);
    }
}

class objectNameVisitor extends TParseTreeVisitor {
    public void preVisit(TObjectName node){
    }
}
```

#### 利用visitor来进行SQL语句中datatype的检查
例如，在netezza到snowflake的SQL转换过程中，我们需要检查datatype是否兼容，当发现create table语句中有使用ST_GEOMETRY datatype时， 我们就要标记出该datatype 需要被转换成snowflake的VARBINARY.

创建一个datatype visitor就非常容易实现以上功能。
```java
class datatypeVisitor extends TParseTreeVisitor {
    public void preVisit(TTypeName node){
    // 加入检查代码
    }
}
```

类似的，我们可以对**SQL函数**进行检查。


### visitor配合GSP的语法树改动技术，进行SQL转换
当找到需要转换的语法或语义点后，需要进行转换，通过修改GSP生成的SQL语法树，我们可以做到这一点。GSP提供两种方法可以从语法树生成SQL文本：`toString()` and `toScript()`。

#### toString()
利用`toString()`从语法树生成SQL文本时，要求对语法树上node做改动时，必须对底层对应的token做好同步。
**SQLFrog采用这种方法**。

#### toScript()
利用`toScript()`从语法树生成SQL文本时，对语法树上node做改动，无需对底层对应的token做同步，但对语句中
的每一个node都要根据语法树重新生成文本，即便这个node在本次操作中没有发生变化。由于GSP目前无法对所有的SQL
语法都支持重新生成文本，因此容易导致生成不正确的SQL文本。

详细的说明可以看[这篇文章](http://support.sqlparser.com/gsp-sql-parse-tree-to-query-cn.html)。
*还需要补充一篇文档对`toString()` and `toScript()`的工作原理做进一步的说明。*







### visitor相关代码
https://github.com/sqlparser/gsp_demo_java/tree/master/src/main/java/demos/visitors