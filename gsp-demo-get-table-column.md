---
layout: page
title: "Extracts the table/column from SQL script"
permalink: gsp-demo-get-table-column.html
---

{% include toc %}

### Run this tool

This tool will fetch table, column and column index inside the SQL script including PL/SQL. You can find this tool in demo\gettablecolumns shipped together with general SQL parser library Java and .NET version.

_getTableColumn /f path_to_sqlfile /t dbvendor /parameter_

(**In order to run this tool, JRE 1.5 or .NET framework 4.5 or higher need to be installed.**)

| Parameter |  DESCRIPTION |
|:--------|:-------:|
| `showSummary`  | Show the summary of database objects, if a table/column appears more than one time in the SQL script, it will be listed only once in this output   |
| `showDetail`   | List the detailed information of the all database objects in the SQL script   |
| `showTreeStructure`   | List the output of found database objects in a hierarchical level   |
| `showBySQLClause`   | Sort table and column by SQL clause   |
| `showJoin`   | List table and column used in the join condition, join condition in where clause also included   |
{: rules="groups"}

### Live demo

We have set up an online live demo for this too, please give it a try: [Get table column demo](http://107.170.101.241:8080/getTableColumn/).

### The detailed explanation of the output

##### Show the detailed information

This is an example output when showDetail is set to true:

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

This is an example output when showSummary is set to true:

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

This is an example output when showTreeStructure is set to true:

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