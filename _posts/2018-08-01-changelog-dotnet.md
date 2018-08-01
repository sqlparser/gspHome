---
layout: page
title: "General SQL Parser .NET version changelog 2018-08-01"
categories:
  - changelog
---

+ dotnet version 3.2.5.6(2018-08-01)
  - [Oracle] fix a bug can't parse plsql block not ended by a semicolon.
  - [general] avoid System.ArgumentNullException when call isvalidsqlpluscmd().
 
+ dotnet version 3.2.5.6(2018-07-27)
  - [scriptWriter] fix a bug when new TObjectName with object and part source token.
  - [API] add new method: TSourceToken.toScript()

+ dotnet version 3.2.5.6(2018-07-11)
  - [SQL Server] support include clause before where condition in create index statement
  - [SQL Server] support WITH (DATA_COMPRESSION = PAGE) in create table statement.
  - [yacc,lex] Able to process rule from 2500 to 3000
  - [SQL Server] fix a bug can't parse CTE in declare for cursor statement.
 
+ dotnet version 3.2.5.5(2018-07-07)
  - [scriptWriter] fix a alias clause of pivot table not placed correct.
  - [scriptWriter] fix a bug can't rewrite bigint datatype correctly.
					
+ dotnet version 3.2.5.5(2018-07-05)
  - [scriptWriter] fix a bug can't rewrite datetime datatype correctly.
 
+ dotnet version 3.2.5.5(2018-06-04)
  - [SQL Server] support if exists clause in drop procedure/table/index statement.
 
+ dotnet version 3.2.5.4(2018-05-29)
  - [general] fix a null exception error raised when call TTable.getTableName() when tableType is subquery.

+ dotnet version 3.2.5.4(2018-05-25)
  - [sql format] fix a problem is that the first SELECT is printed after the closing ) of the INSERT INTO statement.
 
+ dotnet version 3.2.5.1(2018-05-16)
  - [general] upload Gudusoft.GeneralSQLParser package to nuget.org.
  - [general] library .NET core 2.0 compatible.
  
+ dotnet version 3.2.5.1(2018-05-13)
  - [demo\formatsql] move html output code to demo\formatsql, make this library .NET core 2.0 ready.
 
+ dotnet version 3.2.5.0(2018-05-10)
 - [demo\toXML] fix a bug that subquery in then clause of case statement not generated correctly.
 
+ dotnet version 3.2.5.0(2018-04-27)
 - [general] refine the code to remove unnecessary exception from the code.
 
+ dotnet version 3.2.4.6(2018-03-30)
 - [demo/sqlformat] support rtf output.
 - [general] Able to pickup oracle hint in delete/insert/update/merge statement.
 - [scriptWriter] fix a bug miss where keyword in delete clause of merge statement.
 
+ dotnet version 3.2.4.5(2018-03-14)
 - [scriptWriter] support for xml clause in scriptWriter
 - [SQL Server] support create or alter procedure.
 - [DB2] keyword IS can be used as table alias.
 - [Oracle] [Oracle/plsql] support new keyword in create trigger statement.

 
+ dotnet version 3.2.4.4(2018-03-13)
	- [demo/toXML] support for update clause in select statement.
	- [demo/toXML] support into clause in select statement.
	- [demo/toXML] support case statement in oracle plsql.
	- [demo/toXML] list the DISTINCT clause in select statement.
	- [demo/toXML] list return datatype in function declaration of a package. 
	- [demo/toXML] Able to recognize commit statement inside plsql block.
	- [demo/toXML] Able to list CTE in subquery of insert statement.
	- [demo/toXML] Able to list into clause in execute immedate statement.

 
+ dotnet version 3.2.4.3(2018-03-02)
 - [API] add TExpression.OwnerStmt which points to the SQL statement which includes this expression.
 - [scriptWriter] fix a bug can't rewrite Oracle into clause if more than one variable in the list.
		

+ dotnet version 3.2.4.2(2018-02-19)
 - [demos/xmlvisitor] Able to fetch columns in primary key of MySQL create table statement.
 
+ dotnet version 3.2.4.1(2018-02-06)
 - [SQL Server] support use hint clause.

+ dotnet version 3.2.4.1(2018-01-30)
 - [DB2] fix a bug can't parse create trigger statement when there is no keyword RW_ATOMIC after BEGIN keyword in compound trigger body.
 - [DB2] fix a bug can't parse BEFORE keyword in trigger option in create trigger statement.
 
+ dotnet version 3.2.4.0(2018-01-25)
 - [scriptWriter] support Oracle hint in select/delete/insert/udpate/merge
 - [API] Move OracleHint from TSelectSqlStatement to TCustomSqlStatement
 
+ dotnet version 3.2.3.9(2017-12-12)
 - [general] convert function support parameter and style property, use the same property as Java version.
   modify convert function code in TScriptGeneratorVisitor.cs as well.

+ dotnet version 3.2.3.8(2017-12-08)
  - [DB2] fix a bug can't parse create procedure when there is no parameter.
  - [DB2] support always as clause in alter table statement.
  - [DB2] support alter table  ADD VERSIONING USE HISTORY TABLE
  - [DB2] support alter table drop versioning.
  - [DB2] support drop columm cascade.
  - [DB2] support drop not null clause in alter column.
  - [DB2] able to recognize create variable statement.
 
+ dotnet version 3.2.3.8(2017-12-07)
 - [scriptWriter] fix a bug sql server convert function not rewrite correctly.
 - [DB2] supprt xmlserialize function.
 
+ dotnet version 3.2.3.7(2017-11-29)
 - [Oracle] fix a bug can't detect column in over clause of analytic function.		
 - [SQL Server] keyword: xml, server,Catalog, Cube treated as column name correctly.
 
+ dotnet version 3.2.3.6(2017-11-01)
 - [Oracle] fix a bug doesn't detect column name in create trigger like: :new.customer_id 
			
+ dotnet version 3.2.3.5(2017-10-31)
 - [Teradata] fix a bug can't detect table column in create macro statement.
 
+ dotnet version 3.2.3.4(2017-10-30)
- [Teradata] fix a bug treats variable in create macro statement as column.

+ dotnet version 3.2.3.3(2017-10-30)
 - [Oralce] support include/exclude nulls clause in unpivot clause.
 - [teradata] fix a bug can't parse is keyword in comment statement.
 - [general] able to recognize sequence object in syntax like:SEQ_COPS_CORIMA_EXECUTE_QUEUE.nextval and put it into TCustomSqlStatement.DatabaseObjects

+ dotnet version 3.2.3.2(2017-10-26)
  - [general] add TObjectName.coordinate() method return coordinate of the object in SQL script.	
  - [general]  ESqlClause.resultColumn replaced by selectList, insertColumn, mergeInsert

+ dotnet version 3.2.3.1(2017-10-16)
 - [Teradata] fix a bug treat built-in function CURRENT_DATE,CURRENT_TIME as column name.
 
+ dotnet version 3.2.3.0(2017-10-12)
 - [Oracle] Fix a bug can't parse CONSTRAINT keyword used as a columm name.
		
+ dotnet version 3.2.3.0(2017-10-12)
 - [general] Add TCustomSqlStatement.DatabaseObjects property which stores function/trigger/sequence and other database objects name which in the SQL query.

+ dotnet version 3.2.3.0(2017-10-11)
 - [SQL SERVER] support window aggregation group clause in analytic function.
 
+ dotnet version 3.2.3.0(2017-10-10)
 - [DB2] support alter column set not null
 - [DB2] support alter column set data type decimal
 - [Teradata] support comment on/create macro/drop macro/rename table statement.
 
+ dotnet version 3.2.2.5(2017-09-30)
 - [DB2] support XMLTable function.

 
+ dotnet version 3.2.2.5(2017-09-12)
 - [demo] add dataflowanalyzer demo.
 
+ dotnet version 3.2.2.4(2017-09-08)
 - [general] fix a bug sub-select of select union statement points to the wrong parent.

+ dotnet version 3.2.2.3(2017-09-07)
 - [SQL Server] Fix a bug treat table with nolock hint as a function.
 
+ dotnet version 3.2.2.2(2017-08-11)
 - [general] TTable.getTableName() will return "rowlist" if table type is table value constructor.	
 - [general] TTable.getTableName() will return "openrowset" if table type is openrowset.
 
+ dotnet version 3.2.2.1(2017-08-08)
 - [scriptWriter] fix test cases and removeCondition/joinConvert demo.

+ dotnet version 3.2.2.0(2017-08-04)
 - [scriptWriter] add new method:　TParseTreeNode.ToScript() which return String representation this parse tree node
 - [scriptWriter] demos\scriptWriter was merged into core parser under: gudusoft.gsqlparser.scriptWriter
 
+ dotnet version 3.2.1.5(2017-07-28)
 - [general] fix a bug can't detect CTE table in from clause if it original format is quoted ([Agency_cte]) while cte name in from clause is not quote('Agency_cte').
 - [SQL Server] support rebuild clause in alter table statement.
 - [SQL Server] fix a bug can't parse value keyword used as column name such as select b.value from b
			
+ dotnet version 3.2.1.4(2017-07-21)
 - [general] fix a bug TWindowDef.includingOverClause not set to true when over clause is used.
 
+ dotnet version 3.2.1.3(2017-07-20)
  - [general] replace class TAnalyticFunction by TWindowDef in DB2, Informix, SQL Server,Sybase

+ dotnet version 3.2.1.3(2017-07-19)
 - [general] replace TAnalyticFunction with TWindowDef
 - [general] use TFunctionCall.WindowDef instead of TFunctionCall.AnalyticFunction to fetch over clause information.
 
+ dotnet version 3.2.1.2(2017-07-02)
 - [demo] bug fix of joinConvert demo, removeCondition demo, scriptWriter demo.
 
+ dotnet version 3.2.1.1(2017-06-28)
 - [general] fix a bug: parent expr of and/or condition not set correctly.

+ dotnet version 3.2.1.0(2017-06-26)
 - [General] set parent of arguments (expr) in function call to function call.
 - [General] null checking in method: public virtual TSourceToken ComparisonOperator

 
+ dotnet version 3.2.0.9(2017-06-20)
  - [general] fix a bug that treat table hint as column name.
  
+ dotnet version 3.2.0.8(2017-06-14)
  - [DB2]  able to recognize update command options.
  - [general] fix a bug that TGSqlParser class getting a handle on a file and never releasing the lock.
  - [DB2] fix a bug can't parse labeled-duration use seconds keyword.
  - [DB2] fix a bug can't parse query when DATA used as table alias.

+ dotnet version 3.2.0.7(2017-06-12)
 - [General] fix a bug can't detect TABLE keyword in syntax like this: TABLE(subquery)
 - [General] add accept/acceptChildren method of TRestrictionClause.
 
+ dotnet version 3.2.0.6(2017-05-22)
 - [SQL Server] support percentile_cont, percentile_disc, parse, try_parse function.
 - [SQL Server] fix a bug can't handle opertors correctly if it is followed by # character.
  
+ dotnet version 3.2.0.6(2017-05-22)
 - [DB2] support create or replace clause in create procedure/function.

+ dotnet version 3.2.0.6(2017-05-05)
 - [DB2] fix a bug can't parse create function if use create or replace clause instead of create.
 
+ dotnet version 3.2.0.5(2017-04-17)
 - [general] fix stack overflow exception when process AND/OR predicate nested more than 1000 times.                               

+ dotnet version 3.2.0.3(2017-04-13)
 - [DB2] fix a bug can't link column to insert table in create trigger statement.
 - [general] support IEnumerable interface for TParseTreeNodeList and 
   all descendant classes such as : TTableList, TConstraintList, TExpressionList,TFromTableList,TJoinItemList
    TJoinList,TMultiTargetList,TObjectNameList,TTableElementList
 - [general] support IEnumerable interface for TSourceTokenList
 - [general] support IEnumerable interface for TStatementList.


+ dotnet version 3.2.0.2(2017-01-20)
 - [general] fix a null exception error while get table column.

+ dotnet version 3.2.0.2(2017-01-18)
 - [General] fix a bug link qualified column to table in the same level incorrectly without search up level.
 
+ dotnet version 3.2.0.1(2017-01-12)
 - [general] release API document on: http://wangz.net/doc/Help
 - [general] add indexer for TSourceTokenList, TStatementList,TConstraintList,TExpressionList,TFromTableList,
 							TJoinItemList,TJoinList,TMultiTargetList,TObjectNameList,TTableElementList,TTableList

+ dotnet version 3.2.0.0(2017-01-10)
 - [general] This is the first public release version with the same functionality as General SQL Parser Java version 1.8.
 - [general] APIs used to modify parse tree was temporary disabled in current version.
 - [document] including the first APIs documentation in chm.

+ dotnet version 3.1.0.2(2017-01-05)
 - [general] support TParseTreeNode.String property.

+ dotnet version 3.1.0.0(2016-12-28)
 - [demos] include demos.
 
+ dotnet version 3.1.0.0(2016-12-26)
 - [general] fix a bug raise null exception when init lexer of hive/db2/greenplum,
 resolve this problem by remove resource file in project property and add table files again.
 Not know why this happens

+ dotnet version 3.0.1.0(2016-11-14)
 - [DB2] Migrate lex and yacc file.

+ dotnet version 3.0.0.2(2016-08-31)
 - [general] add new fields:  TSourceToken.nodesStartFromThisToken, TSourceToken.nodesEndWithThisToken

+ dotnet version 3.0.0.1(2016-08-26)
 - [general] first release