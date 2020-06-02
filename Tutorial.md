### Tutorial

#### 1. SQL Format

 - 1.1 example

   ```java
   TGSqlParser sqlparser = new TGSqlParser(EDbVendor.dbvmysql);
   GFmtOpt opt = GFmtOptFactory.newInstance();
   sqlparser.sqltext = "SELECT * FROM Persons WHERE Year>1965";
   int ret = sqlparser.parse();
   String result;
   if (ret == 0) {
       result = FormatterFactory.pp(sqlparser, opt);
   } else {
       System.out.println(sqlparser.getErrormessage());
   }
   ```

- 1.2 key API

  The key API is `FormatterFactory.pp(sqlparser, opt);` .

  - `TGSqlParser` This class includes a lexer and a parser. 
  - `GFmtOpt` This class is SQL Format options, see [GFmtOpt.java](https://github.com/sqlparser/gsp_demo_java/blob/master/src/main/java/demos/formatsql/GFmtOpt.java).

- 1.3 Note

  `GFmtOptFactory.newInstance()` return same `GFmtOpt` Object When called in same `Thread`.

- 1.4 Improvement

   Implement `clone` interface that can copy `GFmtOpt` Object.

#### 2. Check Syntax

- 2.1 example

  ```java
  TGSqlParser sqlparser = new TGSqlParser(EDbVendor.dbvmysql);
  GFmtOpt opt = GFmtOptFactory.newInstance();
  sqlparser.sqltext = "SELECT * FROM Persons WHERE Year>1965";
  int ret = sqlparser.parse();
  if (ret == 0) {
      System.out.println("The SQL without syntax error.")
  } else {
      System.out.println("The SQL has syntax error!");
      System.out.println(sqlparser.getErrormessage());
  }
  ```

  2.2 key API

  The key API is `int ret = sqlparser.parse();sqlparser.getErrormessage();` .

  - When `ret` equals `0` mean the SQL without syntax error.
  - When `ret` not equals `0` mean the SQL has syntax error and we can use `sqlparser.getErrormessage()` to get error message. 