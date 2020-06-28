---
layout: page
title: "Extracts the table/column from SQL script"
---

This tool will fetch table, column and column index inside the SQL script including PL/SQL. You can find this tool in demo\gettablecolumns shipped together with general SQL parser library Java and .NET version.

{% include toc %}

### Run this tool

_getTableColumn /f path_to_sqlfile /t dbvendor /parameter_

(**In order to run this tool, JRE 1.5 or .NET framework 4.5 or higher need to be installed.**)

| Parameter |  DESCRIPTION |
|:--------|:--------|
| `showSummary`  | Show the summary of database objects, if a table/column appears more than one time in the SQL script, it will be listed only once in this output   |
| `showDetail`   | List the detailed information of the all database objects in the SQL script   |
| `showTreeStructure`   | List the output of found database objects in a hierarchical level   |
| `showBySQLClause`   | Show table and column group by SQL clause   |
| `showJoin`   | List table and column used in the join condition, join condition in where clause also included   |
{: rules="groups"}

### Live demo

We have set up an online live demo for this too, please give it a try: <a href="http://107.170.101.241:8080/getTableColumn/" class="btn btn--info">Get table column demo</a>

### The detailed explanation of the output

##### Show the detailed information

This is an example output when `showDetail` is set to true:

```
filename|spname|object type|schema|table|table effect
c:\prg\tmp\demo.sql||table||customers|tetCreate
 
filename|spname|object type|schema|table|column|location|linePos|columnPos|datatype
c:\prg\tmp\demo.sql||column||customers|customer_id|createTable|2|3|number:10
c:\prg\tmp\demo.sql||column||customers|customer_name|createTable|3|1|varchar2:50
c:\prg\tmp\demo.sql||column||customers|address|createTable|4|1|varchar2:50
c:\prg\tmp\demo.sql||column||customers|city|createTable|5|1|varchar2:50
c:\prg\tmp\demo.sql||column||customers|state|createTable|6|1|varchar2:25
c:\prg\tmp\demo.sql||column||customers|zip_code|createTable|7|1|varchar2:10
 
filename|spname|object type|schema|index|table|column|location|line|column
c:\prg\tmp\demo.sql||index||customers_pk|customers|customer_id|unknown|8|38
```

1. filename is the SQL script file, "N/A" means file name is not available.
2. spname: the stored procedure where this object is found. "N/A" means stored procedure is not available.
3. object type: the database object type listed in this line.
4. schema: the schema this object belongs to. "N/A" means schema is not available.
5. table: the table this object belongs to if any.
6. column: name of this column
7. location: SQL clause where this column was found, such as select list, where clause, update clause.
8. linePos, columnPos: line and column number in the script.
9. datatype: if this is a column in create table statement, datatype of this column will be listed.

##### Show the summary information

This is an example output when `showSummary` is set to true:

```
Tables:
t_av_internal
t_invoice
t_usage_interval
 
Fields:
missed.id_acc
t_av_internal.c_currency
t_av_internal.id_acc
t_invoice.current_balance
t_invoice.id_interval
t_invoice.invoice_currency
t_usage_interval.dt_end
t_usage_interval.id_interval
```

##### Show the tree structure

This is an example output when `showTreeStructure` is set to true:

```
sstplsql_createprocedure
 sst_loopstmt
  sstselect
   t_invoice(tetSelect)
     id_interval(joinCondition)
     current_balance(resultColumn)
     invoice_currency(resultColumn)
   t_usage_interval(tetSelect)
     id_interval(joinCondition)
     dt_end(resultColumn)
     dt_end(where)
     dt_end(orderby)
    orphan columns:
     id_acc(where)
  sst_assignstmt
  sst_assignstmt
  sst_assignstmt
  sst_exitstmt
 sst_ifstmt
  sst_assignstmt
  sst_loopstmt
   sstselect
    t_av_internal(tetSelect)
      c_currency(resultColumn)
      id_acc(where)
   sst_assignstmt
  sst_assignstmt
```

#### showBySQLClause
Show table and column group by SQL clause.

Take this SQL for example
```sql
SELECT Orders.OrderID, Customers.CustomerName, Orders.OrderDate
FROM Orders
INNER JOIN Customers ON Orders.CustomerID=Customers.CustomerID;
```

The generated result is:

```
Tables:
	tetSelect
		Orders(2,6)
		Customers(3,12)
Columns:
	joinCondition
		Orders.CustomerID(3,32)
		Customers.CustomerID(3,53)
	selectList
		Orders.OrderID(1,15)
		Orders.OrderDate(1,55)
		Customers.CustomerName(1,34)

```

#### showJoin
List table and column used in the join condition, join condition in where clause also included

Take this SQL for example
```sql
SELECT Orders.OrderID, Customers.CustomerName, Orders.OrderDate
FROM Orders
INNER JOIN Customers ON Orders.CustomerID=Customers.CustomerID;
```

The generated result is:

| JoinTable1 | JoinColumn1 | JoinTable2 | JoinColumn2 | JoinType | JoinOperator |
|:--------|:--------|:--------|:--------|:--------|:--------|
|Orders(3,25)|CustomerID(3,32)|Customers(3,43)|CustomerID(3,53)|inner|=|

### Handle the ambiguous columns in SQL script

Sometimes columns used in the SQL script was not qualified which make it's difficult or even impossible to find out which table this column belongs to. Take this SQL for example:

The ambiguous column SQL example
```sql
select ename
from emp, dept
where emp.deptid = dept.id
```

column ename in the first line is not qualified by table emp, so it's ambiguous to know which table this column belongs to emp or dept.

General SQL Parser hanlde such kind of SQL in three ways.

##### Just report an orphan column is found.

Below is the output generated by this tool by default:

```
filename|spname|object type|schema|table|column|location|linePos|columnPos|datatype
c:\prg\tmp\demo.sql|N/A|column|N/A|dept|dept.id|where|3|25|
c:\prg\tmp\demo.sql|N/A|column|N/A|missed|ename|resultColumn|1|8|
```

As you can see, table name of the column: ename was set to "missed" which means this tool can't detect the relationship between table emp and column ename.

##### Link to the first table in the table list

There is a parameter (linkOrphanColumnToFirstTable) you can use to link the orphan column to the first table in the from clause.  When linkOrphanColumnToFirstTable set to true, the output is:
```
filename|spname|object type|schema|table|column|location|linePos|columnPos|datatype
c:\prg\tmp\demo.sql|N/A|column|N/A|dept|dept.id|where|3|25|
c:\prg\tmp\demo.sql|N/A|column|N/A|emp|ename|resultColumn|1|8|
```

##### Provide database meta info to link the orphan column to the right table

Providing the database meta information by using the `IMetaDatabase` interface in the parser,  the orphan column can be linked to the corresponded table correctly. 

You may check the class `sampleMetaDB` shipped together with the library to see how to provide the database meta information. Typically, you need to connect to a database server and fetch the meta information in this class. When you implement such a class, General SQL Parser will automatically use that meta information to link the table and columns correctly.

database meta info provider
```java
setMetaDatabase(new sampleMetaDB())
```

### Handle the star (*) column

The star column means all columns in a table. This column will be linked to the table as well. If the star column in the select list is not qualified with a table name, then it will be linked to all tables in the from clause.

```sql
select *
from emp, dept
where emp.deptid = dept.id
```

The select list in the above SQL query will list all columns in both emp and dept table. so, the output generated by this tool is:
```
filename|spname|object type|schema|table|column|location|linePos|columnPos|datatype
c:\prg\tmp\demo.sql|N/A|column|N/A|emp|*|resultColumn|1|8|
c:\prg\tmp\demo.sql|N/A|column|N/A|emp|emp.deptid|where|3|11|
 
filename|spname|object type|schema|table|column|location|linePos|columnPos|datatype
c:\prg\tmp\demo.sql|N/A|column|N/A|dept|*|resultColumn|1|8|
c:\prg\tmp\demo.sql|N/A|column|N/A|dept|dept.id|where|3|25|
```

There is a parameter:`listStarColumn` in this tool that you can use to control the output of star column. This parameter only affects the output of `summary output`, it doesn't affect the output of the `detailed output` which always list the star column.

### Need more information about the table and column relationship and data flow?

This tool lists all table and columns involved in the SQL script. However, it doesn't tell you the relationship between columns of different tables, it doesn't tell the data flow among the table and columns.

If you want to know when a value of the column is updated, how many other table and columns will be affected. Or, If you want to know the value of a source column was calculated from which target columns,

then this tool won't help. The good news is that we do provide another tool: Dlineage [^dlineage] which do all the above thing for you.

### Further works

Current version extracts the table, column and index column from the SQL script. Other database objects in the SQL script is not listed yet.

### How to get this tool

This tool shipped together with the General SQL Parser library and under the demos\gettablecolums directory. You may also download the source code of this tool from here and modify it to meet your own requirement.

### Changelogs

- (2017-11-01)  Add showBySQLClause,showJoin output options.
- (2017-08-21)  Add the detailed output.
- (2017-08-10) List datatype information if the column is in create table statement.
- (2017-08-10) List index columns


[^dlineage]: [Data lineage article](http://support.sqlparser.com/gsp-demo-data-lineage)


