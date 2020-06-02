### sqlserver join

#### 1. old outer join

- < old_outer_join >

Specifies an outer join using the nonstandard product-specific syntax and the WHERE clause. 

- The \*= operator is used to specify a left outer join
- The =\* operator is used to specify a right outer join.

**example**:

```sql
SELECT Tab1.name, Tab2.id
FROM Tab1, Tab2
WHERE Tab1.id *= Tab2.id
```

**Note**: Using this syntax for outer joins is discouraged because of the potential for ambiguous interpretation and because it is nonstandard. Instead, specify joins in the FROM clause.
It is possible to specify outer joins by using join operators in the FROM clause or by using the non-standard \*= and =\* operators in the WHERE clause. The two methods cannot both be used in the same statement.

**Convert to ANSI SQL**:

```sql
SELECT Tab1.name, Tab2.id
FROM Tab1 LEFT JOIN Tab2
ON Tab1.id = Tab2.id
```



#### 2. join hint

- < join_hint > ::= { LOOP | HASH | MERGE | REMOTE }

Specifies a join hint or execution algorithm. If \<join_hint\> is specified, INNER, LEFT, RIGHT, or FULL must also be explicitly specified. For more information about join hints.

**example**:

```sql
SELECT p.Name, pr.ProductReviewID
FROM Production.Product AS p
LEFT OUTER HASH JOIN Production.ProductReview AS pr
ON p.ProductID = pr.ProductID;
```

**Note**: join hint is T-SQL(Transact-SQL/sqlserver) grammar.













#### references 1:

- sqlserver2000 `FROM` clause syntax

```
[ FROM { < table_source > } [ ,...n ] ]

< table_source > ::=
table_name [ [ AS ] table_alias ] [ WITH ( < table_hint > [ ,...n ] ) ]
 | view_name [ [ AS ] table_alias ] [ WITH ( < view_hint > [ ,...n ] ) ]
 | rowset_function [ [ AS ] table_alias ]
 | user_defined_function [ [ AS ] table_alias ]
 | derived_table [ AS ] table_alias [ ( column_alias [ ,...n ] ) ]
 | < joined_table >
 
< joined_table > ::=
 < table_source > < join_type > < table_source > ON < search_condition >
 | < table_source > CROSS JOIN < table_source >
 | [ ( ] < joined_table > [ ) ]
 
< join_type > ::=
[ INNER | { { LEFT | RIGHT | FULL } [ OUTER] } ]
[ < join_hint> ]
JOIN

< join_hint > ::=
{ LOOP | HASH | MERGE | REMOTE }
```

- ANSI SQL 1999   `FROM`  clause syntax

```
<joined table> ::=
<cross join>
	| <qualified join>
	| <natural join>
	| <union join>
	
<cross join> ::=
	<table reference> CROSS JOIN <table primary>
	
<qualified join> ::=
	<table reference> [ <join type> ] JOIN <table reference>
		<join specification>
		
<natural join> ::=
	<table reference> NATURAL [ <join type> ] JOIN <table primary>
	
<union join> ::=
	<table reference> UNION JOIN <table primary>
	
<join specification> ::=
	<join condition>
	| <named columns join>
	
<join condition> ::= ON <search condition>

<named columns join> ::=
	USING <left paren> <join column list> <right paren>
	
<join type> ::=
	INNER
	| <outer join type> [ OUTER ]
	
<outer join type> ::=
	LEFT
	| RIGHT
	| FULL
	
<join column list> ::= <column name list>
```



#### references 2:

SQL server(page:2714): <https://www.sqlserverscience.com/wp-content/uploads/2018/09/SQL2000_release.pdf>

SQL 1992(page:180): [http://www.contrib.andrew.cmu.edu/~shadow/sql/sql1992.txt](http://www.contrib.andrew.cmu.edu/~shadow/sql/sql1992.txt%20)

SQL 1999(page:238): <http://web.cecs.pdx.edu/~len/sql1999.pdf>