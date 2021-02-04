---
layout: page
title: "Data lineage analysis from multiple SQL Files."
excerpt: "Data lineage analysis from multiple SQL Files and get accurate metadata result in JSON and CSV format."
permalink: data-lineage-multiple-SQL-files.html
categories:
  - data-lineage
---

Data lineage analysis from multiple SQL Files

To get an accurate data lineage analysis result, we may provide 
the definition of the database objects such as table, view, procedure to
the GSP(General SQL Parser).

### 1. Parse SQL file with ambigious table/columnn relation

Take this SQL (file1.sql) for example: 

```sql
CREATE VIEW test 
AS 
  (SELECT NAME, 
          address 
   FROM   manager, 
          employee 
   WHERE  manager.id = employee.id) 
```

Without more information. GSP doesn't know the column `NAME`, `address` in 
the select list belongs to which table in the from clause.

### 2. Provides the table definition 

File2.sql
```sql
Create table employee (id number, name varchar2(100), address varchar2(100));
```

File3.sql
```sql
Create table manager (id number, age varchar2(100), country varchar2(100));
```

If you provide those 2 SQL files with the table definition to the GSP, 
then column `NAME`, `address` will be linked to the table `employee` correctly.

### 3. How to provides multiple SQL files to GSP
In GSP, `gudusoft.gsqlparser.dlineage.DataFlowAnalyzer` class do the actual work of 
data lineage analysis.

```java
	public DataFlowAnalyzer(File sqlFile, EDbVendor dbVendor, boolean simpleOutput) {
		this.sqlFile = sqlFile;
		this.vendor = dbVendor;
		this.simpleOutput = simpleOutput;
	}
```

As you can see here, the first parameter of `DataFlowAnalyzer` accept a `File` type
which will accept a directory that includes all SQL files that need to be processed.


You may also check the DataFlowAnalyzer demo under demos.lineage package shipped together
with the GSP library to find out how to feed multiple SQL files.


### 4. Pulling all objects from a database (table, view, function, procedure, and trigger definitions) 
Once you were pulling all objects from a database (table, view, function, procedure, and trigger definitions),
it is recommended to put the definition of a single object in a single SQL file, especially for 
function, procedure, and trigger definitions. In this way, the processing error in one single SQL file
will not affect the other SQL files.

The order of those SQL files put under a directory doesn't matter. GSP is smart enough to get the necessary
information accordingly.