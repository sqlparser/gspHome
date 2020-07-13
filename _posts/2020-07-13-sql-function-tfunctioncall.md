---
layout: page
title: "SQL Function and TFunctionCall"
categories:
  - sql-syntax
  - get-started-cn  
---

SQL function 在GSP中用TFunctionCall类表示。所有的function都用这个类表示。

### TFunctionCall中的基本信息
一般的SQL function的语法如下：
```sql
funcName(arg1,arg2)
```

TFunctionCall中对应属性值：
```
getFunctionName() = funcName
getArgs().size() = 2
getArgs().getExpression(0) = arg1
getArgs().getExpression(1) = arg2
getFunctionType() = unknown_t
```

目前 `getFunctionType()` 表示的函数类型**并不完善**，用它来判断函数并不一定准确，需小心。

### 不规则参数的函数

一般情况下，函数的参数由`TExpressionList getArgs()`获得。但一些非规则的函数参数需视情况逐个处理。
例如`cast`函数，
```sql
SELECT CAST(ytd_sales AS CHAR(5)) FROM titles
```

对应的参数分别为：
```java
getExpr1() = ytd_sales
getTypename() = CHAR(5)
```



### 判断一个函数是否为数据库的内置函数(built-in funciton)
1. 判断该函数是否为某一数据库的内置函数。`EDbVendor` 用来指定数据库厂商，例如`db2`,`oracle`等。
```java
public boolean isBuiltIn(EDbVendor pDBVendor)
```

2. 静态函数，需指定函数名。功能同1.
```java
public static boolean isBuiltIn(String pName, EDbVendor pDBVendor)
```
###  aggregate function
##### 1. ALL | DISTINCT 
`getAggregateType()` is used to determine the `ALL | DISTINCT` used in the aggregate function.

##### 2. WITHIN GROUP 
*This information is not available in the TFunctionCall yet.*


### window function
```sql
FUNCTION_NAME(expr) OVER {window_name | (window_specification)}
```

在Oracle and SQL Server中，`window_specification`也称为`window_clause`。

在GSP中，用`TWindowDef`表示`window_specification`, 在`TFunctionCall`中，用以下方法获得`window_specification`
```java
public TWindowDef getWindowDef()
```
以这个包含window function的SQL为例：
```sql
SELECT NUM, ODD,
CUME_DIST( ) OVER(PARTITION BY ODD ORDER BY NUM) cumedist
FROM test4
```
GSP的输出为：
```
sstselect
--> function: CUME_DIST, type:unknown_t
	window_specification
		Parition value: ODD
		Order by clause: NUM
```

#### CASE FUNCTION
用`TCaseExpression`表示。

### Related demo
[search SQL Function](https://github.com/sqlparser/gsp_demo_java/blob/master/src/main/java/demos/visitors/searchFunction.java)