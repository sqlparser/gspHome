values-clause

```
values-clause
	Derives a result table by specifying the actual values, using expressions, for
	each column of a row in the result table. Multiple rows may be specified.
```

```sql
SELECT EMPNO, ’emp_act’
FROM EMP_ACT
WHERE PROJNO IN(’MA2100’, ’MA2110’, ’MA2112’)
UNION
VALUES (’NEWAAA’, ’new’), (’NEWBBB’, ’new’)
```

`values-clause`最长见的用法是在`INSERT`语句中，但也可以用在需要`SELECT`语句的地方。
这就是为什么`values-clause`在GSP中是用`TSelectSqlStatement`类来表示的原因。

`values-clause`的语法构成和`SELECT`语句非常的不同，
```sql
VALUES (1),(2),(3)
```

因此，当我们处理代表`values-clause`的`TSelectSqlStatement`类实例时，必须要小心，
因为很多`SELECT`语句中的元素这时是不在`TSelectSqlStatement`类实例中存在的，
访问这些类属性将会导致`NullPointerException`的错误。

### 访问`TSelectSqlStatement`表示的`values-clause`

Use this method to get `values-clause`
```java
public TValueClause getValueClause()
```
if the return value is not null, then this `TSelectSqlStatement` instance represents a values-clause.


Since GSP Java version 2.0.6.9(2020-06-18), TSelectSqlStatement.isValueClause() is added to help determine 
whether a `TSelectSqlStatement` class represents a values-clause or not.


