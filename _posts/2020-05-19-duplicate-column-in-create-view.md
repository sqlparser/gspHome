Duplicate column in create view

```sql
CREATE TABLE t1(f1 int , f3 int);
CREATE TABLE t2(f1 int , f3 int);

CREATE VIEW v1
as
SELECT 
	t1.f1,  -- please note the column name will be f1 in v1
	t2.f1,  -- please note the column name will be f1 in v1
	t1.f2, t2.f3
FROM t1, t2
WHERE t1.f1 = t2.f1;
```

If you executed the above SQL against Oracle database, there will be a ORA-00957
error which means *duplicate column name*.

But the following SQL query will be executed succefully, because the view column
name is specified.

```sql
CREATE VIEW v1 (t1f1, t2f1, t1f2, t2f3)
as
SELECT 
	t1.f1,
	t2.f1,
	t1.f2, t2.f3
FROM t1, t2
WHERE t1.f1 = t2.f1;
```