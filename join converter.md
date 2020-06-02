### join converter

#### working process

1. parse SQL.   If parse error , print error message.
2. If one SQL text has many statements, handle separately.
3. If statements is combined query (Like union), handle separately.
4. When statements has not `Where` Clause , `From` Clause  will convert `cross join`.
5. ...








#### Improvement


  ANSI SQL92 default join is cross join.

  But sqlserver2000 and ANSI SQL99 default join is inner join.

> INNER
> Specifies that all matching pairs of rows are returned. Discards unmatched rows from both tables. This is the default if no join type is specified.
>
> SQL server: <https://www.sqlserverscience.com/wp-content/uploads/2018/09/SQL2000_release.pdf>
> page: 2714



#### Test case error

If SQL is not old SQL , call `convert()` throw `NullPointerException`.

```java
public void test( ){
String sqltext = "SELECT *\n" +
		"FROM   table1  cross join\n" +
		"       table2 \n" +
		"WHERE  table1.f2 > 10";
JoinConverter converter = new JoinConverter(sqltext,EDbVendor.dbvmssql);
System.out.println(converter.convert( ));
}
```

Output:

```
java.lang.NullPointerException
	at demos.joinConvert.JoinConverter.analyzeSelect(JoinConverter.java:569)
	at demos.joinConvert.JoinConverter.convert(JoinConverter.java:328)
	at test.testJoinConverter.test(testJoinConverter.java:408)
```

[JoinConverter.java](https://github.com/sqlparser/gsp_demo_java/blob/%23635/src/main/java/demos/joinConvert/JoinConverter.java)

```
566  JoinCondition jr = new JoinCondition( );
567  jr.expr = item.getOnCondition( );
568  jr.used = false;
569  jr.lexpr = jr.expr.getLeftOperand( );
570  jr.rexpr = jr.expr.getRightOperand( );
561  jr.lefttable = getExpressionTable( jr.lexpr );
562  jr.righttable = getExpressionTable( jr.rexpr );
```

