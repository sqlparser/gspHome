General SQL Parser .NET version

We have have confirmed, that the issue appears strictly only with .NET framework 4.6.1586.0, but happens just sometimes.

With the higher .NET framework 4.7.2053.0 all works fine.

```
2019-10-02 14:02:56,506 ERROR [11] ParserBase:0 Failed to parse vendor MsSql sql string 
CREATE TABLE COPS_ZT (
                                REC_ID     BIGINT IDENTITY NOT NULL,
                                REF_REC_ID BIGINT NOT NULL,
                                REC_DATE DATETIME2 NOT NULL,
                                REC_STATUS       NUMERIC NOT NULL,
                                REC_ERROR        NVARCHAR(255),
                                ZT_CREATION_USER NVARCHAR(255),
                                ZT_CREATION_DATE DATETIME2)
2019-10-02 14:02:56,513 ERROR [11] ParserBase:0 System.ArgumentException: Destination array was not long enough. Check destIndex and length, and the array's lower bounds.
   at System.Array.Copy(Array sourceArray, Int32 sourceIndex, Array destinationArray, Int32 destinationIndex, Int32 length, Boolean reliable)
   at System.Collections.Generic.Dictionary`2.Resize(Int32 newSize, Boolean forceNewHashCodes)
   at System.Collections.Generic.Dictionary`2.Insert(TKey key, TValue value, Boolean add)
   at gudusoft.gsqlparser.nodes.TTypeName.searchTypeByName(String typenameStr)
   at gudusoft.gsqlparser.nodes.TTypeName.set_DataTypeByToken(TSourceToken value)
   at gudusoft.gsqlparser.nodes.TTypeName.setDataTypeInTokens()
   at gudusoft.gsqlparser.TParserMssqlSql.yyaction(Int32 yyruleno)
   at gudusoft.gsqlparser.TParserMssqlSql.yyparse()
   at gudusoft.gsqlparser.TCustomSqlStatement.dochecksyntax(TCustomSqlStatement psql)
   at gudusoft.gsqlparser.TCustomSqlStatement.parsestatement(TCustomSqlStatement pparentsql, Boolean isparsetreeavailable)
   at gudusoft.gsqlparser.TGSqlParser.doparse()
   at CopsDatabasePatcher.SqlParser.SqlParser.Parse(String sql, DatabaseSystem system)
2019-10-02 14:02:56,522 ERROR [11] ParserBase:0 SQL 'CREATE TABLE COPS_ZT (
                                REC_ID     BIGINT IDENTITY NOT NULL,
                                REF_REC_ID BIGINT NOT NULL,
                                REC_DATE DATETIME2 NOT NULL,
                                REC_STATUS       NUMERIC NOT NULL,
                                REC_ERROR        NVARCHAR(255),
                                ZT_CREATION_USER NVARCHAR(255),
                                ZT_CREATION_DATE DATETIME2)' cannot be parsered! Reason 
```

Code to produce this error:

<img src="images/post/parserReport.png">