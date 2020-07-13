---
layout: page
title: "SQL Object and TObjectName"
categories:
  - sql-syntax
  - get-started-cn  
---

## SQL Object and TObjectName类

数据库中的Object，例如table, column, view, schema, database 在ANSI SQL中用`<identifier>`表示。
`<identifier>`是一个字符串，最大长度为128个字符。


### `<regular identifier>`
```xml
<regular identifier> ::=
    Object name
```

### `<SQL language identifier>`
```xml
<SQL language identifier> ::=
    Object name
```
An `<SQL language identifier>` is a `<regular identifier>` that consists only of simple Latin letters, digits, and underscore characters. It must begin with a simple Latin letter. 

### `<delimited identifier>`
```xml
<delimited identifier> ::=
    "Object name"
```
ANSI SQL中，`<delimited identifier>`用 double quote marks（双引号），而在SQL Server中，使用`[` and `]`.
MySQL使用 `` ` ``.

### `Qualification of <identifier>s`
`qualified object name`, 是指几个identifier的组合，形成有层次结构的object name。
一般是
```
server.db.schema.table.column
```

### SQL object name and TObjectName
在GSP中，用TObjectName表示SQL object name，用`TSourceToken`类表示identifier。
因此TObjectName 包含一个或多个`TSourceToken`，有下列可用的token：
```java
public TSourceToken getMethodToken()    -- 表示method
public TSourceToken getPartToken()      -- 表示column
public TSourceToken getObjectToken()    -- 表示 table，view, index等schema level的object
public TSourceToken getSchemaToken()
public TSourceToken getDatabaseToken()
public TSourceToken getServerToken()
```

#### Column
- Only column name

    ```sql
    select empNo
    from emp
    ```
    表示empNo column 的TObjectName中的各种值如下：
    ```
    getDbObjectType() = column
    toString() = empNo
    getPartToken() = empNo
    ```
    
- qualified column name
    ```sql
    select t.empNo
    from emp t
    ```
    表示empNo column 的TObjectName中的各种值如下：
    ```
    getDbObjectType() = column
    toString() = t.empNo
    getPartToken() = empNo
    getObjectToken() = t
    ```    
    
#### Table    
- Only the table name
    ```sql
    select empNo
    from emp
    ```
    
    表示emp table的TObjectName中的各种值如下：
    ```
    getDbObjectType() = table
    toString() = emp
    getObjectToken() = emp
    ```

- qualified table name with schema
    ```sql
    select t.empNo
    from scott.emp t
    ```
    表示emp table的TObjectName中的各种值如下：
    ```
    getDbObjectType() = table
    toString() = scott.emp
    getObjectToken() = emp
    getSchemaToken() = scott
    ```
    
- qualified table name with database and schema    
    ```sql
    select t.empNo
    from hrdb.scott.emp t
    ```
    表示emp table的TObjectName中的各种值如下：
    ```
    getDbObjectType() = table
    toString() = scott.emp
    getObjectToken() = emp
    getSchemaToken() = scott
    getDatabaseToken() = hrdb
    ```    
    
- qualified table name with server, database and schema    
    ```sql
    select t.empNo
    from server1.hrdb.scott.emp t
    ```
    表示emp table的TObjectName中的各种值如下：
    ```
    getDbObjectType() = table
    toString() = scott.emp
    getObjectToken() = emp
    getSchemaToken() = scott
    getDatabaseToken() = hrdb
    getServerToken() = server1
    ```       
    
#### Function

```sql
SELECT * FROM Department D
CROSS APPLY dbo.fn_GetAllEmployeeOfADepartment(D.DepartmentID)
```

表示fn_GetAllEmployeeOfADepartment function的TObjectName中的各种值如下：

```
getDbObjectType() = function
toString() = dbo.fn_GetAllEmployeeOfADepartment
getObjectToken() = fn_GetAllEmployeeOfADepartment
getSchemaToken() = dbo
```    


#### Method
Method like nodes() of SQL Server xml Data Type.

```sql
select	doc.c.value('level', 'int') as [Level]
from	N.ReformattedSegments.nodes('/path/segment') doc(c)
```

表示N.ReformattedSegments.nodes method 的TObjectName中的各种值如下：

```
getDbObjectType() = method
toString() = N.ReformattedSegments.nodes
getMethodToken() = nodes
getPartToken() = ReformattedSegments
getObjectToken() = N
```   

## Related demo
[search SQL Object](https://github.com/sqlparser/gsp_demo_java/blob/master/src/main/java/demos/visitors/searchSQLObject.java)
