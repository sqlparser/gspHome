### GSP developer Tutorial



> - class TGSqlParser
>
> This is the main class of GSP library. Use instance of this class to parse SQL query and generate parse
> tree nodes for further processing.
>
> - enum EDbVendor
>
> This is the type of database vendors, such as Oracle, SQL Server, MySQL and so on. Must be used
> when initialize an instance of TGsqlParser class.
> 
>[gsp_for_java_developer_guide.pdf](http://sqlparser.com/kb/gsp_for_java_developer_guide.pdf)



#### 1.General concepts in GSP

##### 1.0 pre knowledge

> A **statement** is the basic command that can be sent on its own to the database engine. 
>
> Many statements consist of several building blocks called **clauses** - some are optional (like the WHERE, GROUP BY or ORDER BY clauses in a SELECT statement).

example:

> The following statement:
>
> ```
> SELECT foo FROM bar JOIN quux WHERE x = y;
> ```
>
> is made up of the following clauses:
>
> - SELECT foo
> - FROM bar
> - JOIN quux
> - WHERE x = y

##### 1.1 Statement

`TCustomSqlStatement`  is the base class of all SQL statements.

part of subclasses([all subclasses](./resource/TCustomSqlStatement_Subclasses.html)):

- `TSelectSqlStatement`
- `TUpdateSqlStatement`
- `TTruncateStatement`
- `TDeleteSqlStatement`
- `TInsertSqlStatement`


You can use `TGSqlParser.sqlstatements` to get statement list Because one SQL file or SQL string may have many statements.

##### 1.2 Parse tree node (clause)

`TParseTreeNode`  is the base class of all SQL clause/node.

part of subclasses([all subclasses](./resource/TParseTreeNode_Subclasses.html)):

- `TWhereClause`
- `TOrderBy`
- `TGroupBy`
- `TValueClause`
- `TLimitClause`

You can use `TSelectSqlStatement::getLimitClause` `TCustomSqlStatement::getWhereClause` to get Clause.

**Note:**Not all method work!

`TTruncateStatement` inherit `TCustomSqlStatement` but not have `TWhereClause`, so call `getWhereClause` will return null;

##### 1.3 Token

Token is the smallest element(word) of SQL in GSP.

example:

```java
sqlparser.sqltext = "Select   * From Person Where age> 20";
int ret = sqlparser.parse();
TSourceTokenList list = sqlparser.sourcetokenlist;
if (ret == 0)
    while(list.hasNext()) {
        TSourceToken t = list.next();
        System.out.print('[' + t.toString() + ']');
    }
```

output:(The empty bracket is white space between SQL word)

```
[Select][   ][*][ ][From][ ][Person][ ][Where][ ][age][>][ ][20]
```

##### 1.4 Expression

An expression is a combination of one or more values, operators, and SQL functions that evaluates to a value.

`TExpression` is the class of Expression.

 example:

- `SELECT SUM(col1-(col2+col3)) FROM table`  

  the `SELECT` part is an expression.

  You can use `TCustomSqlStatement::getResultColumnList::getExpr` to  get `SELECT` part expression.

- `SELECT * FROM Customers WHERE Country='Germany' AND City='Berlin'` 

  the `WHERE` part is an expression.

  You can use `TCustomSqlStatement::getWhereClause::getCondition` to  get `WHERE` part expression.


