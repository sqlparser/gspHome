---
layout: page
title: "General SQL Parser Java version changelog 2018-08-01"
categories:
  - changelog
---

version history of general sql parser:
+ GSP Java version 1.9.4.4(2018-08-22)
  - [API] Add new method TSourceToken TSourceToken.nextSolidToken(boolean treatCommentAsSolidToken)
  - [API] Add new method TSourceToken TSourceToken.prevSolidToken(boolean treatCommentAsSolidToken)

+ GSP Java version 1.9.4.4(2018-08-20)
  - [MySQL] support compressed keyword in alter table row_format clause.
  - [MySQL] support show index statement
  - [API] add new class TShowIndexStmt
  
+ GSP Java version 1.9.4.3(2018-08-15)
  - [Teradata] support COMPILE WITH NO SPL clause in alter procedure statement.
  - [PostgreSQL] support rename table clause in alter table statement.
  
+ GSP Java version 1.9.4.3(2018-08-13)
  - [getTableColumn] fix a bug can't recognize the column derived from CTE.
  
+ GSP Java version 1.9.4.2(2018-07-31)
  - [Oracle] fix a bug can't parse plsql block not ended by a semicolon.
  - [getTableColumn] link column in add/modify clause to table in alter table statement.
  
+ GSP Java version 1.9.4.2(2018-07-31)
  - [Oracle] fix a bug can't parse plsql block not ended by a semicolon.
  - [getTableColumn] link column in add/modify clause to table in alter table statement.
 
+ GSP Java version 1.9.4.2(2018-07-27)
  - [API] add new method: TSourceToken.toScript()

+ GSP Java version 1.9.4.2(2018-07-26)
  - [Teradata] Teradata Geometry datatype support 3 parts function.
  - [Teradata] support syntax that using "," between no values in function parameters.
 
+ GSP Java version 1.9.4.1(2018-07-25)
  - [Dlineage/demo] fix a bug source column is not shown correct when table name in from clause is with bracket

+ GSP Java version 1.9.4.1(2018-07-19)
  - [Teradata] fix a bug can't parse `||` operator followed by a variable directly.

+ GSP Java version 1.9.4.1(2018-07-18)
  - [API] TMssqlGrant replaced by TGrantStmt.
  - [SQL Server] fully support create schema statement.
  - [MySQL] fix a bug can't handle if not exists clause in create database statement.

+ GSP Java version 1.9.4.1(2018-07-17)
 - [MySQL] Support a list of tables of rename table statement.

+ GSP Java version 1.9.4.1(2018-07-16)
 - [scriptWriter] fix a bug can't handle group_concat() function correctly.

+ GSP Java version 1.9.4.0(2018-07-12)
 - [scriptWriter] fix a bug can't toScript() not working for regexp operator.
 
+ GSP Java version 1.9.4.0(2018-07-09)
 - [Teradata] support DYNAMIC RESULT SETS in create procedure statement.
 - [Teradata] fix a bug that parser can't parse a where clause before the from clauses
 - [Teradata] Able to parse sample clause before where clause.
 - [Teradata] Locking Access parse error.
 - [Teradata] Able to parse create trigger statement.
 - [Teradata] support "order by" clause within the scope of an xmlagg function call.
 - [Teradata] support unique keyword after select.

+ GSP Java version 1.9.4.0(2018-07-07)
 - [Teradata] Two sets of brackets is causing the parser to fail.
 - [API] add new classes related to execute_option: TExecuteOption, TResultSetsExecuteOption, TResultSetDefinition,TInlineResultSetDefinition,TSchemaObjectResultSetDefinition
 - [SQL Server] support execute_option in execute statement.
 - [DB2] support period clause in update statement.

 
+ GSP Java version 1.9.3.8(2018-07-03)
 - [Teradata] fix null exception bug in WindowFrame clause. 
 - [MySQL] Able to get default expression in alter table alter column clause.
 - [MySQL] use TRenameStmt to represent rename table statment.
 - [MySQL] fully support drop procedure statement.
 - [SQL Server] use TDropProcedureStmt instead of TMssqlDropDbObject to represent drop procedure statement.
			
+ GSP Java version 1.9.3.7(2018-06-15)
 - [Teradata] support return...hash...local sequence in table clause.
 - [Teradata] support upper function in the right side of IN condition.
 - [Teradata] support AT clause in TIMESTAMP constant.
 - [Oralce] fix a bug can't parse CREATE MATERIALIZED VIEW statement when STORE AS BASICFILE clause is used.
 - [Oracle] support alter materalized view refresh clause.
 - [Hana] support placeholder syntax in from table clause.

 
+ GSP Java version 1.9.3.6(2018-06-13)
 - [Redshift] fix a bug that include limit clause in order by clause.
 	 
+ GSP Java version 1.9.3.6(2018-06-12)
 - [API] add new method: TInformixOuterClause.getTableList()
 - [PostgreSQL] fix a null exception bug when parse create table like statement.
 - [DB2] support copy options in create table statement.
 - [Informix] using TLimitClause to fetch skip clause, first max, limit max value in select list.
 
+ GSP Java version 1.9.3.5(2018-06-01)
 - [XML\xsd] shipped sqlschema.xsd together with this libraty.
 - [XML\xsd] add NOT keyword in generated xml for like, between predicate.
 - [XML\xsd] support cte_list type in query_expression_type
 - [general] fix a bug caused by set tableExpr in setTableonly() method.
 
+ GSP Java version 1.9.3.5(2018-05-31)
 - [demo\toXML] improve sqlschema.xsd to support all tags generated by toXML demo.

+ GSP Java version 1.9.3.5(2018-05-30)
 - [general] fix a bug not treat FCT as table collection expression in SQL like this: select a from TABLE(FCT);

+ GSP Java version 1.9.3.4(2018-05-29)
 - [demos\columnImpact\] fix a bug introduced when support subquery in TTable.getTableName() 

+ GSP Java version 1.9.3.4(2018-05-28)
 - [netezza] supprt overlaps operator in where condition.
 
+ GSP Java version 1.9.3.4(2018-05-28)
 - [general] fix a null exception error which will raised when call TTable.getTableName() when tableType is subquery.
 
+ GSP Java version 1.9.3.3(2018-05-22)
 - [greenplum] support like other_table clause in create table.
 - [API] add new enum: ETableElementType

+ GSP Java version 1.9.3.2(2018-05-18)
 - [DB2] support DEACTIVATE ROW ACCESS CONTROL clause in ALTER TABLE
 - [DB2] support UNIQUE keyword in select statement.
 - [demo\toXML] support create variable statement.
 
+ GSP Java version 1.9.3.1(2018-05-17)
 - [DB2] Support Oracle pl/sql code used in DB2 database by calling oracle parser internally.
 - [DB2] fix a bug can't get create trigger staetment correctly if there is a for cursor in loop .. end loop statement inside.
 - [demo\toXML] supprot create alias statement.
 - [DB2] support create variable statement.
	

+ GSP Java version 1.9.3.1(2018-05-16)
 - [DB2] lexer error while processing literal '/\_op\_sox/Project/Default/BusinessEntity/%'
 - [DB2] support PRIOR operator.
 - [DB2] support Hierarchical Query Clause.
 - [DB2] can't detect declare statement in create trigger statement.
 - [DB2] support varchar2 datatype.
 
	

+ GSP Java version 1.9.3.1(2018-05-15)
 - [DB2] support decfloat/CODEUNITS16, CODEUNITS32 datatype.
 - [DB2] support OCTETS in varchar/char datatype.

 
+ GSP Java version 1.9.3.0(2018-05-14)
 - [demo\toXML] support TSetDatabaseObjectStmt in toXML demo.
 
+ GSP Java version 1.9.3.0(2018-05-13)
 - [DB2] Able to get full information from set [current] schema statement.
 - [DB2] support with no row movement clause in create view statement.
 - [DB2] support comment statement.
 - [DB2] support create audit policy statement.
 - [API] move TCreateAuditPolicyStmt, TAlterAuditPolicyStmt from gudusoft.gsqlparser.stmt.hana to gudusoft.gsqlparser.stmt
 - [SQL Server] support order by clause before union set operator.
 - [MySQL] support using clause in execute statement.
 - [MySQL] support timestamp argument in get_format function.
 - [MySQL] support time/datatime/double/signed int datatype in cast function.
 - [MySQL] support between condition in select list.
 - [MySQL] fully support create database statement.
 - [MySQL] fix a bug TObjectName.getTableString() and TObjectName.getSchemaString() not return schema and table name correctly in describe statement.

 
+ GSP Java version 1.9.2.9(2018-05-09)
 - [SQL Server] Fully support drop schema statement, represented by TDropSchemaSqlStatement
 - [API] add TDropDatabaseStmt.getDatabaseNameList()
 - [SQL Server] Fully support drop database statement, represented by TDropDatabaseStmt
 
+ GSP Java version 1.9.2.9(2018-05-08)
 - [DB2] IS keyword can be used as table alias.
 
+ GSP Java version 1.9.2.9(2018-05-07)
 - [Oracle] Support drop partition clause in alter table statement.
 
+ GSP Java version 1.9.2.8(2018-04-28)
 - [DB2] Support create alias statement.

+ GSP Java version 1.9.2.7(2018-04-25)
 - [Oralce] support keep/nokeep/session/global option in create sequence statement.
 - [Teradata] fix a bug that dividing variables causing parsing issue.
 - [Teradata] support create macro only having ; within it.
 - [Teradata] single line comment in stored procedure cause parsing error.
 - [Teradata] support with/without return clause in declare statement.
 - [Teradata] support signal and resignal statement in procedure.
	 
+ GSP Java version 1.9.2.7(2018-04-25)
 - [Sybase] Able to recogine load table statement.
 - [General] fix a java.lang.ClassCastException: gudusoft.gsqlparser.nodes.TColumnWithSortOrder cannot be cast to gudusoft.gsqlparser.nodes.TIndexColName

+ GSP Java version 1.9.2.6(2018-04-20)
 - [DB2] fix a bug can't parse if statement if there is a label before it.
 - [DB2] support NOT SECURED clause in create trigger statement.
 - [DB2] support diagnostic-string-expression in signal-information clause of signal statement.
 - [DB2] fix a bug can't fetch create trigger statement correctly if it comes after create procedure statement.
 - [DB2] support release savepoint statement.
 
+ GSP Java version 1.9.2.6(2018-04-20)
 - [getTableColumn] fix a bug can't detect select list column derived from a subquery which is consists of several select statement by using union/intersect/except operator.

+ Java version 1.9.2.5(2018-04-18)
 - [Netezza] support execute statement.
 
+ Java version 1.9.2.4(2018-04-09)
 - [Oracle/plsql] fix a bug can't detect pacakge name in assignment statement in plsql.
 - [API] add TObjectName.getPackageToken() returns the source token of Oracle package name.
 - [API] add TObjectName.getNumberOfPart() which returns the total part number of an objectname. For example: scott.emp which return 2.
 - [Netezza] Able to get new synonmy name in alter synonmy statement.
 - [Netezza] Able to pickup SAMEAS tablename in create external table statement using TCreateTableSqlStatement.getAsTable().
 
+ Java version 1.9.2.4(2018-04-08)
 - [demo/formatsql] support RTF output in this release.
 - [Sybase] support execute command without exec keyword if there is no multiple statements in the batch
 
+ Java version 1.9.2.3(2018-04-07)
 - [SQL Server] support CLOSE { SYMMETRIC KEY key_name | ALL SYMMETRIC KEYS } 
 - [Teradata] support default clause in parameter declaration.
 - [Netezza] support substring syntax like substring (arg1,arg2,arg3)

+ Java version 1.9.2.3(2018-04-03)
 - [MySQL] Able to recogine show count(*) errors/warnings
 
+ Java version 1.9.2.2(2018-04-03)
 - [Teradata] support select list item with parenthesis around.
 - [Teradata] support DEFAULT DATE attribute in parameter declaration of create/replace macro statement.
 
+ Java version 1.9.2.1(2018-03-29)
 - [Teradata] support XC, XCF, XCF after character type.
 - [Teradata] fix a bug can't parse END IF keyword after elseif clause directly.
 - [Teradata] support while statement.
 - [Teradata] fix a bug can't recognize ( symbol before datatype in create table statement.
 - [Teradata] support DECLARE EXIT HANDLER/DECLARE CONTINUE HANDLER;
 

+ Java version 1.9.2.1(2018-03-27)
 - [Teradata] fix a bug can't parse quaify clause after column alias.

+ Java version 1.9.2.0(2018-03-26)
 - [SQL Server] support IF EXISTS clause in drop table statement.
 - [MySQL] support qualified name in describe statement.
 
 
+ Java version 1.9.2.0(2018-03-26)
 - [Hana] support all statements of Hana including create procedure/function/trigger stored procedure.

+ Java version 1.9.1.2(2018-03-19)
 - [Hana] support validate user/ldap provider statement.
 - [Hana] support update statement.
 - [API] move TUnsetStmt from package gudusoft.gsqlparser.stmt.snowflake; to package gudusoft.gsqlparser.stmt
 - [Hana] support unload/unset statement.
 - [Hana] support truncate collection/table statement.

+ Java version 1.9.1.2(2018-03-18)
 - [Hana] support set history session/pse/schema/system license/transaction statement.
 - [Hana] support rollback statement.
 - [Hana] support rename collection/column/database/index/table statement.
 - [Hana] support recover data/database statement.
 - [Hana] support merge delta/merge statement.
 - [Hana] support lock table/merge delta statement.
 - [API] rename THiveLockSqlNode to TLockSqlNode, mover from package gudusoft.gsqlparser.nodes.hive; to package gudusoft.gsqlparser.nodes;
 - [API] rename THiveLockTable to THiveLockTable and move from package gudusoft.gsqlparser.stmt.hive; to package gudusoft.gsqlparser.stmt
 - [Hana] support load statement.
 - [Hana] support insert statement.
 - [Hana] support export/import statement.
 - [Hana] support explain plan statement.

+ Java version 1.9.1.2(2018-03-15)
 - [API] move TDropTriggerSqlStatement from package gudusoft.gsqlparser.stmt.postgresql; to package gudusoft.gsqlparser.stmt
 - [Hana] support drop audit policy, drop certificate/collection/credential statement.
 - [Hana] support delete statement.
 - [Hana] support create workload class/mapping statement.
 - [Hana] support create type/user/usergroup/virtual function/virtual table statement.
 - [API] TMssqlCreateType move from package gudusoft.gsqlparser.stmt.mssql to package gudusoft.gsqlparser.stmt
 - [Hana] support create table statement.
 
+ Java version 1.9.1.2(2018-03-14)
 - [Hana] support create synonmy statement.
 - [Hana] support create role/saml provider resource/schema/sequence/statistics/structured privilege statement.
 - [API] move TCreateRoleStmt from gudusoft.gsqlparser.stmt.snowflake to gudusoft.gsqlparser.stmt
 - [Hana] support create JWT provider/LDAP provider/pse/remote resource statement.
 - [Hana] support create index statement.
 - [Hana] support create certificate/collection/credential/database/fulltext index/graph workplace statement.
 
+ Java version 1.9.1.1(2018-03-12)
  - [getTableColumn] fix a bug can't link  a un-qualified column to table using IMetaDatabase interface.
  - [Oracle] support SUBMULTISET condition in plsql if statement.
  - [Oracle] fix a null exception when processing object_access_expression in toXML demo 
  - [SQL Server] support masked with clause in create/alter table statement.
  
+ Java version 1.9.1.0(2018-03-08)
 - [Oracle] support the combination of GENERATED and NOT NULL keywords in create table statement.
 - [Oralce] support SUBMULTISET condition.
 - [Oracle] support for the EXTEND procedure in pl/sql.
 - [demo/toXML] support CTE in select statement which is not at the top level.
 
+ Java version 1.9.0.9(2018-03-07)
 - [Netezza] support if not exists clause in create table statement.
 - [Netezza] fully support create synonmy, sequence statement.
 - [Netezza] fully support drop sequence, grant statement.
 
+ Java version 1.9.0.8(2018-03-02)
 - [MySQL] fails on encountering string literals with a certain form, making it impossible to route stetements containing them
 
+ Java version 1.9.0.7(2018-02-26)
 - [Hana] support create audit policy statement.
 - [Hana] support call, comment on, commit, connect statement.
 - [Hana] support backup check, backup data, backup list data statement.
 - [Netezza] support synonym, drop database, call statement.
 - [Netezza] parse alter table query which adds multiple columns at a time
 - [Netezza] support drop procedure statement.
 - [Hana] support backup cancel, backup catalog delete statement.
 - [Hana] support alter usergroup, alter view, alter view cache, alter virtual table, alter workload class, alter workload mapping statement.

+ Java version 1.9.0.7(2018-02-24)
  - [API] TAlterUserStmt more from gudusoft.gsqlparser.stmt.snowflake to gudusoft.gsqlparser.stmt
  - [Hana] support alter table, alter user statement.
  - [API] TAlterRoleStmt move from gudusoft.gsqlparser.stmt.vertica to gudusoft.gsqlparser.stmt
  - [Hana] support alter PSE, alter remote source, alter role, alter saml provider, alter sequence, alter statistics, alter system statement.

+ Java version 1.9.0.6(2018-02-23)
  - [Netezza] fix a bug can't handle using clause in create external table statement.
  - [Hana] support alter audit policy, alter credential, alter database, alter fulltext index, alter index, alter LDAP provider, alter JWT provider statement.
  
+ Java version 1.9.0.5(2018-02-14)
  - [demo/dlieange] dlineage improvement.
  
+ Java version 1.9.0.4(2018-02-06)
  - [general] fix a null exception error when iterate the convert function call.
				
+ Java version 1.9.0.3(2018-02-02)
 - [netezaa] Able to pickup etkTemp info when create table using TEMP clause
 - [general] fix OutOfMemory error when process nested case statement.


+ Java version 1.9.0.3(2018-02-01)
 - [DB2] "-" can't be used as character in identifier.
 - [DB2] support for cursor name in declare statement.
 - [DB2] support drop table statement inside create procedure statement.
 - [Sybase] support order by clause in update statement. 
 - [Oracle] fix a bug CASE keyword can't be used as table alias.

	
+ Java version 1.9.0.2(2018-01-25)
  - [netezaa] support merge statement.
  - [Oracle] fully parse drop procedure statement
  - [Oracle] fix a bug  TObjectName.schemaString is blank after processing view name in drop MATERIALIZED VIEW statement.	
  - [netezaa] fully parse drop view statement.
  - [netezaa] fully parse alter synonmy statement.
  - [netezaa] fully parse alter schema statement.
  
+ Java version 1.9.0.1(2018-01-24)
  - [netezaa] fully parse drop table statement.
  - [netezaa] fully parse alter database statement.
  - [netezaa] fully parse alter view statement.
  - [netezaa] fully parse create user statement.
  - [netezaa] support create external table .. sameas syntax.
  - [netezaa] support rename column in alter table statement.
  - [netezaa] fix a bug can't parse CREATE OR REPLACE materialized VIEW.
  
+ Java version 1.9.0.1(2018-01-18)
  - [snowflake] support all snowflake statements.
  - [snowflake] support truncate table statement, undrop database, schema, table statment, unset, use statement.
  - [snowflake] support line comment start in #

+ Java version 1.9.0.0(2018-01-17)
  - [snowflake] support show file formats, functions and all show statements.
  
+ Java version 1.9.0.0(2018-01-16)
  - [API, general] move gudusoft.gsqlparser.stmt.TRedshiftShow to gudusoft.gsqlparser.stmt.TShowStmt
  - [API, general] move gudusoft.gsqlparser.stmt.TRedshiftSet to gudusoft.gsqlparser.stmt.TSetStmt
  - [snowflake] support put, remove, revoke, set, show columns, show databases statement
  
+ Java version 1.9.0.0(2018-01-15)
  - [snowflake] support list, merge statement
  
+ Java version 1.9.0.0(2018-01-12)
  - [snowflake] support insert statement.
  - [snowflake] support get statement,grant ownership, grant statement
  
+ Java version 1.9.0.0(2018-01-11)
  - [snowflake] support all drop statements.
  - [snowflake] support drop database, drop file format, drop pipe, drop role, drop network policy, drop monitor rresour
  - [API,redshift] move gudusoft.gsqlparser.stmt.redshift.TRedshiftDropDatabase to gudusoft.gsqlparser.stmt.TDropDatabaseStmt
  - [snowflake] support desc statement, drop function,

+ Java version 1.9.0.0(2018-01-10)
  - [snowflake] support delete,
  - [snowflake] support create user, create warehouse

+ Java version 1.9.0.0(2018-01-09)
  - [snowflake] support create stage, create table,
  
+ Java version 1.9.0.0(2018-01-08)
  - [snowflake] support create schema, create sequence, create share,
  
+ Java version 1.9.0.0(2018-01-03)
  - [snowflake] support create pipe, create resource monitor, create role,
  - [snowflake] support copy into statement, create database, create file format,create function, create network policy

+ Java version 1.9.0.0(2018-01-03)
  - [snowflake] support bind variable
  - [snowflake] support comment, commit statement

+ Java version 1.9.0.0(2017-12-27)
  - [snowflake] support alter schema, alter sequence, alter session, alter share, alter stage, alter user,alter view, alter warehouse, begin

+ Java version 1.9.0.0(2017-12-26)
 - [general] rename TAlterRoleRename to TAlterRoleStmt
 - [snowflake] support alter resource monitor, alter role,
 - [snowflake] support alter account, alter database, alter file format,alter function, alter network policy, alter pipe

 
+ Java version 1.8.9.8(2017-12-22)
 - [general] fix a bug can't handle BOM while using parser.setSqlInputStream(input).
	
+ Java version 1.8.9.8(2017-12-20)
 - [sybase] support parameter in create procedure with no parameter mode specified.

+ Java version 1.8.9.8(2017-12-19)
 - [general] extend identifier length from 255 to 8080 character.

 
+ Java version 1.8.9.7(2017-12-11)
  - [SQL Server] support OPTIMIZE FOR ( @xml = NULL ) in option clause.
  - [DB2] Able to recognize label on statement.
  - [Oracle] support EDITIONABLE keyword in create trigger statement.
  - [Oracle] support VIRTUAL VISIBLE clause in column definition.
  
+ Java version 1.8.9.6(2017-12-04)
 - [teradata] able to pickup date keyword if it's used a column name in query.
 - [teradata] support echo statement in REPLACE MACRO statement.
 - [teradata] support more than one data attribute in datatype used in REPLACE MACRO parameter.
 - [teradata] support rollback statement in replace macro statement.
 
+ Java version 1.8.9.5(2017-12-01)
 - [oracle] schema and object name was set correctly in syntax like: schema1.proc1 in stored procedure.
 
+ Java version 1.8.9.5(2017-11-30)
 - [MySQL] able to get comment from column definition in alter table statement.
		
+ Java version 1.8.9.5(2017-11-29)
 - [SQL Server] keyword: xml, server,Catalog, Cube treated as column name correctly.

+ Java version 1.8.9.4(2017-11-24)
  - [Sybase] detect SQL syntax error instead of raising NullPointerException when isnull ( rules_failed , '' )

+ Java version 1.8.9.3(2017-11-10)
 - [MySQL] fix ClassCastException when create a new node of TMySQLPrepareSqlNode
 
+ Java version 1.8.9.2(2017-11-08)
 - [Oracle] support rename statement.
 - [Oracle] support editioning keyword in create view statement.
 - [Oracle] support preserve/purge materialized view log.
 - [Oracle] support drop materialized view, drop materialized view log statement.	
 - [teradata] support trycast function.
 
+ Java version 1.8.9.1(2017-11-06)
 - [general] add fastSetString in TParseTreeNode.java 
 - [MySQL] lexer performance improvement.
 - [demo] DataFlowAnalyzer support /s option, only list physical table/column relationship

+ Java version 1.8.9.1(2017-10-30)
 - [Teradata] fix a bug treats variable in create macro statement as column.
		
+ Java version 1.8.9.0(2017-10-27)
 - [Oracle] support create database link statement.
 
+ Java version 1.8.9.0(2017-10-26)
 - [Oracle] support drop public database link
 - [Oralce] support drop synonmy statement.
 - [Oralce] support include/exclude nulls clause in unpivot clause.


+ Java version 1.8.8.9(2017-10-25)
 - [demo] getTableColumn demo add a new option showBySQLClause to list database object in order of SQL clause.
 - [general] add TObjectName.coordinate() method return coordinate of the object in SQL script.
 - [general]  ESqlClause.resultColumn replaced by selectList, insertColumn, mergeInsert
 
	  
+ Java version 1.8.8.8(2017-10-18)
  - [Teradata] support default value in variable decalre.
  - [Teradata] support declare condition/declare handler sqlexception/sqlwarning/not found

+ Java version 1.8.8.8(2017-10-16)
  - [Teradata] support empty block between BEGIN/AND.
  - [Teradata] support set value clause in insert clause of merge statement.
  - [Teradata] fix a bug treat built-in function CURRENT_DATE,CURRENT_TIME as column name.

 
+ Java version 1.8.8.7(2017-10-12)
 - [Oracle] Fix a bug can't parse CONSTRAINT keyword used as a columm name.

+ Java version 1.8.8.7(2017-10-11)
 - [SQL SERVER] support window aggregation group clause in analytic function.

+ Java version 1.8.8.7(2017-10-10)
 - [DB2] support alter column set not null
 - [DB2] support alter column set data type decimal
	
+ Java version 1.8.8.7(2017-10-09)
 - [Oracle, DB2, SQL Server, Netezza, Teradata and MySQL] Able to handle $$ODS_LOB in this expr: p.SUBDIV_QUALIFIER=$$ODS_LOB
 
+ Java version 1.8.8.6(2017-09-30)
 - [MySQL] fix a bug can't parse interval clause like this: now() + INTERVAL (term2 * 1) day

+ Java version 1.8.8.6(2017-09-29)
 - [Oracle] fix a bug can't handle $$ODS_LOB in this expr: p.SUBDIV_QUALIFIER=$$ODS_LOB			
 - [general] enhance TSqlCmds to fetch supported SQL statement types, able to update support SQL statements in website. 
 
+ Java version 1.8.8.5(2017-09-12)
 - [demo] add dataflowanalyzer demo.

+ Java version 1.8.8.4(2017-09-08)
  - [SQL Server] Able to recognize insert bulk statement.
  - [general] fix a bug sub-select of select union statement points to the wrong parent.

+ Java version 1.8.8.4(2017-09-06)
  - [Teradata] fix a bug can't handle period keyword used as column name.
  - [Netezza] support double datatype.
  - [Netezza] support from external table clause.
  - [Netezza] support call statement.

+ Java version 1.8.8.3(2017-08-30)
 - [MySQL] fix a bug can't parse character name in string format like 'utf8'
 - [MySQL] execute stmt represented by class TExecutePreparedStatement instead of TUnknownSqlStatement.
 - [MySQL] change execute stmt parameter from type TExecParameterList to TExpressionList
 
+ Java version 1.8.8.2(2017-08-21)
 - [getTableColumn] Add the detailed output.

+ Java version 1.8.8.2(2017-08-22)
 - [Oracle] fix a bug can't parse pivot clause with parenthesis arounded.
 
+ Java version 1.8.8.1(2017-08-15)
 - [scriptWriter] support else clause in insert all statement (Oracle). All testcases in testScriptGenerator was passed.
 - [general] Add TInsertSqlStatement.isInsertAll() and TInsertSqlStatement.isInsertFirst() method represents 
   Oracle insert all/first clause.

+ Java version 1.8.8.0(2017-08-10)
 - [scriptWriter] scriptWriter feature avaiable in this release, use TParseTreeNode.toScript() method to return string representation
 of any parse tree node including SQL statement.
 - [general] add new method: TCustomSqlStatement.getIndexColumns(), return all index information included in this SQL statement.
 - [getTableColumn] return datatype information if column is in create table statement.
 - [MySQL] support COLLATE name in string literal. 
 - [MySQL] Able to recoginze session and global option in show variables command.
 - [MySQL] fix bug can't parse nested escape character in string literal.
 
+ Java version 1.8.7.2(2017-08-09)
 - [general] TTable.getTableName() will return "rowlist" if table type is table value constructor.
 - [general] TTable.getTableName() will return "openrowset" if table type is openrowset.	
 - [general] replace class: TIndexColName with TColumnWithSortOrder
 - [general] add new class:　TColumnWithSortOrder used in column list in unqiue and primary key.
 - [general] change type of TConstraint.columnList from TObjectNameList to TPTNodeList<TColumnWithSortOrder> ;
 

+ Java version 1.8.7.2(2017-08-07)
 - [SQL Server] support compute clause in scriptWriter.
 - [SQL Server] remvoe class TComputeClauseItemList, replaced by TPTNodeList<TComputeClauseItem> in TComputeClause
 - [SQL Server] remove class TComputeExprList, replace by TPTNodeList<TComputeExpr> in TComputeClauseItem

+ Java version 1.8.7.2(2017-08-07)
 - [Oracle] fix a bug treat interval day to second as generic datatype.

 
+ Java version 1.8.7.2(2017-08-06)
 - [general] remove method:　public TParseTreeNode createConstant(TParseTreeNode node,ENodeType ent)
 - [general] TConstant.stringLiteralSequence change from type to TPTNodeList <TConstant> to TSourceTokenList.
 - [general] enhance TConstant class to support scriptWriter.
 
+ Java version 1.8.7.1(2017-08-04)
 - [scriptWriter]
 
 All code under demos\scriptWriter was merge into core parser under: gudusoft.gsqlparser.scriptWriter
 
 Add new method public String toScript() in TParseTreeNode
 
  private TScriptGenerator scriptGenerator = null;

    /**
     * Text string of this node, return value is the same as {@link #toString()} if this node is not modified
     * after created by parser.
     * If this node is modified, then use this method to return string representation instead of {@link #toString()}
     * @return text string of this node
     */
 
  public String toScript(){
    if (scriptGenerator == null){
        scriptGenerator = new TScriptGenerator();
    }
     return scriptGenerator.generateScript(this);
  }
  
 
 From TScriptGenertor move to TExpression
 1. searchColumnInExpr(TExpression sourceExpr, String columnName) -> searchColumn(String columnName)
 2. removeExpr(TExpression pExpr) -> remove()
 3. copyExpr(TExpression src,TExpression target) -> copyTo(TExpression target)
 4. public TExpression createXXXXX is removed, use new TExpression(EExpressionType pExpressionType),
	TExpression(EExpressionType pExpressionType, TExpression pLeft, TExpression pRight),
	and TExpression(EExpressionType pExpressionType, TExpression pLeft, TExpression pRight, EComparisonType pComparisonType) instead.
 
 From TScriptGenertor move to test.scriptWriter.testScriptGenerator
 1. verifyScript( TSourceTokenList originalTokenList ) -> verifyScript(EDbVendor dbVendor, String src, String target)
 
 In TExpression
 1. original method remove() was renamed to remove2()
 
 
 - [scriptWriter]  Move method from TScriptGenertor.searchColumnInExpr() to TExpression.searchColumn() 
 - [scriptWriter]  Move method from TScriptGenertor.copyExpr() to TExpression.copyTo()
 - [scriptWriter] Move method from TScriptGenertor.removeExpr() to TExpression.remove();
 - [general] rename TExpression.remove() to TExpression.remove2() for placeholder, don't use remove2() method in new code.

+ Java version 1.8.7.1(2017-08-03)
 - [sriptWriter] rewrite all scriptWriter related testcases.
 - [sriptWriter] merge code of scriptWriter into the core parser, add new method TParseTreeNode.toScript() to get SQL script of any nodes.
 - [general] add TMssqlExecuteAs.getLoginName() to replace getUserName() method.
 
 
+ Java version 1.8.7.0(2017-08-01)
 - [snowflake] support select and create view statement.
 - [general] make sure variable will not be recognized as column
 - [Dlineage demo] fix a bug can't build table/column relation correctly in merge statement.
	
+ Java version 1.8.6.5(2017-07-27)
 - [general] fix a bug can't detect CTE table in from clause if it original format is quoted ([Agency_cte]) while cte name in from clause is not quote('Agency_cte').

+ Java version 1.8.6.5(2017-07-27)
 - [Teradata] fix a bug can't parse type cast inside create macro statement.
 - [Teradata] fix a bug can't parse <= operator if there is space before : like this: stm.startmonth<=:strRptYear
 - [Teradata] support comment on statement.
 - [generic] fix generic parser doesn't work.

+ Java version 1.8.6.5(2017-07-26)
 - [Teradata] able to parse select statement that put expand on clause before where clause.
 - [Teradata] fix a bug treats col1 (DATE) as funciton call in  select col1 (DATE), col2 from tab1
 - [Teradata] support abort statement.
 - [Teradata] support not null constraint in parameter declarations in CREATE/REPLACE MACRO.
 - [general] schema and object name was set correctly in TRenameStmt.
 - [general] support generic parser.
 - [Oracle] fix a bug can't parse when "translate" used as column name.
 
+ Java version 1.8.6.4(2017-07-20)
 - [Netezza] support create materialized view statement.
 - [Netezza] Able to recognize temporary table in create table statement by using TCreateTableSqlStatement.getTableKinds()
		
+ Java version 1.8.6.3(2017-07-20)
 - [Hana] support WITH CACHE RETENTION <minute_value> and WITH STRUCTURED PRIVILEGE CHECK clause in create view.	
 - [general] replace class TAnalyticFunction by TWindowDef in DB2, Informix, greenplum,ODBC,Sybase, Teradata
 
+ Java version 1.8.6.3(2017-07-18)
 - [general] Remove public enum TWindowFrame.EWindowExpressionType { Rows,Range};, use ELimitRowType {Rows,Range} instead 
 - [general] Move public enum EBoundaryType {ebtUnboundedPreceding,ebtUnboundedFollowing,ebtCurrentRow,ebtPreceding,ebtFollowing};	from TWindowFrameBoundary to gudusoft.gsqlparser
 - [general] move public enum EWindowExcludeType { currentRow,ties,group,noOthers};  from TFrameExclusionClause to gudusoft.gsqlparser 
 - [general] over clause in analytic function is represented by TWindowDef class. class TAnalyticFunction is not used any logner.
 - [general] remove TWindowDef.setFrameClause,TWindowDef.getFrameClause, use TWindowDef.setWindowFrame, TWindowDef.getWindowFrame instead.

+ Java version 1.8.6.3(2017-07-17)
 - [general] replace class TAnalyticFunction by TWindowDef in Oracle, SQL SERVER
 
+ Java version 1.8.6.2(2017-07-14)
 -[toXML] add precision and scale in datatype
			
+ Java version 1.8.6.2(2017-07-13)
 - [hive] support union clause in select statement used in insert statement.
 
+ Java version 1.8.6.1(2017-07-02)
 - [MySQL] support source command and \. command.
 - [MySQL] Use HashMap instead of ArrayList to search SQL command in TSqlCmds.		
 - [MySQL] support nchar in cast function.
 - [MySQL] support fulltext(column) index.
 - [MySQL] able to recognzie show profile/profiles statement.
 - [greenplum] support psql meta command also know as slash or backslash commands
 - [greenplum] able to detect \ character.
 

+ Java version 1.8.6.1(2017-06-30)
 - [greenplum] support analyse keyword in analyze statement.
 - [toXML] support precedence Field Expression in toXML demo.				
 - [toXML] support analytic function in toXML demo.
 - [general] merge class TWindowSpecification and TWindowDefinition into TWindowDef
 - [general] class TPartitionByClause replaced by TPartitionClause 

+ Java version 1.8.6.0(2017-06-28)
 - [Hive] fix a bug can't parse the window function contains only order by clause.
 
+ Java version 1.8.6.0(2017-06-26)
 - [DB2] fix a bug keyword YEAR/SECOND can't be used as table alias.	
 - [netezaa] support CTE of select statement in create table statement.
 - [General] set parent of arguments (expr) in function call to function call.			
 - [General] add EExpressionType.removed_t which is used in remove expression.
	
+ Java version 1.8.5.9(2017-06-19)
 - [MySQL] add support for row construction.
	
+ Java version 1.8.5.9(2017-06-19)
 - [MySQL] Can't parse query when DEFAULT is used in set clause of update statement
 
+ Java version 1.8.5.8(2017-06-16)
 - [general] fix a bug that treat table hint as column name.
	
+ Java version 1.8.5.8(2017-06-6)
  - [MySQL] support the syntax .tbl_name, which is indicating 'tbl_name with default database'.
  
+ Java version 1.8.5.7(2017-06-14)
  - [MySQL] support row list comparision in select list.
  - [MySQL] support table.* in Multiple-Table delete statement.
  - [MySQL] fix a bug can't parse comment enclosed within double quote (") characters.
  - [DB2]  able to recognize update command options.
  - [DB2] fix a bug can't parse labeled-duration use seconds keyword.
  - [DB2] fix a bug can't parse query when DATA used as table alias.


+ Java version 1.8.5.6(2017-06-02)
 - [Teradata] fix a bug can't parse number after percent keyword in collect statistics.


+ Java version 1.8.5.6(2017-05-27)
 - [general] able to pickup table in select ... into clause.
 
+ Java version 1.8.5.6(2017-05-25)
 - [Sybase] fix an OutOfMemoryError when parser can't parse SQL script.
 
+ Java version 1.8.5.6(2017-05-22)
 - [DB2] support create or replace clause in create procedure/function.


+ Java version 1.8.5.5(2017-05-19)
 - [MySQL] support primary key clause without PRIMARY keyword.
 - [MySQL] fix a bug treat ----9223372036854775808 as comment.
 - [MySQL] support order by clause in alter table statement.
 - [MySQL] support procedure analyze clause.
 - [MySQL] support order by clause before union keyword in select statement.

+ Java version 1.8.5.5(2017-05-18)
 - [MySQL] support select topic = all (subquery)
 - [MySQL] fix a bug treats LOW_PRIORITY keyword as table name in delete statement.
 - [MySQL] support multiple empty values in insert values clause.
 - [MySQL] able to recognize reset statement.
 - [MySQL] fix a bug can't recognzie := operator in set statement.
 - [MySQL] able to recognize flush statement.
 - [MySQL] support create aggregate function.
 - [Teradata] fix a bug can't (DATE) after case...end expr.
 - [Teradata] fix a bug can't parse USING _spVV0 (DATE)
 - [Teradata] support rename table statement.
 - [Teradata] support rename column in alter table.
 - [Teradata] support parenthesis around column in add clause of alter table.
 - [general] max rule of yacc extended to 3000 from 2500

+ Java version 1.8.5.4(2017-05-17)
 - [Teradata] fix a bug can't parse float number in using option of COLLECT STATISTICS statement.
 - [Informix] fix a bug can't check syntax inside create procedure statement.
 - [Teradata] fix a bug treat sysdate as column name.
                    

+ Java version 1.8.5.4(2017-05-16)
 - [Teradata] support drop macro statement.
 
+ Java version 1.8.5.3(2017-05-12)
 - [general] performance improvement by modify code in public enum ENodeType, TCustomLexer.java and TLexerMysql.java
 - [couchbase] support execute statement, support all couchbase(N1QL) statements.

+ Java version 1.8.5.3(2017-05-11)
 - [couchbase] support insert/update/merge/upsert/explain/prepare statement
   
+ Java version 1.8.5.2(2017-05-05)
 - [couchbase] support build/create/drop index, delete,infer


+ Java version 1.8.5.1(2017-04-26)
 - [ODBC] add a list of customized keywords to odbc_keyword.properties
 - [ODBC] fix a bug treat some keywords as identifier.


+ Java version 1.8.5.0(2017-04-24)
 - [general] change of TCustomLexer.java to make performance improvement.

 
+ Java version 1.8.4.9(2017-04-21)
 - [sql formatter] fix stack overflow bug when format deep nested AND/OR expression.
 
+ Java version 1.8.4.9(2017-04-19)
 - [general] column in create table statement derived from select list column alias was marked as columnAlias.
 - [MySQL] support prepare statement quoted with "
 - [MySQL] able to recognize show keys/full fields statement.
 - [MySQL] support explain extended statement.
 - [MySQL] fix a bug can't handle "b+@@global.max_user_connections"
 - [MySQL] support set SQL_SELECT_LIMIT
 - [MySQL] support DEFAULT keyword in values clause of insert statement.
 - [MySQL] support time(length) datatype.
 - [MySQL]  support negtive value in decimal datatype.
 - [MySQL] fix a bug can't handle float number like: +.1, -.1
 - [MySQL] support long byte datatype.
 - [MySQL] support SQL_BUFFER_RESULT.

+ Java version 1.8.4.9(2017-04-18)
 - [MySQL] support in expr in select list.
 - [MySQL] fix a bug can't handle hex number: 0xD0B0D0B1D0B2
 - [MySQL] support set sql_mode, set timestamp statement.
 - [MySQL] support character set clause in cast function.
 - [MySQL] fix a bug can't handle timestamp const when it's quoted using " character.
 - [MySQL] support is unknown predicate.
 - [MySQL] support less equal, great equal in select list.
 - [general] expand yystack work correctly.
 - [MySQL] support set sql_mode statement.
 - [MySQL] support 3 parts qualified name start with variable.

+ Java version 1.8.4.8(2017-04-17)
 - [general] fix stack overflow exception when process AND/OR predicate nested more than 1000 times.
 - [general] increase max_chars to be able to process huge string literal. 
 - [Teradata] get table column fix a bug can't link column in subquery when there are qualified tables used in where condition.
 - [Teradata] support SUBSTR function that use FOR keyword instead of Teradta syntax.


+ Java version 1.8.4.7(2017-04-14)
 - [Teradata] support NULLS LAST/FIRST clause in sort clause.
 - [Teradata] fix a bug LAST can't be used as table alias.
 - [Teradata] support qualify clause in select list.
 - [Teradata] support primary index clause in collect statistics.
 - [Teradata] support asc/desc sort order in quantile function.

+ Java version 1.8.4.7(2017-04-13)
 - [Teradata] support collect statistics with a name only.
 - [Teradata] support sample clause before from clause.
 - [getTableColumn] able to recogine column alias used in where clause.  
 - [Teradata] support variable when there is a tab character between : and name like this: ":	Payment_Month"

+ Java version 1.8.4.6(2017-04-12)
  - [getTableColumn] fix a bug treats table alias in update clause as a real table. 

+ Java version 1.8.4.6(2017-04-07)
  - [getTableColumn] when search column in select list of subquery, 
     if column alias of this result column exist and doesn't match, 
     then ignore this result column.


+ Java version 1.8.4.6(2017-04-05)
 - [SQL Server] support for system_time clause.
 - [MySQL] fix a bug the lexer doesn't properly handle hash symbols at the beginning of quoted identifiers.


+ Java version 1.8.4.6(2017-03-27)
 - [Oracle] fix a bug can't parse chr function in translate function arguments.

+ Java version 1.8.4.5(2017-03-22)
 - [Vertica] support show statement.

+ Java version 1.8.4.5(2017-03-21)
 - [MySQL] fix a bug treat procedure parameter as column name.
 - [MySQL] support deallocate prepare statement.
	 
+ Java version 1.8.4.5(2017-03-20)
 - [Vertica] support set statement.
 - [Vertica] support revoke statement.
 - [Vertica] support profile statement.
 - [Vertica] support grant statement.
 - [Vertica] support export to vertica statement.
 - [Vertica] support explain statement.

+ Java version 1.8.4.4(2017-03-19)
 - [Vertica] support drop view statement.
 - [Vertica] support drop user statement.
 - [Vertica] support drop transform function statement.
 - [Vertica] support drop text index statement.
 - [Vertica] support drop subnet statement.
 - [Vertica] support drop sequence statement.
 - [Vertica] support drop schema statement.
 - [Vertica] support drop role statement.
 - [Vertica] support drop resource pool statement.
 - [Vertica] support drop projection statement.
 
+ Java version 1.8.4.3(2017-03-17)
 - [Vertica] support drop profile statement.
 - [Vertica] support drop procedure statement.
 - [Vertica] support drop network interface statement.
 - [Vertica] support drop library statement.
 - [Vertica] support drop function statement.
 - [Vertica] support drop fault group statement.
 - [Vertica] support drop authentication statement.
 - [Vertica] support drop aggregate function statement.
 - [Vertica] support drop access policy statement.
 - [Vertica] support disconnect statement.
 - [Vertica] support create user statement.
 - [Vertica] support create text index statement.
 - [Vertica] support create subnet statement.

+ Java version 1.8.4.2(2017-03-14)
 - [Vertica] support create hcatalog schema statement.
 - [Vertica] support create function statement.
 - [Vertica] support create fault group statement.
 
+ Java version 1.8.4.2(2017-03-13)
 - [DB2] fix a bug can't parse quoted string not ended correctly.
 - [Vertica] support create access policy statement.
 - [Vertica] support comment statement.
 - [Oracle] rename stmt\oracle\TOracleCommentOnSqlStmt to stmt\TCommentOnSqlStmt
 - [Oralce] use sstCommentOn instead of sstoraclecomment
 
 - [Vertica] support release savepoint statement.
 - [Vertica] support rollback statement.
 - [Vertica] support savepoint statement.
 - [Vertica] support commit/end statement.
 - [Vertica] support begin/start transaction statement.


+ Java version 1.8.4.1(2017-03-12)
 - [Vertica] support alter session statement.
 - [Vertica] support alter schema statement.
 - [Vertica] support alter role rename statement.
 - [Vertica] support alter resource pool statement.
 - [Vertica] support alter profile statement.
 - [Vertica] support alter network interface statement.
 - [Vertica] support alter projection rename statement.
 
+ Java version 1.8.4.1(2017-03-09)
 - [Vertica] support alter node statement.
 - [Vertica] support alter library statement.
 - [Vertica] support alter function statement.
 - [Vertica] support alter fault group statement.
 - [Vertica] support alter database statement.
 - [Vertica] support alter authentication statement.

+ Java version 1.8.4.1(2017-03-08)
 - [DB2] able to detect string not ended by " correctly.  
 - [Vertica] support alter access policy statement.

+ Java version 1.8.4.0(2017-03-03)
  - [Openedge] support select and create view statement.


+ Java version 1.8.3.2(2017-02-22)
  - [Oracle] fix a bug for method call.
  
+ Java version 1.8.3.1(2017-02-17)
 - [general] Able to get location of output column in create table statement from subquery.
 - [Oracle] support method call after the double set of parenthesis
 - [Oracle] support  multiple DROP clauses in the ALTER TABLE statement
 - [Oracle] support multiple SET clauses in alter session statement.
 - [Vertica] able to recognize copy and show statement.
 - [Vertica] support DATETIME keyword used as column name.
 - [Vertica] fix a bug can't parse query when greatest/least used as column name.            
 - [Vertica] support on commit delete/preserve rows clause in create table.
 - [Teradata] Support first_value/last_value function. 
 - [Hive] Support column list in insert statement.


+ Java version 1.8.3.1(2017-02-16)
 - [Impala] support not like predicate
 - [ODBC] support operator =>, =<                                   
 - [ODBC] fix a bug can't parse column*-.01                   
 - [ODBC] support Interval Escape Sequences: {INTERVAL '1' DAY}	
 - [ODBC] fix a bug can't parse qualified name when ‘IS’ is followed by dot.	
 - [ODBC] fix a bug PRINT/SAVE keyword can't be column alias



+ Java version 1.8.3.0(2017-01-30)
 - [vertica] start to support vertica.

+ Java version 1.8.2.4(2017-01-25)
 - [PostgreSQL, Vertica] Able to get datatype from a datatype cast:  FLOAT '123.5' by using TConstant.getCastType()
 - [Teradata] fix a bug treat current_timestampm as column name.

+ Java version 1.8.2.4(2017-01-24)
 - [general] Able to link column alias in subquery of create table statement to created table.

+ Java version 1.8.2.4(2017-01-19)
 - [impala] support string literal used in column alias

+ Java version 1.8.2.4(2017-01-17)
 - [Vertica] start to add support for vertica


+ Java version 1.8.2.3(2017-01-13)
 - [General] fix a bug link qualified column in subquery to table in the same level incorrectly.
 
+ Java version 1.8.2.2(2017-01-13)
 - [Teradata] support multiple add column clause in alter table statement.
 - [greenplum] support cte in create table statement.  
  
+ Java version 1.8.2.1(2016-12-09)
 - [Teradata] support minute(4) to second syntax
 - [Teradata] support not cs data attribute.
 - [Teradata] fix a bug can't handle data type specifiers after current_timestamp function.
		
+ Java version 1.8.2.1(2016-12-08)
 - [Teradata] support variable with quotation marks, :"Name Surname" 
 - [Teradata] fix a bug treat current_date/current_time as column name.


+ Java version 1.8.2.0(2016-11-30)
  - [MySQL] support TimestampAttrs after null constraint 
  - [MySQL] support asc/desc keyword in index column in add primary/forgeign/unique key clause.
  
  
+ Java version 1.8.1.9(2016-11-18)
 - [MySQL] Fix a bug can't handle placeholder "?" in condition: department_id !=?
 - [MySQL] Able to regonize show full processlist statement.

+ Java version 1.8.1.7(2016-11-11)
 - [SQL Server] support content/document clause of xml datatype in create table statement.

+ Java version 1.8.1.7(2016-11-10)
 - [Teradata] support parenthesis around datatype in create macro parameter.
 - [Teradata] support data attribute after string; 
 - [Teradata] support comma between datatype and data attributes.

+ Java version 1.8.1.7(2016-11-09)
 - [Mdx] Partially support alter cube statement. 
 - [Dax] fix a bug can't handle expression when = operator at the begin of line.            
 - [Teradata] support data attribute in between condition.
 
+ Java version 1.8.1.6(2016-11-04)
 - [toXML] Able to parse DDL statements of EXECUTE IMMEDIATE.
 - [Oracle] support virtual column definition in create table statement.
 - [SQL Server] support create [primary] xml index statement

+ Java version 1.8.1.6(2016-11-03)
 - [Oracle] support read only/read write clause in alter table statement. 
 - [Oracle] support EDITIONABLE/NONEDITIONABLE/RW_EDITIONING keyword in create view statement.
 - [Oracle] support nopartition clause in create sequence.	
 - [Oracle] Able to regonize create [bigfile|smallfile] temporary/undo tablespace statement.

+ Java version 1.8.1.6(2016-11-02)
 - [General] fix a bug can't fetch join information correctly when processing: cross join table1 left join table2 on condition


+ Java version 1.8.1.5(2016-11-01)
 - [MySQL] fix a bug that getTableColumn treat "X" as a column name.

+ Java version 1.8.1.4(2016-10-31)
 - [mdx] support with measure clause in select statment.
 - [mdx] support create measure statement and support dax expression in this statement.


+ Java version 1.8.1.3(2016-10-28)
 - [Oracle/getTableColumn] fix a bug treat bind variable as column.            
 - [Hana] Fix a bug can't parse count( column_name )

+ Java version 1.8.1.3(2016-10-26)
 - [Teradata] support begin/end transaction.
 - [Teradata] Rename TTeradataEndTransaction to TEndTran, move from gudusoft.gsqlparser.stmt.teradata to gudusoft.gsqlparser.stmt
 - [General] Rename TMssqlBeginTran to TBeginTran, move from gudusoft.gsqlparser.stmt.mssql to gudusoft.gsqlparser.stmt
 - [General] Rename TMssqlBeginTranSqlNode to TBeginTranSqlNode, move from gudusoft.gsqlparser.nodes.mssql to gudusoft.gsqlparser.nodes

+ Java version 1.8.1.2(2016-10-21)
 -[Teradata] fix a bug can't match table when prefixed with schema name while building relationship between table and column.


+ Java version 1.8.1.2(2016-10-19)
 - [General] add method TCustomSqlStatement.getTables()  TCustomSqlStatement.getJoins() which is more consistent to get tables and joins from statement.
 - [Hive] support CTE in select statement/create view/create table/insert.	 
 - [Teradata] link column to table correctly if it comes from a subquery prefixed with alias of subquery.


+ Java version 1.8.1.1(2016-10-13)
 - [Teradata] support syntax like this: New address().street('df')
 - [Teradata] fix a bug cast execute statement to TMssqlExecute instead of TTeradataExecute                
 - [Teradata] fix a bug missing lock statement inside block.               
 - [Teradata] Able to fetch table and column only shown in where clause. 
 - [Teradata] support multiple locking table queries

+ Java version 1.8.1.0(2016-10-12)
 - [DAX] fully support DAX syntax.
 
+ Java version 1.8.0.1(2016-09-30)
 - [Teradata] Able to fetch table kind in create table, introduce new property: EnumSet<ETableKind> getTableKinds() in TCreateTableSqlStatement
 - [Teradata] support create macro statement.
 
+ Java version 1.8.0.1(2016-09-20)
 - [Oracle] support physical properties before select statement in create table.
 - [Oracle] support options in CREATE MATERIALIZED VIEW statement.

+ Java version 1.8.0.0(2016-09-12)
 - [hana] support select statement.
 - [SQL Server] move gudusoft.gsqlparser.nodes.mssql.TQueryHint to gudusoft.gsqlparser.nodes.TQueryHint
 - [SQL Server] move gudusoft.gsqlparser.nodes.mssql.EQueryHint to  gudusoft.gsqlparser.EQueryHint

 
+ Java version 1.7.3.5(2016-09-01)
 - [SQL Server] support with table option in create table statement.
 - [SQL Server] fix a bug can't parse switch to clause with only target partition. 
 - [Teradata] support variable name in qualified format.
 - [Teradata] support SQL	SECURITY INVOKER clause in create procedure
 - [SQL Server] support with xmlnamespaces	
 - [DB2] fix a bug TYPE keyword can't be column name in unique constraint.
 - [Oracle] pipelined clause can appears between parallel_enable clause and deterministic clause.
 - [Teradata] support substring syntax like this: substring(str_expr, from_expr, for_expr)

+ Java version 1.7.3.5(2016-08-31)
 - [toXML] support substring function.
 - [netezza] reform the class strucutre of substring function
 - [general] fix a bug can't match same table between quoted and non-quoted name.
 - [Oracle] offset keyword can be used as table/column name.
 - [Oracle] able to parse pipelined clause and parallel_enable clause with arbitary order in create function.  
 - [Oracle] fix a bug can't handle string operand in concatetation expression in using clause
 

+ Java version 1.7.3.4(2016-08-30)
 - [Teradata] support syntax like this: student.Last_name('Tamura').First_name('Natsuki')

+ Java version 1.7.3.3(2016-08-19)
 - [toXML] support create materialize view statement
 - [SQL Server, toXML] support null/not null clause in create type statement.
 
+ Java version 1.7.3.3(2016-08-18)
 - [SQL Server] support create xml schema collection statement.
 - [Teradata] able to fetch distinct clause.
 - [general] add enum: EUniqueRowFilterType, add TSelectDistinct.getUniqueRowFilter()

+ Java version 1.7.3.3(2016-08-17)
 - [toXML] support view attribute: WITH SCHEMABINDING in create view statement.
 - [toXML] list subquery in create table statement.
 - [Oralce] fix a bug can't regonize concatenation operator after float number.
 - [Oracle] support truncate partition clause in alter table.
 - [Oracle] SUPPLEMENTAL can be used as column name


+ Java version 1.7.3.3(2016-08-16)
 - [Oracle] fix a bug can't handle / correctly after create function aggregate using implementation type
 - [Oracle] support flashback archive clause in alter table.
 - [Oracle] able to regonize compound trigger body during getting raw statement.
 - [SQL Server] support table hint in merge statement.
 - [SQL Server] fix a bug can't fetch subquery inside declare variable.
          

+ Java version 1.7.3.3(2016-08-15)
 - [Oracle] fix a bug can't regonize sqlplus command after sql statement without a semicolon but separated by a blank line.

+ Java version 1.7.3.3(2016-08-12)
 - [MySQL] fix a bug can't parse comment clause appears before change column clause in alter tabble
 - [Oracle] support drop/reuse storage clause in truncate table


+ Java version 1.7.3.2(2016-08-11)
 - [Teradata] fix a NullPointerException while parsing elseif statement
 - [PostgreSQL/Redshift/Greenplum] support modulo "%" operator


+ Java version 1.7.3.1(2016-07-21)
 - [PostgreSQL/Redshift] support with clause of select statement which is used in insert statement.


+ Java version 1.7.3.0(2016-07-20)
 - [XML demo] particially support plsql create trigger statement in xml demo. 
 - [XML demo] support Oracle comment on statement. 
 - [Oracle/plsql] support new keyword in create trigger statement.
 - [Oracle/plsql] support treat function in plsql code.
 - [sql server] fix a bug can't recognize value keyword used in qualified name
 - [redshift] support qualified table name in drop table statement.


+ Java version 1.7.3.0(2016-07-18)
 - [Postgresql/Greenplum] support WITH clause of select in create view statement.


+ Java version 1.7.2.9(2016-06-29)
 - [Postgresql] support LIKE predicate in select list.
 - [SQL Server] support parse, try_parse, percentile_cont and percentile_disc function.
 

+ Java version 1.7.2.8(2016-06-22)
 - [general] move TBaseType.setTokenToIdentifier() to TExpression.setTokenToIdentifier()
 - [SQL Server] support call target expression in function call, new class: TExpressionCallTarget, new method: TFunctionCall.getCallTarget()


+ Java version 1.7.2.8(2016-06-20)
 - [Teradata] support block statement with label name.		
 - [Teradata] support loop statement.
 - [Teradata] support leave statement.
 - [Teradata] support for statement.
 - [Oracle] "PRIMARY" can be used as table/column name.


+ Java version 1.7.2.7(2016-06-17)
 - [General]  add new method: TCreateIndexSqlStatement.setColumnNameList/setTableName
 - [Teradata] add suppport for repeat statement.
 - [Teradata] add suppport for if statement.
 - [Teradata] add support for close/open/fetch cursor.
 - [Teradata] support label name in compound statement.
 - [PostgreSQL,Greenplum] support is distinct from predict without left side condition in case expression.
 - [Oracle] supported object dot-notation references max to 10 nested level.
 - [PostgreSQL] support logical condition in select list


+ Java version 1.7.2.7(2016-06-14)
 - [MDX] add some testcase to illustrate how to get function arguments.


+ Java version 1.7.2.7(2016-06-07)
 - [toXML] support oracle create type statement.
 - [PostgreSQL] support drop table statement.
 
+ Java version 1.7.2.6(2016-06-06)
 - [Oracle] support FORCE keyword in create type statement	
 - [Oracle] fix a bug can't parse CREATE OR REPLACE FUNCTION ... as Language JAVA NAME  and other sql statement without separated by / 
 - [Redshift] fix a bug can't process 3 part qualified name in redshift. 
 
+ Java version 1.7.2.6(2016-06-03)
 - [SQL Server] add new method: TCreateIndexSqlStatement.setFilegroupOrPartitionSchemeName/getFilegroupOrPartitionSchemeName/setPartitionSchemeColumns/getPartitionSchemeColumns/setIncludeColumns/getIncludeColumns/setFilterPredicate/getFilterPredicate
 - [SQL Server] add new method: TMssqlRevert.setCookie/getCookie
 - [SQL Server] add new method: TMssqlExecuteAs.setExecuteAsOption/getExecuteAsOption/setCookie/getCookie/setUserName/getUserName/setNoRevert/isNoRevert
 - [SQL Server] add new method: TMssqlCreateFunction.getProcedureOptions(), TMssqlCreateFunction.setProcedureOptions()
 - [SQL Server] add new method: TMssqlCreateProcedure.getProcedureOptions(), TMssqlCreateProcedure.setProcedureOptions()
 - [SQL Server] add new enum: EExecuteAsOption, EProcedureOptionType. add new class: TExecuteAsClause, TProcedureOption
 - [SQL Server] add new method: TMssqlCreateProcedure.isForReplication()

+ Java version 1.7.2.5(2016-05-30)
 - [toXML demo] fix a bug detect schema name incorrectly in create schema statement.           
 - [toXML demo] fix a issue of NullPointerException when process continue statement.
 
+ Java version 1.7.2.5(2016-05-27)
 - [General] TExecParameterList supports visitor.
 - [SQL Server] add new field to TMssqlCreateTrigger: ETriggerTimingPoint timingPoint which replace field: fireMode and EnumSet <ETriggerDmlType> dmlTypes which replace field: dmlTpyes;
 - [SQL Server] add new enum: ETriggerTimingPoint, ETriggerDmlType
 
+ Java version 1.7.2.4(2016-05-25)
 - [SQL Server] support create type statement.

+ Java version 1.7.2.4(2016-05-24)
 - [Oracle] fix a bug can't parse "language java name" inside create package body.
 - [MySQL] support limit clause in union set
 - [MySQL] fix a bug can't parse case statement when case used after end keyword.
 - [MySQL] support execute statement
 - [MySQL] support string like this: b'0'
 - [MySQL] support charset clause


+ Java version 1.7.2.4(2016-05-23)
 - [MySQL] support index option in alter table.
 - [MySQL] support comment after add index clause of alter table statement.	
 - [MySQL] support ASD/DESC keyword after colum name in add index clause of alter table statement.
 

+ Java version 1.7.2.4(2016-05-20)
 - [MySQL] support comment after table constraint
 - [MySQL] able to parse timestamp attrs after not null constraint
 
+ Java version 1.7.2.3(2016-05-18)
 - [Oracle] There is no need to separate multi create type statements in one file using / command.

+ Java version 1.7.2.3(2016-05-17)
 - [Oralce] fix a cast exception when parse wrapped function.
 - [Oracle] fix a bug can't handle / correctly after create function as language statement.
 
+ Java version 1.7.2.2(2016-05-13)
 - [Teradata] support Replace procedure statement.
 - [Teradata] support call statement. 
 - [Teradata] support create procedure without parameters.
 - [general] add new method TCreateIndexSqlStatement.setClustered, TCreateIndexSqlStatement.setNonClustered, TCreateIndexSqlStatement.isClustered and TCreateIndexSqlStatement.isNonClustered   
 - [general] add new method TCreateIndexSqlStatement.setIndexType(EIndexType indexType).


+ Java version 1.7.2.2(2016-05-11)
 - [Oracle] support qualified name with 5 parts.

 
+ Java version 1.7.2.2(2016-05-10)
 - [MySQL] fully support group_concat function.
 
+ Java version 1.7.2.1(2016-05-09)
 - [general] add set method for properties of all nodes which will be used in scriptWriter demo.
 - [SQL Server] fix a null exception error while parsing create synonym statement inside stored procedure.
               

+ Java version 1.7.2.1(2016-05-05)
 - [Oracle] support in/out keyword in constructor declaration in create type body statement.
 - [Teradata] Fix a bug TInsertSqlStatement.toString return null when insert statement inside a stored procedure.
 
+ Java version 1.7.2.0(2016-04-29)
 - [SQL Server] support switch to target_table clause in alter table statment.
 - [toXML] support execute statement in insert statement.
 - [toXML] support execute statement, create synonym statement, create trigger.
 
+ Java version 1.7.1.9(2016-04-26)
 - [Teradata] Fix a bug can't recognize sql statement inside BTEQ ".if" statement.
 - [Teradata] support create procedure statement.
 
+ Java version 1.7.1.8(2016-04-25)
 - [DB2] support number datatype
 - [DB2] support create global temporary table statement.
 - [Hive] fix a bug join clause toString() doesn't include first table.
 - [Hive] will rollup clause will not be included in group by clause's toString() output.
 - [Teradata] fix a bug can't parse named alias in between condition	 
 - [scriptWriter] support alter table statement.
 
+ Java version 1.7.1.7(2016-04-22)
 - [scriptWriter] improve scriptWriter to support create table, update. Add more sample code to illustrate how to use scriptWriter.

+ Java version 1.7.1.7(2016-04-20)
 - [toXML] support sql server go, create database, create schema, create procedure, create function statement.
 
+ Java version 1.7.1.6(2016-04-13)
 - [SQL Server] || are used as a concatenation operator was detect as a syntax error since the plus sign + is the only valid operator in SQL Server.
	

+ Java version 1.7.1.6(2016-04-12)
 - [Oralce] support in/out/in out keyword in using clause of open for statement.	
 - [Oralce] support case expression in open for using statement.
 - [Oracle] multiple method invocations bug fix.
 - [Oracle] support qualified name in limit clause of fetch statement.
 - [oracle] support '||' in USING clause of EXECUTE IMMEDIATE
 - [oracle] support supplemental log clause in create table statement.

+ Java version 1.7.1.6(2016-04-11)
 - [Teradata] support modify primary index in alter table statement.


+ Java version 1.7.1.6(2016-04-05)
 - [demo] toXML support oracle Hierarchical clause.


+ Java version 1.7.1.5(2016-03-30)
 - [MySQL] able to regonize SHOW FULL TABLES statement.
 - [MySQL] support syntax: VARCHAR(50) COLLATE utf8_bin
 - [MySQL] fix a bug can't handle TIME keyword when it used in column name.
 - [MySQL] fix a bug can't handle \\\\ inside quote like this: 'String with 5 slashes \\\\'
 - [MySQL] support limit clause before union keyword


+ Java version 1.7.1.5(2016-03-29)
 - [MySQL] support "set NAMES latin1" statement.
 - [MySQL] "#" character is start of a line comment, it can't be a character in identifier.

+ Java version 1.7.1.4(2016-03-28)
 - [general] toString() method reserve comment inside node. add new function TParseTreeNode.setIncludingComment(boolean), if you want to remove comment inside node,
 - [demo: TGetTableColumn] fix null exception when handle function derived table.

+ Java version 1.7.1.3(2016-03-25)
 - [demo: searchFunction] Use visitor pattern to find out all functions inside script.

+ Java version 1.7.1.3(2016-03-24)
 - [sybase] support create or replace procedure.
 - [sybase] support //(double slash) comment
 - [general]  class TCallStatement move from package gudusoft.gsqlparser.stmt.oracle to package gudusoft.gsqlparser.stmt


+ Java version 1.7.1.2(2016-03-23)
 - [Teradata] support execute macro statement
 - [impala] fix a bug can't parse order by clause after table in from clause directly without a table alias.

+ Java version 1.7.1.1(2016-03-14)
 - [General] Unify the structure of TPivotClause to support both Oracle and SQL Server	
 - [Teradata] support ROWS CURRENT ROW in partition by clause.
 
+ Java version 1.7.1.1(2016-03-14)
 - [General] Unify the structure of TPivotClause to support both Oracle and SQL Server	
 - [Teradata] support ROWS CURRENT ROW in partition by clause.


+ Java version 1.7.1.1(2016-03-11)
 - [DB2] fix a bug can't parse optimize for clause after isolation clause.
 - [teradata] support alter table drop columm, drop constraint
 - [teradata] nested comment is invalid in teradata


+ Java version 1.7.1.1(2016-03-10)
 - [Teredata] support CV (create view) keyword.
 - [Teredata] support drop join/hash index

+ Java version 1.7.1.0(2016-03-04)
 - [oracle] type of datatype: NATIONAL CHARACTER changed from nchar_t to ncharacter_t
 - [oracle] type of datatype: character changed from char_t to character_t
 - [oracle] type of datetype: integer changed from  int_t to integer_t
 - [oracle] type of datetype: decimail changed from dec_t to decimal_t
 - [general] add new EJoinType.join represents  join with inner prefixed.


+ Java version 1.7.0.9(2016-03-01)
 - [Oracle] fix a bug can't parse create database link statement correctly.
 
+ Java version 1.7.0.8(2016-02-18)
 - [general] add missing acceptChildern() method of class where accept() method already exists.
 - [DB2] support substring.
 - [toXML demo] support constructor function in create type body.
 
+ Java version 1.7.0.8(2016-02-17)
 - [toXML demo] support parameter mode, exception declaration

+ Java version 1.7.0.8(2016-02-16)
 - [Teradata] fix a bug can't parse interval qualifier like this: YEAR(4) TO MONTH
 - [MySQL] fix a bug can't parse consecutive ;(semicolon) after a single statement.
 
 
+ Java version 1.7.0.7(2016-02-14)
 - [general] toString() method doesn't include comment inside node anymore.
 - [oracle, plsql] support open cursor with parenthesis with no parameter.
 - [oracle, plsql] support plsql exponentiation operator
 - [general] add acceptChildren() method for TConstant
 - [plsql] remove rule: plsql_expression from lzyaccoracleplsql.y


+ Java version 1.7.0.6(2016-02-06)
 - [Hive] fix a bug can't recognize column name in syntax like schema.table.column

+ Java version 1.7.0.5(2016-01-28)
 - [General] fix a nullexception while setting string of table in create table statement.

+ Java version 1.7.0.4(2016-01-19)
 - [Oracle] fix a bug missing typeName of TPlsqlCreateTypeBody
 - [toXml] support plsql create type and create type body.
 - [Teradata] support at time zone 'GMT' clause of timestamp
 
 
+ Java version 1.7.0.4(2016-01-18)
 - [toXML] support drop table and truncate table statement.
 - [impala] fix a bug can't parse column list in insert statement
 - [impala] support values clause in insert statement
 
+ Java version 1.7.0.3(2016-01-11)
 - [impala] support offset clause in select statement
 - [Sybase] null exception while parse continue statement inside if statement.
 - [General] fix a bug doesn't set database, schema and object name correctly in ObjectName
   found in drop procedure, create index and reference table in create table statement.
   
+ Java version 1.7.0.2(2016-01-08)
 - [Impala] support insert overwrite statement without table keyword.

+ Java version 1.7.0.2(2016-01-06)
  - [Oralce] Able to get package name from wrapped package.                 

+ Java version 1.7.0.1(2015-12-29)
  - [toXml] add support for create package body.

+ Java version 1.7.0.1(2015-12-23)
  - [demos] fix a bug can't visit columns in case expression in demo columnInClause, by replacing accpet() with acceptChildren().

+ Java version 1.7.0.1(2015-12-22)
  - [toXml] support create index, create view, CTE in toXml demo.

+ Java version 1.7.0.0(2015-12-21)
  - [impala] support Impala SQL dialect when initalize a new sql parser instance with dbvimpala 

+ Java version 1.6.5.2(2015-12-21)
  - [Teradata] fix a bug can't parse (date) datatype conversion after number constant. select 999 (date) from t;

+ Java version 1.6.5.2(2015-12-18)
 - [DB2] fix bug TDb2HandlerDeclaration.toString() doesn't work.
 - [DB2] fix bug TInsertSqlStatement.toString() doesn't work when insert statement inside stored procedure.
 - [MySQL] fix a bug can't detect current_timestamp() in default constriant

+ Java version 1.6.5.2(2015-12-17)
 - [Teradata] fix a bug can't parse (date) datatype conversion after NULL. select NULL (date) from t;

+ Java version 1.6.5.1(2015-12-14)
 - [Teradata] fix bug can't handle (date) datatype conversion, since (date) is also a valid expression depends on context.
 - [Teradata] char can be used as function name

+ Java version 1.6.5.0(2015-12-11)
 - [SQL Server] add isClustered() method to TConstraint.

+ Java version 1.6.4.9(2015-12-10)
 - [general] TGroupByItem.getExprList() is replaced by getExpr() which is an expression with type list_t;

+ Java version 1.6.4.9(2015-12-09)
 - [General] TInsertSqlStatement.getValueType() replaced by TInsertSqlStatement.getInsertSource()
 - [General] add enum EInsertSource, represents source of insert value.

+ Java version 1.6.4.8(2015-12-02)
 - [Teradata] fix a bug can't parse DATETIME used as column name inside cast function.

+ Java version 1.6.4.8(2015-11-30)
 - [Teradata] fix a bug can't link column in analytic function after rank
 - [Teradata] Teradata parse error with <INTERVAL> <DateTime> TO <DateTime>

+ Java version 1.6.4.7(2015-11-26)
 - [Teradata] alble to get as table name in create table statement by using TCreateTableSqlStatement.getAsTable()

+ Java version 1.6.4.7(2015-11-25)
 - [general] add new method TSelectSqlStatement.getParenthesisCount() to easy check whether this select statement is parenthesised.


+ Java version 1.6.4.6(2015-11-24)
 - [DB2] able to parse create database statement.
 - [SQL Server] fix a bug can't parse query if there are two consecutive semicolons in the query
 - [SQL Server] support qualified column in the IN Clause of pivot/unpivot clause. 
 - [DB2] able to recognize create stogroup statement.

+ Java version 1.6.4.6(2015-11-23)
 - [SQL Server] support reconfigure statement.
 
 
+ Java version 1.6.4.5(2015-11-21)
 - [Teradata] fix a bug can't parse select (DATE)
 - [demo] add toXML2, not accomplished yet.

 
+ Java version 1.6.4.4(2015-11-19)
 - [Oracle] support more than one connect by clause in Hierarchical Queries, introduce new
 - [Oracle] fix a bug can't parse g_lookup_arr(p_lookup_type) (v_appln_idx).NEXT(v_meaning);
 - [DB2] fix a bug can't parse FETCH FIRST 10 ROWS
 - [Oracle] "NEW" can be used as column name.
 - [Oracle] support datatype: long raw (size) in variable declaration.

+ Java version 1.6.4.3(2015-11-17)
 - [DB2] fix a bug can't parse FETCH FIRST ROW ONLY clause

+ Java version 1.6.4.2(2015-11-13)
 - [demo] rewrite toXML demo to accommodate the change made to accept(TParseTreeVisitor v)
 - [general] add acceptChildren(TParseTreeVisitor v) to TParseTreeNode which will iterate all sub-nodes.
 		accept(TParseTreeVisitor v) doesn't iterate all sub-nodes anymore. Please use acceptChildren
 		insted of accept if you need to iterate all sub-nodes automatically.
 - [Teradata] support multiple strings directly followed by each other	 
 - [Oracle] fix a bug when parse XMLPI function. 
 - [sql server] support optimize for query hint

 
+ Java version 1.6.4.2(2015-11-12)
 - [sql server] fix a bug can't parse [order] as column name.
 - [sql server] support temporary table used as a target table in merge into 
 - [informix] support Substring Operator with only start position.
 - [general] add TPTNodeList <TPivotClause> pivotClauseList in TPivotedTable
 - [general] remove aliasClause from TPivotedTable, use aliasClause in TPivotClause instead.
 - [sql server/oracle] All tables can be fetched from TCustomSqlStatement.tables when pivot table is used in from clause.
 - [general] TCustomSqlStatement.getTargetTable().getTableType() is ETableSource.pivoted_table means it's a pivot table.
 - [sql server] fix a bug can't parse exec statement after insert if there is no semicolon after insert statement.

Java version 1.6.4.2(2015-11-09)
* [general] add new enum ESetOperatorType which stands for set operators: union, except, intersect and minus.
* [general] keywords/built-in function check for greenplum, redshift,hive and informix.


Java version 1.6.4.1(2015-11-06)
* [Get table/column] fix a bug can't recognize variable in for statement.

* [Teradata] all teradata statements accept visitor.
* [Sybase] all sybase statements accept visitor.
* [Redshift] all redshift statements accept visitor.
* [PostgreSQL] all PostgreSQL statements accept visitor.
* [Netezza] all Netezza statements accept visitor.
* [MySQL] all MySQL statements accept visitor.

Java version 1.6.4.1(2015-11-05)
* [SQL Server] all sql server statements accept visitor.
* [Informix] all informix statements accept visitor.
* [Hive] all hive statements accept visitor.
* [DB2] all db2 statements accept visitor.
* [Oracle] all oracle statements accept visitor.

Java version 1.6.4.1(2015-11-04)
* [general] TAlterTableStatement.getTableElementList() was deprecated, all option can be fetched from alterTableOptionList.
* [general] EAlterTableOptionType.AddTableConstraint was replaced by EAlterTableOptionType.AddConstraint

Java version 1.6.4.1(2015-11-03)
* [SQL Server] unify the API interface of  add column and add constraint in alter table statement.

Java version 1.6.4.1(2015-10-30)
* [SQL Server] support merge statement in from clause.

Java version 1.6.4.0(2015-10-27)
* [SQL Server] support CTE query in return statement.
* [general] able to check whether a function is a built-in function of database.  
  public boolean isBuiltIn(EDbVendor pDBVendor)

Java version 1.6.4.0(2015-10-22)
* [Table column] temporay table in into clause was pickuped as table.
* [into clause] all tables in into clause was organized as an expression list.
posgresql, greenplum, netezza, redshift

Java version 1.6.3.9(2015-10-19)
* [Doc] release gsp_for_java_developer_guide.pdf
* [Refactor] move back THierarchical from gudusoft.gsqlparser.nodes.oracle to gudusoft.gsqlparser.nodes because 
both oracle and informix use this clause.


Java version 1.6.3.8(2015-10-15)
* [DB2] fix a bug can't detect table/column inside IFEXISTS
* [Oracle] fix a bug subpartition keyword can't be used as column name and alias.

Java version 1.6.3.8(2015-10-15)
* [Refactor] move THierarchical from gudusoft.gsqlparser.nodes to gudusoft.gsqlparser.nodes.oracle


Java version 1.6.3.7(2015-10-08)
* [Refactor] move TTeradataStmtStubSqlNode from gudusoft.gsqlparser.stmt.teradata to gudusoft.gsqlparser.nodes.teradata
* [Refactor] move TExpandOnClause from gudusoft.gsqlparser.stmt.teradata to gudusoft.gsqlparser.nodes.teradata

Java version 1.6.3.7(2015-10-07)
* [Refactor] move TMySQLPrepareSqlNode from gudusoft.gsqlparser.stmt.mysql to gudusoft.gsqlparser.nodes.mysql
* [Refactor] replace TMssqlTruncateTable with TTruncateStatement
* [Refactor] move TMssqlSetSqlNode from gudusoft.gsqlparser.stmt.mssql to gudusoft.gsqlparser.nodes.mssql
* [Refactor] remove unused class: TMssqlDropIndex
* [Refactor] move TMssqlUpdateTextSqlNode from gudusoft.gsqlparser.stmt.mssql to gudusoft.gsqlparser.nodes.mssql
* [Refactor] move TMssqlStmtStubSqlNode from gudusoft.gsqlparser.stmt.mssql to gudusoft.gsqlparser.nodes.mssql
* [Refactor] move TMssqlSendOnConversationSqlNode from gudusoft.gsqlparser.stmt.mssql to gudusoft.gsqlparser.nodes.mssql
* [Refactor] move TMssqlRaiserrorSqlNode from gudusoft.gsqlparser.stmt.mssql to gudusoft.gsqlparser.nodes.mssql
* [Refactor] move TMssqlRevertSqlNode from gudusoft.gsqlparser.stmt.mssql to gudusoft.gsqlparser.nodes.mssql
* [Refactor] move TMssqlLabelSqlNode from gudusoft.gsqlparser.stmt.mssql to gudusoft.gsqlparser.nodes.mssql
* [Refactor] move TMssqlGotoSqlNode from gudusoft.gsqlparser.stmt.mssql to gudusoft.gsqlparser.nodes.mssql
* [Refactor] move TMssqlEndConversationSqlNode from gudusoft.gsqlparser.stmt.mssql to gudusoft.gsqlparser.nodes.mssql
* [Refactor] move TMssqlDeallocateSqlNode from gudusoft.gsqlparser.stmt.mssql to gudusoft.gsqlparser.nodes.mssql
* [Refactor] move TMssqlCreateTriggerUpdateColumnList from gudusoft.gsqlparser.stmt.mssql to gudusoft.gsqlparser.nodes.mssql
* [Refactor] move TMssqlCreateTriggerUpdateColumn from gudusoft.gsqlparser.stmt.mssql to gudusoft.gsqlparser.nodes.mssql
* [Refactor] move TMssqlBulkInsertSqlNode from gudusoft.gsqlparser.stmt.mssql to gudusoft.gsqlparser.nodes.mssql
* [Refactor] move TMssqlBeginTranSqlNode from gudusoft.gsqlparser.stmt.mssql to gudusoft.gsqlparser.nodes.mssql
* [Refactor] move TMssqlBeginDialogSqlNode from gudusoft.gsqlparser.stmt.mssql to gudusoft.gsqlparser.nodes.mssql

Java version 1.6.3.7(2015-10-06)
* [Javadoc] ESqlStatement, EDbVendor
* [Refactor] rename sstplsql_returnstmt to sst_returnstmt
* [Refactor] rename sstplsql_raisestmt to sst_raisestmt
* [Refactor] rename sstplsql_openstmt to sst_openstmt
* [Refactor] rename sstplsql_openforstmt to sst_openforstmt
* [Refactor] rename sstplsql_loopstmt to sst_loopstmt
* [Refactor] delete TLabeledStmt
* [Refactor] rename sstplsql_ifstmt to sst_ifstmt
* [Refactor] rename sstplsql_fetchstmt to sst_fetchstmt
* [Refactor] rename  sstplsql_exitstmt to sst_exitstmt
* [Refactor] rename sstplsql_elsifstmt to sst_elsifstmt
* [Refactor] rename sstdropsequencestmt to sstdropsequence
* [Refactor] rename sstplsql_cursordecl to sst_cursordecl
* [Refactor] replace sstoraclecreatematerializedview with sstcreatematerializedview
* [Refactor] rename sstoraclestoredprocedurestmt to sst_storedprocedurestmt
* [Refactor] rename sstplsql_block to sst_block
* [Refactor] rename sstplsql_closestmt to sst_closestmt
* [Refactor] rename sstplsql_casestmt to sst_casestmt
* [Refactor] move gudusoft.gsqlparser.stmt.TBasicStmt to gudusoft.gsqlparser.stmt.oracle.TBasicStmt
* [Refactor] rename sstplsql_assignstmt to sst_assignstmt which is used in both Oracle and postgresql
* [Hive] remove TAlterViewStmt, use TAlterViewStatement instead.

Java version 1.6.3.6(2015-09-30)
* [Demo] imporove columnsInResultColumn demo to support nested subquery.
* [Teradata] support create index with index parameters followd index name directly.

Java version 1.6.3.5(2015-09-28)
* [SQL Server] fix a bug can't parse merge statement inside stored procedure if no semicolon 
* [DB2] fix a bug can't parse single line comment end with @ inside stored procedure

Java version 1.6.3.4(2015-09-22)
* [general] fix a bug that TObjectName.getColumnToken() return null when objectname is
* [general] Add new enum value: insertColumn, setValue to ESqlClause to make it more clearly 


Java version 1.6.3.3(2015-09-18)
* [general] move TAlterViewStmt from package gudusoft.gsqlparser; to package gudusoft.gsqlparser.stmt;

Java version 1.6.3.3(2015-09-17)
* [Teradata] fix a bug in generated_clause.
* [Teradata] allow not null constraint before character set in column definition.

Java version 1.6.3.2(2015-09-16)
* [Oracle] support SUBPARTITION FOR clause in from clause.
* [Oracle] support expression list in query partition clause
* [SQL Server] support  SCHEMA :: schema_name in grant statement.
* [SQL Server] fix a bug can't parse REF schema name in qualified datatype
* [SQL Server] fix a bug can't parse LEFT MERGE JOIN.


Java version 1.6.3.2(2015-09-15)
* [Oracle] support XMLPI function.
* [Teradata] support replace recursive view statement
* [Oracle] support bequeath clause in create view statement.
* [Oracle] support trigger_edition_clause
* [Oracle] support enable/disable keyword in simple_dml_trigger.
* [Oracle] support only table clause in delete/update statement.
* [Oracle] support VISIBLE/INVISIBLE clause in create view statement
* [Oracle] able to parse row_pattern_clause
* [Oracle] support cross/outer apply.

Java version 1.6.3.1(2015-09-14)
* [DB2] lock table support in stored procedure.
* [SQL Server] supprot try_cast function.
* [Teradata] support syntax like this: 1 NOT > 2


Java version 1.6.3.1(2015-09-11)
* [Oracle] get table column missing column in translate function.

Java version 1.6.3.0(2015-09-09)
* [Oracle] support XMLType_view_clause in create view statement.
* [Oracle] support object_view_clause in create view statement
* [Oracle] support create table of object name with detailed object infomation.
* [Oracle] support overriding keyword in create type and create type body statement.
* [Oracle] support create type with only OID.
* [Oracle] support execute function without parameter.
* [MySQL] support use database statement.
* [MSSQL] rename TMssqlUse to TUseDatabase and move from package gudusoft.gsqlparser.stmt.mssql to gudusoft.gsqlparser.stmt;

Java version 1.6.2.6(2015-09-08)
* [MySQL] support select into statement without from clause.
* [MySQL] support definer option in create view.  	
* [MySQL] fix a bug can't handle delimiter ;; correctly.
* [SQL Server] fix a bug can't process datatype enclosed with brackets correclty. [nvarchar](50)


Java version 1.6.2.5(2015-09-08)
* [Sybase] support merge partition clause in alter table.
* [Sybase] treat { and } as a single token.
* [sybase] support location cause in insert statment.


Java version 1.6.2.5(2015-09-02)
* [MySQL] support dumpfile and outfile in into clause.
* [MySQL] able to get charset name from column definition and table option. 
* [MySQL] support ON UPDATE CURRENT_TIMESTAMP clause in column definitions
* [Hive] able to parse insert statement when TABLE keyword is missing.

Java version 1.6.2.4(2015-08-28)
* [DB2] fix a bug can't parse set clause of update statement if single column is surrounded by parenthesis.
* [Oracle] use TPivotedTable to represent pivot table in from clause.

Java version 1.6.2.4(2015-08-27)
* [SQL Server] enhanced to support multiple pivoted table, introduce new class: TPivotedTable

Java version 1.6.2.3(2015-08-26)
* [General] fix a bug when parse :setvar in SQL Server scripts.

Java version 1.6.2.3(2015-08-25)
* [General] fix a bug in searchColumnInResultSet() when parse multiple select statement in CTE.


Java version 1.6.2.2(2015-08-21)
* [MySQL] able to recognize lock tables, unlock tables.
* [MySQL] fix a bug can't parse unicode string like: _ucs2 x'2018'
* [Teradata] Support where clause after order by clause in select statement.
* [General] Enhance accept() method in TCaseExpression, so visitor can iterate all elements in case expr.
* [demo] Enhance columnsInResultColumn to support case expr.

Java version 1.6.2.1(2015-08-18)
* [Oracle] fix a bug schema.tablename doesn't parse correctly in comment on statement

Java version 1.6.2.0(2015-08-06)
* [Redshift] support column alias like [ntile].

Java version 1.6.1.9(2015-07-30)
* [Redshift] support CTE(with clause select) in create table statement.

Java version 1.6.1.8(2015-07-29)
* [Redshift] support all Window Functions.

Java version 1.6.1.7(2015-07-28)
* [Redshift] support create table when column attribute and column constraint's 
   position not comply with sql syntax in official document.
* [Redshift] support copy statement when parameters occurs before CREDENTIALS clause
  which is not comply with sql syntax in official document.
  
Java version 1.6.1.6(2015-07-25)
* [Redshift] support lag function.
* [Redshift] support Nested WITH expressions.

Java version 1.6.1.5(2015-07-24)
* [Redshift] non-reserved keywords can be column name.

Java version 1.6.1.5(2015-07-23)
* [Teradata] fix a bug can't parse DAY(4) TO SECOND(0)
* [General]  TTable.getName() will return empty string instead of raise null exception while  
* [Teradata] support contains operator.

Java version 1.6.1.4(2015-07-16)
* [General] fix a bug raise NullPointerException if input sql is empty.
* [Redshift] support substring function.
* [Redshift] support timestamp without time zone.
* [Redshift] support double precision data type.
* [Redshift] support PERCENTILE_DISC Window Function.
* [Redshift] Fix bugs while parsing Window Function.
* [Redshift] support extract function.
* [MySQL] fix a bug can't parse empty comment like this /**/                                               
* [demos] add tableColumnRename demo under demos\gettablecolumns

Java version 1.6.1.3(2015-07-09)
* [Teradata] support NO FALLBACK clause in create table statement while select query is used.


Java version 1.6.1.2(2015-07-08)
* [Redshift] fix nullexception error while init redshift parser.
* [Teradata] fix a bug can't parse CREATE TABLE ... AS statement.
* [Oracle] support PARTITION FOR in partition_extension_clause.

Java version 1.6.1.1(2015-07-07)
* [SQL Server/sql formatter] fix a bug when format sql server merge statement
* [Oracle/PLSQL] able to get language, declaration and libname from call spec.
* [Oracle/PLSQL] support accessible_by_clause in create function/procedure

Java version 1.6.1.1(2015-07-03)
* [Oracle] support editionable/noneditionable keyword in create function/procedure/package/package body
* [Oracle] support RETURNING BULK COLLECT INTO in EXECUTE IMMEDIATE statement.
* [MySQL] Able to parse STRAIGHT_JOIN without join condition
* [Teradata] fix a bug can't parse IS IN condition
* [Teradata] support number like this: 8.0001E 04
* [SQL Server] fix a bug can't parse collate in between expression.


Java version 1.6.1.1(2015-07-03)
* [redshift] add support for copy/unload statement.
* [MySQL] fix a bug new table name not set correctly in alter table rename statement.

Java version 1.6.1.1(2015-07-02)
* [DB2] support get diagnostics inside stored procedure.
* [DB2] support decalre global temporary table inside stored procedure.
* [DB2] support create index inside stored procedure.

Java version 1.6.1.0(2015-06-29)
* [redshift] support grant/insert/lock/prepare/reset/revoke/rollback/select/set/truncate/update

Java version 1.6.1.0(2015-06-23)
* [MySQL] support table options in alter table statement.
* [MySQL] support add key clause in alter table.
* [MySQL] fix a bug when set default value is integer in alter column

Java version 1.6.1.0(2015-06-21)
* [MySQL] support Character String Literal Character Set
* [MySQL] support signal statement, TMySQLSignal.
* [MySQL] support begin statement;
* [MySQL] support join clause in delete statement(Multiple-Table Syntax)
* [redshift] support drop group/schema/table/user/view, end, execute, explain, fetch statement.
* [general] move TExplainPlan from package gudusoft.gsqlparser.stmt.oracle; to package gudusoft.gsqlparser.stmt;
						chang statement type from sstoracleexplainplan to sstExplain.
						TExplainPlan used in Oracle and redshit.
						
Java version 1.6.0.9(2015-06-19)
* [redshift] support create user/view, deallocate, delete, drop database.


Java version 1.6.0.9(2015-06-18)
* [redshift] support create database/group/schema/table.
* [MySQL] fix a bug can't parse table constraint when this is no constraint name after keyword CONSTRAINT

Java version 1.6.0.8(2015-06-16)
* [redshift] support alter table/user, analyze, begin, cancel, close

Java version 1.6.0.8(2015-06-15)
* [Teradata] fix a bug can't parse in condition when there is no parenthesis around expression.


Java version 1.6.0.7(2015-06-09)
* [Teradata] fix a bug can't parse ^< operator                                   
* [MySQL] fix a bug when date used as column name.

Java version 1.6.0.6(2015-06-08)
* [redshift] add all commands in lzdbcmds

Java version 1.6.0.6(2015-06-03)
* [Oracle] support chained function in  call statement.
* [DB2] Fix a bug can't parse insert clause in merge statement if there is no insert column list specified.
* [MySQL] MySQL doesn't support table alias in insert statement.


Java version 1.6.0.6(2015-06-02)
* [Oracle] support add partition in alter table

Java version 1.6.0.5(2015-05-29)
* [General] fix a bug remove space before newline which makes sql not exactly the same as origin text.

Java version 1.6.0.4(2015-05-28)
* [MySQL] fix a bug can't parse identifier followed by delimiter without space like:  select 1$$, here $$ is delimiter.

Java version 1.6.0.3(2015-05-22)
* [Oracle] support fetch first/next clause.
* [Oracle] support offset clause.

* [MySQL] fix a bug can't tokenize >= correctly.                       		                          
* [Teradata] fix a bug can't process hex literal start with lowercase 'x'

Java version 1.6.0.3(2015-05-21)
* [TGetTableColumn demo] illustrates how to get table effect type and location of column.
* [general] fix a bug can't detect table in foreign key constraint

Java version 1.6.0.2(2015-05-19)
* [table/column] missing source table when link column to table in linkToFirstTable function.
* [visitor] able to process visitor when function type is unknown_t in TFunctionCall                
* [demos] traceColumn demo

Java version 1.6.0.1(2015-04-30)
* [getTableColumn] if table alias is used in update statement, old algorithm to
get table column is not correct, use new get table column algorithm instead.
* [Oracle] fix a bug can't parse qualifiedName1.Name2.delete; inside plsql block

Java version 1.6.0.0(2015-04-29)
* [SQL Server] Fix a bug can't get text of alter database statement.

Java version 1.6.0.0(2015-04-28)
* [general] introduce new algorithm to get table and column in query.
* [MySQL] fully support drop index statement.
* [Oracle] fix a bug can't parse sql when log is a table alias.      

Java version 1.5.4.2(2015-04-22)
* [demo] add class myMetaDB implements IMetaDatabase to demo

Java version 1.5.4.2(2015-04-22)
* [Oracle] fix a bug can't parse case statement inside plsql.

Java version 1.5.4.1(2015-04-03)
* [general] static parser table is keep, while  release memory allocated by flexer.yystack,flexer.yytextbuf,flexer.buf in TGSqlParser.freeParseTable()


Java version 1.5.4.0(2015-03-18)
* [general] release memory allocated by flexer.yystack,flexer.yytextbuf,flexer.buf in TGSqlParser.freeParseTable()


Java version 1.5.3.9(2015-03-13)
* [general] release mysql parser table in TGSqlParser.freeParseTable()

Java version 1.5.3.8(2015-03-02)
* [general] add TGSqlParser.freeParseTable() which can be used to free memory of parse table after parse query.

Java version 1.5.3.8(2015-02-27)
* [Oracle] add support for error_logging_clause
* [MySQL] support load data local infile
* [DB2] support variable with hypen character inside like this: :xx-xxx-xxxx-xx

Java version 1.5.3.8(2015-02-27)
* [Netezza] Fix NullPointerException when parse position function.
* [Oracle] fix a bug can't parse case statement if ending with a label.            
* [MySQL] fix a bug can't parse not equal operator in select list.
* [Oracle] fix a bug cannot parse the collection method call when it has parents more than two
* [SQL Server] fix NullPointerException when more than one CTE in CTEList

Java version 1.5.3.7(2015-02-21)
* [MySQL] fix a bug can't parse timestamp(precision)

Java version 1.5.3.7(2015-02-21)
* [DB2] support minus operator

Java version 1.5.3.7(2015-02-17)
* [Oracle] support INDEX BY {PLS_INTEGER | BINARY_INTEGER | {VARCHAR2 | VARCHAR | STRING} (v_size) | LONG | type_attribute | rowtype_attribute}
		datatype of the indexes since Oracle 12c
* [MySQL] fix a bug can't parse user defined DELIMITER correctly
* [Teredata] support day() to hour syntax
* [Oralce] add TKeepDenseRankClause.getFirstLast() function to distinguish first and last function
* [Oralce] publish order by clause in TKeepDenseRankClause
* [Oracle] add support for three TRANSLATE function parameters

Java version 1.5.3.6(2015-01-26)
* [PostgreSQL] Fix a bug can't detect column used in json operators.


Java version 1.5.3.5(2015-01-21)
* [Oracle] fix a bug that table alias "new" causes parsing error


Java version 1.5.3.5(2015-01-20)
* [SQL Server] Able to regonize receive statement inside block.
* [SQL Server] fix a bug can't parse create queue statement in EXECUTE AS keyword in this statement.
* [MySQL] fix a bug can't parse mysql query with single row comment symbol "#" and no space after it
* [Netezza] support drop schema
* [Oracle] support follows trigger clause in create trigger statement.
* [Oracle] support passing clause in XMLexists function
* [Oracle] support accessiable by clause.
* [Oracle] support continue statement of pl/sql
* [Oracle] fix a bug can't parse with context clause in c_declaration of call spec
* [Oracle] Fix a bug of TCallSpec.getLang() Returns Wrong Value of C lang

Java version 1.5.3.4(2015-01-16)
* [PostgreSQL] support json operators: ->, ->>, #>, #>>, @>, <@, ?, ?|, ?&
* [PostgreSQL] add new datatype: json and jsonb

Java version 1.5.3.3(2014-12-18)
* [SQL Server] support on database/all server option of drop trigger statement
* [SQL Server] fully support grant permission in grant statement.
* [SQL Server] support where clause in create index statement.
* [SQL Server] support event_type | event_group in create trigger on database statement
* [SQL Server] support with check option in alter table...check constraint
* [SQL Server] fix a bug can't parse update clause in not matched clause of merge statement
* [SQL Server] fix a null exception bug while parsing drop sequence statement in IF statement.


Java version 1.5.3.2(2014-12-11)
* [DB2] The keywords NEXTVAL and PREVVAL can be used as alternatives for NEXT VALUE and PREVIOUS VALUE respectively.

Java version 1.5.3.2(2014-12-09)
* [DB2] fix a bug can't parse IF/LOOP statement inside stored procedure
* [General] first argument in XMLELEMENT function is saved in XMLElementNameExpr instead of the first argument in args.
* [General] rename TFunctionCall.getValueExprList()  to getXMLElementValueExprList()

Java version 1.5.3.2(2014-12-08)
* [Oracle] Able to get value expr for XMLSERIALIZE function using: TFunctionCall.getExpr1() 
* [Oracle] Able to get value expr for XMLROOT function using: TFunctionCall.getExpr1() 
* [Oracle] Able to get value expr list for XMLFOREST function using: TFunctionCall.getXmlForestValueList() 
* [Teradata] support insert into tname.* syntax which is used in MultiLoad scripts

Java version 1.5.3.1(2014-11-28)
* [Oracle] support CTE in insert statement
* [Teradata] fix a bug can't parse expression with alias clause when compare a list of expressions with a subquery 

Java version 1.5.3.0(2014-11-11)
* [Sybase] add support for delete statistics statement
* [Sybase] add support for writetext statement
* [Sybase] support lock/with clause in select...into clause.
* [Sybase] fix a bug can't parse set identity_update stores_south on
* [Sybase] support Parallel Degree of query, prefetch clause.

Java version 1.5.3.0(2014-11-10)
* [general]  change TTableHint.hintIndex to hintValue
* [Teradata] Able to get detailed constraint information from alter table statement.
* [Teradata] fix a bug can't parse CREATE TABLE with GLOBAL TEMPORARY option
* [Oracle] fix a bug can't parse a procedure that ends with a label followed by execute immediate
* [Oracle] support inserts values into a table with a specified partition in INSERT ALL statement
* [Oracle] support merges into a table with a specified partition.
* [Oracle] support view as a target in MERGE.
* [Oracle] comment can't be nested.                       
* [Oracle] fix a bug parse qualified name in IN clause without brackets
* [Oracle] fix a bug while process quoted string.

Java version 1.5.2.9(2014-11-04)
* [Oracle] fix a bug "location" can't be alias name

Java version 1.5.2.9(2014-11-03)
* [general] fix offset error while parse sql multi times.     
* [Oracle] add support for flash_cache clause, cell_flash_cache clause

Java version 1.5.2.9(2014-10-31)
* [Oracle] fix a bug can't parse delete clause in merge statement

Java version 1.5.2.9(2014-10-30)
* [MySQL] support literal in column alias without AS keyword

Java version 1.5.2.8(2014-10-22)
* [netezza] fix a bug can't parse trim argument like this: BOTH FROM expr
* [Oracle] fix a bug can't parse INITIALLY IMMEDIATE clause in add constraint clause

Java version 1.5.2.7(2014-10-21)
* [SQL Server] fix a bug treat expression type comparison instead of assignment

Java version 1.5.2.7(2014-10-17)
* [SQL Server] able to get output clause from merge statement
* [SQL Server] add support for throw statement.

Java version 1.5.2.6(2014-10-14)
* [oracle/plsql] fix a bug that can't parse chained method with no parameter in second method.

Java version 1.5.2.5(2014-10-11)
* [oracle/plsql] fix a bug that can't parse chained method with no parameter.

Java version 1.5.2.4(2014-10-10)
* [oracle/plsql] support CHAR in this declaration:  TYPE line IS TABLE OF point INDEX BY VARCHAR2(32 CHAR);
* [oracle] schema token of table is missing in truncate table statement if table name was qualified.
* [netezza] support cte in create view statement
* [oracle] improve support PLSQL Method Chaining

Java version 1.5.2.3(2014-09-16)
* [demo] improve demo analzyeScript to illustrate to how parse query hint in option clause.
* [sql server] able to fetch detailed information about option clause in select, delete, update and merge statement.
* [sql server] add new class for set rowcount statement: TMssqlSetRowCount
* [sql server] add new enum: EQueryHint
* [sql server] add new class: TOptionClause, TQueryHint
* [sql server]  add support for table hint in query hint.
* [sql server]  change type of TTableHint.exprList from TPTNodeList <TExpression> to TExpressionList


Java version 1.5.2.2(2014-09-11)
* [sql server] ajust operator precedence levels to comply with TSQL
* [oracle] support type constructor expression in single statement

Java version 1.5.2.1(2014-09-09)
* [mysql] fix a bug can't link quoted table name with normal table name
* [db2] support rollback statement in stored procedure
	
Java version 1.5.2.0(2014-08-29)
* [pp] fix a bug in multithread environment using pp.

related file:
MediatorFactory.java
ProcessorFactory.java
FormatterFactory.java

* [oracle] fix a bug can't parse alter session set DDL_LOCK_TIMEOUT
* [teradata] fix a bug can't parse DATE keyword in values clause of insert statement.
* [teradata] support create index with no index name specified.
* [teradata] support default constraint after data attribute list in column definition
* [teradata]  Any order of the GROUP BY and ORDER BY clauses appear in select can be parsed.
* [teradata] fix a bug can't parse DATE keyword inside ADD_MONTHS function.
* [teradata] fix a bug can't parse primary index in create table(AS Clause)
* [teradata] support unqiue aggregate type in function
* [teradata] add support for create procedure statement

Java version 1.5.1.8(2014-08-03)
* [teradata] support all combinations of set/multiset global temporary/volatile keyword in create table.
* [oracle] fully support plsql create type and create type body
* [teradata] fix a bug can't parse merge insert clause with VALUES keyword
* [teradata] support having clause after order by clause in select statement

Java version 1.5.1.8(2014-08-01)
* [teradata] fix a bug can't recognize DATE function in this syntax: (DATE (FORMAT 'YYYY/MM/DD')
* [teradata] support syntax: COLLECT STATISTICS xxx INDEX (name list)

Java version 1.5.1.8(2014-07-30)
* [netezza] fix a bug can't parse TEMP keyword in create TEMP table statement======================================


Java version 1.5.1.7(2014-07-29)
* [oracle] fix a bug can't parse CHR function with using clause in plsql code.
* [netezza] add support for alter table statement, supported clause: add column, rename table,

Java version 1.5.1.7(2014-07-28)
* [teradata] fix a bug can't parse HOUR TO SECOND(0)
* [teradata] fix a bug can't parse  USING Request Modifier with DATE
* [teradata] support returns clause in table function
* [teradata] support single column name in collect stats statement
* [teradata] support _unicode,_latin,_graphic,_kanjisJIS character set.
* [teradata] support CT keyword in create table statement 
* [teradata] support generated...as identity column attribute
* [Teradata] fix a bug can't parse MINUTE(4) TO SECOND(2)  interval qualifier
* [teradata] able to recognize show statement, rename statement 
* [teardata] add support for GIVE statement
* [teradata] fix a bug can't parse column definition if datatype attributes appears 
* [oracle] fix a bug can't parse group by clause with listed parenthesis expression.
* [netezza] able to recognize commit statement
* [postgresql] fix a bug can't parse date function correctly.

Java version 1.5.1.6(2014-07-09)
* [netezza] Don't treat '\' as an escape char                     
* [general] fix a bug when modify sql, add where clause after adding join condition
* [Netezza] support explicit datetype cast
* [Postgresql] fix a bug can't recognize money,bigint,bigserial,typea datatype correctly.
* [Teradata] including named clause in result column when calling TResultColumn.toString()
* [MySQL] fix a bug can't parse user defined demlimiter correctly

Java version 1.5.1.5(2014-07-04)
* [Oracle] fix a bug when quote delimiter was used in execute immediate statement.
* [Oracle] add support for alter view viewname compile

Java version 1.5.1.4(2014-06-24)
* [Netezza] fix a bug mishandle '\' inside a literal
* [Netezza] support CTE in insert statement		
* [Netezza] support timestamp cast function
* [Oracle] fix a bug can't parse sql when keyword RETURN use as table alias       
* [Oracle] fix a bug can't parse plsql package body when case statement inside specification                                               
* [Oracle] support rowtype record variable in merge statement
* [Oracle] support INTERVAL constant

Java version 1.5.1.3(2014-06-20)
* [Teradata] support commit statement

Java version 1.5.1.2(2014-06-16)
* [Teradata] fix a bug that missing end parenthesis in expression if including explicit datatype conversion

Java version 1.5.1.1(2014-06-12)
* [Sybase] support insert bulk requests
* [Sybase] fix a out of memory (java heap space) bug while parsing set statement inside procedure

Java version 1.5.1.0(2014-06-06)
* [Teradata] Fix a bug can't parse COLLECT STATISTICS  with COLUMN options

Java version 1.5.0.9(2014-05-30)
* [Teradata] Fix a bug can't parse COLLECT STATISTICS  with INDEX options
* [Teradata] able to get table/column info from COLLECT STATISTICS statement


Java version 1.5.0.8(2014-05-29)
* [Oracle] fix a bug can't parse create trigger statement with nested function/procedure declaration.

Java version 1.5.0.7(2014-05-23)
* [Netezza] fix a bug can't parse cast value to TIMESTAMP in select list.

Java version 1.5.0.6(2014-05-16)
* [Netezza] fix a bug can't parse National character correctly if there is a escape 
* [Netezza] fix a bug can't parse substring correctly.

Java version 1.5.0.5(2014-05-14)
* [Netezza,PostgreSQL, Greenplum] Fix a bug that Left operand of assignment expression within update statement not parsed correct


Java version 1.5.0.5(2014-05-08)
* [MySQL] Fix a bug can't handle "delimiter" directive correctly                             
* [MySQL] Fix a bug does not recognize column lengths in parentheses when specifying columns for indexes
* [MySQL] Index column list in TConstraint was changed from columnList to indexCols.
* [Generic] add new enum: ESortType, will be used to replace TBaseType.srtNone,srtAsc and srtDesc
* [Generic] add new class: TIndexColName, represent index column in MySQL.


Java version 1.5.0.4(2014-04-25)
* [Teradata] add public void accept(TParseTreeVisitor v) for class:
  TIndexDefinition,TCollectFromOption,TCollectColumnIndex and TTeradataLockClause


Java version 1.5.0.3(2014-04-21)
* [Teradata] fix a bug can't parse date datatype in cast expression if more than one date keywords in sql.
* [Teradata] fix a bug can't parse float number in compress clause of create table statement

Java version 1.5.0.3(2014-04-18)
* [Teradata] support the third parameter in substring function.
* [Teradata] support volatile multiset keywords in create table statement
* [Teradata] fix a bug can't parse column without parenthesis in collect stats.
* [Teradata] fix a bug can't parse STATS keyword in create table statement
* [MySQL] fix a bug can't parse datetime datetype with length 
	

Java version 1.5.0.3(2014-04-17)
* [Teradata] Able to parse ^ as a NOT operator

Java version 1.5.0.2(2014-04-11)
* [Teradata] fix a bug can't detected alias in (named aliasname)

Java version 1.5.0.1(2014-04-04)
* [Teradata] support is [not] in predicate

Java version 1.5.0.2(2014-04-11)
* [Teradata] fix a bug can't detected alias in (named aliasname)

Java version 1.5.0.1(2014-04-03)
* [general] add location property to TSelectSqlStatement, if select statement is a subquery,
location property can be used to indicate where it comes from, such as where clause.


Java version 1.5.0.0(2014-03-31)
* [Oracle] fix a bug can't parse create trigger if procedure specification was define inside trigger.                                                     

Java version 1.5.0.0(2014-03-24)
* [MySQL] fix a bug can't parse truncate table statement if keyword table is omitted.

Java version 1.5.0.0(2014-03-21)
* [Teradata] fix a bug can't parse bigint, tinyint and number datatype in explicit dataType conversion clause
* [Teradata] support primary index clause in create table statement
* [Teradata] support on commit clause in create table statement
* [Teradata] fix a bug can't parse Create set volatile table.
* [Teradata] fix a bug that column with name "period" will be lost in column list of insert statement.
* [Oracle] fix a bug can't parse object access expression with name more than 4 parts.

Java version 1.5.0.0(2014-03-19)
* [general] fix a bug can't detect AND keyword use as table alias

Java version 1.4.9.9(2014-03-12)
* [Netezza] able to parse create external table

Java version 1.4.9.9(2014-03-11)
* [Teradata] fix a bug can't detect syntax error if there is no "with no data" clause in create table ... as statement

Java version 1.4.9.9(2014-03-10)
* [general] fix a bug misidentified columns in HAVING clause 
* [Oracle] fix a bug can't parse negative scale value in number datatype


Java version 1.4.9.8(2014-03-05)
* [Teradata] Rename TDatatypeAttribute.value to attributeValue
* [Teradata] Rename TDatatypeAttribute.type to attributeType
* [Teradata] TOutputFormatPhrase, TOutputFormatPhraseList are no longer used.
  use TExplicitDataTypeConversion instead

Java version 1.4.9.8(2014-02-28)
* [Teradata] Fully support time, date and timestamp datatype in datatype Attribute.
* [Teradata] support create set table .. as statement.
* [Teradata] fix a bug can't parse HOUR(4) TO MINUTE interval qualifier


Java version 1.4.9.7(2014-02-25)
* [Teradata] support qualified name in columns of create view statement
* [Oracle] fix a bug can't parse order by clause in select statement of cursor.


Java version 1.4.9.7(2014-02-24)	
* [Oracle] fix a bug that treat "/" at a single line inside pl/sql code as command delimiter.
* [Oracle] fix a bug can't parse create type statement index by a user defined type
* [Teradata] fix a bug can't parse column PERIOD in select list.

Java version 1.4.9.6(2014-02-17)
* [Netezza] support select...from external 

Java version 1.4.9.5(2014-02-13)
* [Teradata] support create table .. as statement.
* [Teradata] fix a bug can't parse CREATE VOLATILE SET TABLE statement.
* [Teradata] fix a bug can't parse format attribute including timestamp type 


Java version 1.4.9.4(2014-02-07)
* [PostgreSQL] fix a bug string concatenation is not recognized conrrectly.
* [PostgreSQL] add support for VALUES Lists in from clause.
* [PostgreSQL] able to get row count and offset value for limit clause via TLimitClause
* [general] remove class TSelectLimit, use TLimitClause instead.
* [general] change TLimitClause.offset, TLimitClause.row_count from type TConstant to TExpression.
* [general] TLimitClause.selectLimitValue replaced by TLimitClause.row_count.   
* [Teradata] fix a bug that 'NOT CS' is being changed to 'NOTCS' during pretty print.
* [Teradata] fix a bug can't handle graphic literal correctly.		
* [Oracle] Support three dimensional array.
* [Oracle] subtype keyword can be used in parameter name
* [Oracle] support custom type name
* [Oracle] support numeric expression in limit clause in fetch statement.
* [Oracle] support interface type name
* [Oracle] support collection count method in a condition.	
* [Oracle] support language specification in function specification.
* [Oracle] fix a bug can't parse translate function if the third parameter is a integer;
* [Oracle] add support for collections in using clause of execute statement
* [Oracle] fix a bug can't parse qualified type name in declare statement of PLSQL.

Java version 1.4.9.3(2014-01-29)
* [Hive] improved to return null instead of NullPointerException if isBaseTable() of TTable is false.   
* [Teradata] fix a bug can't parse day(4) to minute
* [Teradata] fix a bug can't parse CREATE MULTISET VOLATILE TABLE  statement


Java version 1.4.9.2(2014-01-08)
* [Netezza] fix a bug that MINUS/INTERSECT/EXCEPT keywords break stmt.getSubQuery().toString() 

Java version 1.4.9.2(2014-01-06)
* [DB2] fix a bug keyword HOUR can't be column name in select list.
* [General] fix a bug can't detect syntax error if value list is not the 
	same size as column list in insert statement.

* [PostgreSQL] fix a bug can't parse only constant in the right side of in condition.
	
Java version 1.4.9.1(2014-01-02)
* [Greenplum] support Greenplum including stored procedure.
* [Netezza, SQL Server, Sybase] fix a bug can't parse only constant in the right side of in condition.
	

Java version 1.4.9.1(2013-12-26)
* [greenplum] support set schema name in alter table statement
* [greenplum] support rename column clause in alter table statement

Java version 1.4.9.0(2013-12-23)
* [Hive] fix a bug raise an exception while parse alter view statement with as select statement.
* [Teradata] fix a bug can't parse interval qualifier inside function call.	
* [Teradata] support lock clause items in create view statement
	
Java version 1.4.8.9(2013-12-13)
* [MySQL] fix a bug create view statement was treated as unknown statement.

Java version 1.4.8.9(2013-12-10)
* [Oracle] fix a bug can't parse loop statement in some condition introduced in Java version 1.4.8.3(2013-10-25)
* [Teradata] fix a bug can't parse using request modifier.
* [Teradata] support uc keyword in UPPERCASE Phrase
* [Teradata] support cs keyword in CASESPECIFIC Phrase

Java version 1.4.8.9(2013-12-09)
* [Teradata] fix minors bug can't parse output format phrase correctly.

Java version 1.4.8.9(2013-12-06)
* [Hive] fix a bug parsing identifies "=" as token type ttkeyword rather than ttequals                
* [Postgresql] fully support PL/pgSQL

Java version 1.4.8.8(2013-12-05)
* [Teradata] add support for COLLECT STATS db1.tbl1 COLUMN (id); which was removed in Java version 1.4.8.5
* [Oralce] rename TPlsqlElsifStmt to TElsifStmt
* [Oralce] move TPlsqlElsifStmt from gudusoft.gsqlparser.stmt.oracle to gudusoft.gsqlparser.stmt

Java version 1.4.8.8(2013-12-04)
* [Oralce] rename TPlsqlAssignStmt to TAssignStmt
* [Oralce] move TPlsqlAssignStmt from gudusoft.gsqlparser.stmt.oracle to gudusoft.gsqlparser.stmt
* [Oracle] rename TPlsqlBlock to TCommonBlock
* [Oracle] move TPlsqlBlock from from gudusoft.gsqlparser.stmt.oracle to gudusoft.gsqlparser.stmt
* [Oracle] rename TOracleStoredProcedureSqlStatement to TCommonStoredProcedureSqlStatement
* [Oracle] move TOracleStoredProcedureSqlStatement from from gudusoft.gsqlparser.stmt.oracle to gudusoft.gsqlparser.stmt

Java version 1.4.8.8(2013-12-02)
* [Oralce] rename TPlsqlBasicStmt to TBasicStmt
* [Oralce] move TPlsqlBasicStmt from gudusoft.gsqlparser.stmt.oracle to gudusoft.gsqlparser.stmt
* [Oracle] rename  TPlsqlCloseStmt to TCloseStmt
* [Oracle] move TPlsqlCloseStmt from gudusoft.gsqlparser.stmt.oracle to gudusoft.gsqlparser.stmt
* [Oracle] rename TPlsqlFetchStmt to TFetchStmt
* [Oracle] move TPlsqlFetchStmt from gudusoft.gsqlparser.stmt.oracle to gudusoft.gsqlparser.stmt
* [Oracle] rename TPlsqlOpenforStmt to TOpenforStmt
* [Oracle] move TPlsqlOpenforStmt from gudusoft.gsqlparser.stmt.oracle to gudusoft.gsqlparser.stmt
* [Oracle] rename TPlsqlOpenStmt to TOpenStmt
* [Oracle] move TPlsqlOpenStmt from gudusoft.gsqlparser.stmt.oracle to gudusoft.gsqlparser.stmt
* [Oracle] move TExecImmeNode from gudusoft.gsqlparser.stmt.oracle to gudusoft.gsqlparser.nodes
* [Oralce] rename TPlsqlRaiseStmt to TRaiseStmt
* [Oralce] move TPlsqlRaiseStmt from gudusoft.gsqlparser.stmt.oracle to gudusoft.gsqlparser.stmt
* [Oralce] rename TPlsqlReturnStmt to TReturnStmt
* [Oralce] move TPlsqlReturnStmt from gudusoft.gsqlparser.stmt.oracle to gudusoft.gsqlparser.stmt
* [Oracle] rename TPlsqlExitStmt to TExitStmt
* [Oracle] move TPlsqlExitStmt from gudusoft.gsqlparser.stmt.oracle to gudusoft.gsqlparser.stmt
* [Oracle] rename TPlsqlLoopStmt to TLoopStmt
* [Oracle] move TPlsqlLoopStmt from gudusoft.gsqlparser.stmt.oracle to gudusoft.gsqlparser.stmt
* [Oralce] rename TPlsqlCaseStmt to TCaseStmt
* [Oracle] move TPlsqlCaseStmt from gudusoft.gsqlparser.stmt.oracle to gudusoft.gsqlparser.stmt
* [Oracle] rename TPlsqlStmt to TLabeledStmt
* [Oracle] move TPlsqlStmt from gudusoft.gsqlparser.stmt.oracle to gudusoft.gsqlparser.stmt
* [Oralce] rename TPlsqlIfStmt to TIfStmt
* [Oracle] TPlsqlIfStmt move from gudusoft.gsqlparser.stmt.oracle to gudusoft.gsqlparser.stmt
* [oracle] rename TPlsqlCursorDeclStmt to TCursorDeclStmt
* [oracle] TPlsqlCursorDeclStmt move from gudusoft.gsqlparser.stmt.oracle to gudusoft.gsqlparser.stmt
* [oracle] rename TPlsqlVarDeclStmt to TVarDeclStmt
* [oracle] TPlsqlVarDeclStmt move from gudusoft.gsqlparser.stmt.oracle to gudusoft.gsqlparser.stmt


Java version 1.4.8.7(2013-11-25)
* [Netezza] support distribute clause in create view statement
* [Netezza] support distribute on random clause in create table as statement.
* [Netezza] support generate [express] statistics statement, add new class: TNetezzaGenerateStatistics
* [Netezza] support groom table statment, add new class: TNetezzaGroomTable.
* [Teradata] fix a bug can't parse datatype attribute before datatype

Java version 1.4.8.6(2013-11-21)
* [Teradata] fix a bug can't parse table level primary key.
* [General] Don't visit having clause in TGroupBy.accept method
* [SQL Server] add support for NEXT VALUE FOR function.


Java version 1.4.8.6(2013-11-14)
* [Hive] HIVE-3472 : add Date data type 
* [Hive] HIVE-784 : Support uncorrelated subqueries in the WHERE clause
* [Hive] HIVE-3976 - Support specifying scale and precision with Hive decimal type
* [Hive] HIVE-5191: Add char data type
* [Hive] Support providing some table properties via HQL,TTable public TPTNodeList<THiveKeyValueProperty> getTableProperties()
* [Hive] HIVE-4658 : Make KW_OUTER optional in outer joins
* [Hive] Hive-2608 Do not require AS a,b,c part in LATERAL VIEW
* [MySQL] fixed a NullPointerException error where parsing decode function
    
Java version 1.4.8.5(2013-11-07)
* [Teradata] support collect statistics in V14.0
* [Oracle] fix a bug treat parameters in subquery of declare Cursor statement as column name.
        

Java version 1.4.8.4(2013-10-31)
* [demos] support decalre and set statement in xml demo.
* [DB2] support SYS naming option where tables is identified as library/file (library=schema and file=table)
* [Oracle] able to get detailed informaiton about call statement by adding a new class: TCallStatement	
* [general] add new enum type ELiteralType, add new property TConstant.literalType
* [MySQL] support date, time, timestamp literal by specified using a type keyword and a string.
* [Demo] improve toXML demo to support expression list in in expression.
* [SQL Server] fix a bug when keyword MINUS use as column alias.        
* [SQL Server] fix a bug treat the date/time part as a column name in dateadd,datediff,datename and datepart function


Java version 1.4.8.3(2013-10-29)
* [MySQL] add support for with rollup modifier in group by clause	
* [MySQL] add new class TSetAssignment, enum: ESetScope,ETransactionIsolationLevel,ESetStatementType
* [MySQL] able to get detailed information of set statement
* [MySQL] fix a bug can't parse connect string like this: 'bob'@'%.example.org'

Java version 1.4.8.3(2013-10-25)
* [general] fix a bug can't link column to table correctly 
* [Oracle] fix a bug can't parse loop ... end loop if there is only single statement inside loop.

Java version 1.4.8.2(2013-10-23)
* [general] add version information in MANIFEST.MF
* [SQL Server] fix a bug can't parse SP_RENAME 'ValidBatchJob.JobCode' , 'JobRSN',  'COLUMN'

Java version 1.4.8.1(2013-10-22)
* [Postgresql] fix a bug can't recognize create view statement

Java version 1.4.8.0(2013-10-21)
* [SQL Server] add support for create sequence, drop sequence and alter sequence.
* [general] add new class TSequenceOption,enum ESequenceOptionType,
	 all sequence options was available.
	 
Java version 1.4.8.0(2013-10-18)
* [Teradata] support "NOT CASESPECIFIC" clause in create table
* [Oracle] fix a bug can't get table/column in the "chr" Oracle/PLSQL function
* [MySQL] fix a bug can't handle string large than 256 characters

Java version 1.4.8.0(2013-10-11)
* [Teradata] add support for LOCKING Request Modifier
* [Teradata] add support for USING Request Modifier

Java version 1.4.7.9(2013-10-09)
* [demos] improve toXML demo that able to list table hint and aggregateType of function call.
* [SQL Server] add TTableHint to TParseTreeVisitor
* [SQL Server] fix a bug mixed table alias with table hint
* [Teradata] able to process extra semi colons in sql script
* [netezza] fix a bug can't parse get values from sequence inside parenthesis.


Java version 1.4.7.8(2013-10-08)
* [MySQL] fix a bug can't parse create function with DEFINER=`demo`@`%`                              
* [MySQL] add new enum EDeclareType represents type of declare statement
* [MySQL] add support for characteristic in create function statement.
* [MySQL] fix a bug can't parse inner join clause without join condition
* [netezza] fix a bug can't parse ORGANIZE ON clause in create table statement


Java version 1.4.7.7(2013-09-30)
* [general] add a new demo rmdupParenthesis to illustrate how to remove duplicated parenthesis in select statement and expression.
* [general] add a new property public TSourceToken getLinkToken() in TSourceToken.java

Java version 1.4.7.7(2013-09-29)
* [Oracle] new keyword was treated as identifier in referencing clause of create trigger

Java version 1.4.7.6(2013-09-25)
* [Teradata] fix a bug can't parse create database.

Java version 1.4.7.6(2013-09-22)
* [General] In TSelectSqlStatement, add a new method addWhereClauseOR/addConditionOR that specify an addition with an "or".

Java version 1.4.7.5(2013-09-18)
* [Oracle] fix a bug can't parse natural outer join.

Java version 1.4.7.5(2013-09-11)
* [Oracle] fix a bug can't get statement correctly if there are multiple create library statements
* [general] fix a bug when add new condition to where clause by always adding parentheses around old condition.
* [general] add a new method addCondition of TSelectSqlStatement which is alias of addWhereClause method.

Java version 1.4.7.4(2013-09-06)
* [sql format] put "BETWEEN ... AND" in the same line
* [sql format] fix a bug When wsPaddingParenthesesInExpression = false, FormatterFactory.pp() mangles "IS NULL"


Java version 1.4.7.4(2013-09-05)
* [Sybase] support on segment name clause in create index statement
* [Sybase] improvement support of update column clause in create trigger
* [Sybase] fix a bug can't parse at isolation clause after order by clause

Java version 1.4.7.3(2013-09-03)
* [Hive] including test cases under test\hive directory, illustrates how to access parse tree nodes of hive query.
* [Oralce] fix a bug can't get schema name in CREATE LIBRARY statement
* [Oralce] support UNTRUSTED in CREATE LIBRARY statement
* [Sybase] fix a bug can't parse set statement when it's the last statement in stored procedure.

Java version 1.4.7.3(2013-09-02)
* [Sybase] fix a bug can't parse dump tran and update index statistics statement inside stored procedure

Java version 1.4.7.2(2013-09-02)
* [Sybase] fix a bug can't detect link between table and column when there is index hint in table.

Java version 1.4.7.2(2013-08-30)
* [Sybase] support the ‘begin’ and ‘end’ block after a special label.
* [Sybase] RIGHT keyword can be column name in set clause of update statement.
* [Sybase] support mixed condition in update column clause of create trigger statement
* [Sybase] the string value with double quotation mark "" and start with a number character will not be treated as a column


Java version 1.4.7.1(2013-08-29)
* [Teradata] support "RESET WHEN" clauses in window aggregate functions
* [Sybase] fix a bug treat the date/time part as a column name in dateadd,datediff,datename and datepart function
* [Sybase] fix a bug can't parse update all statistics
* [Sybase] support 'on default' clause while creating table
* [Sybase] fix a bug can't parse 'RAISERROR @@error,'
* [Sybase] support 'with fillfactor =' clause while creating index
* [Sybase] able to recognize update index statistics statement
* [Sybase] support isolation clause.
* [Sybase] able to recognize dump transaction statement.
* [Sybase] fix a parse error when insert column with database name


Java version 1.4.7.1(2013-08-28)
* [Oralce] fix a bug can't parse in condition if only single value in the right side

Java version 1.4.7.1(2013-08-27)
* [Teradata] support index definition clause in create table	
* [Oralce] enhanced sql formatter for plsql exception clause and if/else statement.
* [Hive] fix a bug can't get text of select statement in insert statement.  
* [Teradata] support create table option.  	
* [Teradata] support constant list in compress clause

Java version 1.4.7.0(2013-08-23)
* [Sybase] fix a bug can't link column in force index function to the table correctly.
    

Java version 1.4.7.0(2013-08-21)
* [Hive] query start from FROM keyword is treated as THiveFromQuery statement(formly treated as select statement) 
	except the one used in union set which is still treated as a select statement. 
* [Oracle] support alter trigger statement
* [Oracle] able to split sql script including create trigger, alter trigger without / to separate those statements


Java version 1.4.6.9(2013-08-19)
* [Oracle] support create package body with empty body.
* [Oracle] fix a bug can't parse loop statement when only single null; statement inside.
* [Teradata] fix a bug fails to parse recursive statement in insert statement
* [Teradata] fix a bug can't parse NEW VARIANT_TYPE if no alias after argument.
* [Hive] Fully Hive support.
* [Teradata] support use of an IN keyword followed by a literal: cust_id in 200


Java version 1.4.6.8(2013-08-14)
* [Sybase] improve the ability to detect all column names(reserved words listed in sybase official document can't be used as column name)
* fix a bug treats the cursor name as the column of the update table for the statement ‘UPDATE Where Current of Cursor’
* [Sybase] fix a bug can’t extract column information of table with force index function.
* Able to process literal without size limitation.    
* [Oracle] enhancement of plsql sql formatter.
* [Hive] fix a bug can't parse select statment with only select clause.
   
Java version 1.4.6.7(2013-08-12)
* [Hive] parse tree of select and insert statement is available.
* [Hive] add test cases for select and insert statement.

Java version 1.4.6.6(2013-08-2)
* [SQL Server] fix a bug can't recognize TYPE and ACTION as column name
* [PostgreSQL] able to fetch all detailed information about alter table statement
adding 
	new class TAttributeOption
	new value of enum EAlterTableOptionType
    AlterColumnSetDefault,
    AlterColumnDropDefault,
    AlterColumnDropNotNull,
    AlterColumnSetNotNull,
    AlterColumnSetStatistics,

    AlterColumnSetOptions,
    AlterColumnResetOptions,
    AlterColumnSetStorage,
    AlterColumnSetDataType,
    AddTableConstraint,
    ValidateConstraint,
    dropConstraint,
    setWithOIDS,
    setWithoutOIDS,
    clusterOn,
    setWithoutCluster,
    enableTrigger,
    enableAlwaysTrigger,
    enableReplicaTrigger,
    enableTriggerAll,
    enableTriggerUser,
    disableTrigger,
    disableTriggerAll,
    disableTriggerUser,
    enableRule,
    enableAlwaysRule,
    enableReplicaRule,
    disableRule,
    inherit,
    noInherit,
    ofAnyType,
    notOf,
    ownerTo,
    setTablespace,
    setStorageParameters,
    resetStorageParameters,
	
	new members in class TAlterTableOption
		public TObjectName getNewTablespaceName()
		public TObjectName getNewOwnerName() 
		public TObjectName getAnyTypeName()
		public TObjectName getParentTable() 
		public TObjectName getRuleName()
		public TObjectName getTriggerName() 
		public TObjectName getIndexName()
		public TConstraint getTableConstraint()
		public TExpression getUsingExpr()
		public TObjectName getNewCollation()
		public TTypeName getNewDataType()
		public TObjectName getStorageName()
		public TPTNodeList<TAttributeOption> getAttributeOptions()
		public TConstant getStatisticsValue()
		public TExpression getDefaultExpr()

Java version 1.4.6.6(2013-08-1)
* [Hive] support variable and fix some minor parse bugs

Java version 1.4.6.5(2013-07-31)
* [Hive] able to parse all hive queries, but parse tree is not available in this version.

Java version 1.4.6.4(2013-07-30)
* [PostgreSQL] able to get SYMMETRIC part in between condition by introduce 
	a new function TExpression.isSymmetric()

Java version 1.4.6.4(2013-07-29)
* [Teradata] support interval qualifier of time, timestamp and date constant
* [Teradata] support at 'America Pacific' clause in cast function
 

Java version 1.4.6.4(2013-07-23)
* [Hive] start to work for Hive

Java version 1.4.6.3(2013-07-20)
* [Oracle] fix a bug can't parse PIVOT/UNPIVOT clause after table alias clause
* [SQL Sever] fix a bug can't parse operator != followed by -2 without a space


Java version 1.4.6.3(2013-06-27)
* [SQL Sever] fix a bug can't parse operator != followed by -2 without a space

Java version 1.4.6.3(2013-06-27)
* [Teradata] fix a bug can't parse when a '=' followed by a '$'
* [Teradata] fix a bug can't parse update with nested target 
* [Teradata] fix a bug can't parse a INSERT WITH statement
* [Teradata] fix a bug can't parse MOD expression in between condition

Java version 1.4.6.2(2013-06-26)
* [Teradata] fix a bug can't parse CHAR SET LATIN
* [Oracle] fix a bug can't parse < operator when it is preceded by ? without a space. 
* [Teradata] fix a bug can't parse COLLECT STATS ON schema1.table1;
* [MySQL] support unsigned keyword in create table statement
* [Postgresql] fix a bug that parse character as nchar_t, but it should be char_t.
* [Postgresql] fix a bug can't recognize time,serial,text datatype correctly.
* [Postgresql] support IF EXISTS clause and ONLY keyword in alter table statment
* [MySQL] fix a bug that treats tinyint as real datatype
* [MySQL] fix a bug can't recognize boolean datatype correctly.

Java version 1.4.6.2(2013-06-13)
* [Postgresql] improve to handle precision and scale in datatype
* [Postgresql] fix a bug can't recognize date datatype correctly.
* [Teradata] fix a bug parsing COLLECT STATS statement
	
Java version 1.4.6.1(2013-06-05)
* fix a bug treat column alias in group by clause as a column.

Java version 1.4.6.0(2013-05-31)
* [Oracle] support member condition in PLSQL
* [Oracle] support iS not empty predicate
* [Oracle] fix a bug can't get raw statement correctly inside create package.

Java version 1.4.6.0(2013-05-29)
* [MySQL] support ( table_references ) in table_factor

Java version 1.4.5.9(2013-05-17)
* [Oracle] support subquery in pivot_in_clause
* [Oracle] support chr function with using NCHAR_CS parameter
* [MySQL] support into clause at the end of select statement
* [MySQL] fix a bug can't parse CAST(cnt AS DECIMAL)
* [Oracle] add support for natural full|right|left [outer] join
* [Oracle] add support for getRestrictionClause() in TCreateViewSqlStatement 
* [Oracle] support natural inner join

version Java 1.4.5.8(2013-04-18)
* [MySQL] MySQL comment requires a space after the initial "--", able to detect this syntax error
* [MySQL] support delimter command
* [Teradata] support volatile keyword in create table statement
* [mssql] fix a bug not parse truncate table statment inside IF statement

version Java 1.4.5.7(2013-04-01)
* [DB2] support commit statement inside loop
* [DB2] support create or replace clause in create trigger statement.
* [Oracle] More accurate to report datatype in index by clause.
* add a new interface: ITokenHandle, this interface can be used to handle source token 
	when parse sql query using TGSqlParser. each source token created by lexer can be
	handled before send to parser, this enable you to control how a source token should
	be processed by a parser by resetting tokencode of a TSourceToken object.

version Java 1.4.5.6(2013-03-27)
* [DB2] able to regonize stored procedure without a speical terminator.
* [Oracle] support  'PIPELINED USING schema.implementation type' and 'AGGREGATE USING schema.implementation type' in create function
* [Oracle] support pipelined keyword in create function
* [Oracle] fix a bug that handle pivot clause.
	
version Java 1.4.5.5(2013-03-26)
* [MySQL] support describe statement and adding new class: TDescribeStmt
* [MySQL] support prepare statement and adding new class: TMySQLPrepareStmt
* [MySQL] support truncate table statement 
* [MySQL] support exist condition in select list
* [DB2] support qualified name in SPECIFIC clause in create procedure
* [DB2] support restart with clause in identity alteration
* [DB2] fixed a error can't parse signed number in identity options
* [DB2] able to ignore syntax error in create index statement

version Java 1.4.5.4(2013-03-22)
* [DB2] support select * from s.t1 FOR UPDATE 
* [Oracle] fix a bug doesn't regonize datatype in index by clause.
* [Oracle] support create package body without declare section
* [Oracle] able to access detailed argument of xmlelement function using getArgs() and getValueExprList()
* [Oracle] fix a bug can't process <>? correctly
* [Oracle] fix a bug can't process <=? correctly
* [MySQL] support MySQL's VALUE keyword (it is a synonym for VALUES).

version Java 1.4.5.2(2013-03-14)
* fix a bug that raise exception when set the meta database processing some SQL statement.
* rename TMergeInsertClause.deleteWhereClause to TMergeInsertClause.insertWhereClause
* rename TMergeInsertClause.getDeleteWhereClause to TMergeInsertClause.getInsertWhereClause 

version Java 1.4.5.2(2013-02-22)
* [Teradata] support Implied CAST like this {(t1.ACCT_OPEN_D (FORMAT 'YYYYMMDD')   (CHAR(8)) )}
* [Mdx] support scope statement without statement list after
* [Teradata] support NOT CASESPECIFIC datatype Attribute
* [Teradata] fix a bug can't parse character set datatype
* [Oracle] support is empty collection operator in sql statement
* [Oracle] support the use of the ansi lateral operator

version Java 1.4.5.1(2013-02-19)
* [Oracle] fix a bug doesn't support connect_by_root operator in where condition


version Java 1.4.5.1(2013-02-18)
* [Oracle]  improved support for unpivot clause.
* [Oracle] support collection operator: multiset union/intersect/except
* [Oracle] support is empty collection operator
* [Oracle] support interval expression within the scope of an over function.
* [Oracle] support "order by" clause within the scope of an xmlagg function call.

version Java 1.4.5.1(2013-02-17)
* [Oracle] fix a problem to parse 1..:bl_test

* [Oracle] able to get detailed information about invoker rights clause, 
	DETERMINISTIC, parallel enable clause and result cache clause.
	
* [Oracle] introduce new java class: TParallelEnableClause, TResultCacheClause,
	TStreamingClause and TInvokerRightsClause

version Java 1.4.5.0(2013-02-14)
* [Oracle] support a "connect by" clause follows a "group by" clause.
* [Oracle] 'type' can be column name 
* [Oracle] able to handle the order by clause in the context of a collect function
* [Oracle] fix a bug can't process substition variable correctly inside quote.

version Java 1.4.4.9(2013-02-08)
* [Teradata] support expression list in group by clause like this: GROUP BY (1,2,3,4,5,6,7,8,9,10,11,12)

version Java 1.4.4.8(2013-02-06)
* [Oracle] fix a bug that natural can't be used as database object name;
* [Oracle] 'type' can be column name in for update clause
* [Oracle] fix a bug that doesn't recognize '-', '+' as a unary operator unless it is preceded by whitespace
* [Oracle] allowing an alias ('t') to follow a sample block when the seed specification is missing.

version Java 1.4.4.8(2013-02-05)
* add new enum type:
	public enum EAggregateType {
	    none,
	    all,
	    distinct,
	    unique,
	}

* able to get all/distinct/unqiue information in aggregate function by using TFunctionCall.getAggregateType()
* [Oracle] support explain plan statement
* [Oracle] keyword full can be table name and table alias.
* [Oracle] allowing a sample block to contain two parameters when the word 'block' appears after the word 'sample'.

version Java 1.4.4.7(2013-01-31)
* [Oracle] support the "the" clause for querying nested tables
* [Oracle] fix a bug can parse this expression: select 1+-.9 from dual;
* [Oracle] support "select from (tablename)" syntax. 
* [Oracle] fix a bug can't handle predicate like this: 1<-:a;
* [Oracle] support the xml object-like interface.
* [Oracle] support the "insert into table(subquery) alias" syntax.
* [Oracle] fix a bug can't support the predicate 1>=-:a
* [Oracle] support naming arguments for user-defined functions
* [Oracle] support placeholder expression in translate function.
* change definition of  public ArrayList getSyntaxErrors() to  public ArrayList <TSyntaxError> getSyntaxErrors()   
* [demo] improve analyzeScript.java to add support for create index statement.

version Java 1.4.4.6(2013-01-30)
* [Oracle] fix a bug can't parse place holder correctly in into clause and where in condition.
* [Oracle] support the partition clause for delete
* [Oracle] permit whitespace between the two '|' characters in the string concatenate operator
* [Oracle]  keyword: 'right' can be a column name
* [Oracle] support the 'with' clause in an insert statement
* [Oracle] support keyword likec/like2/like4 in like condition
* [Oracle] able to consider 'unique' to be an alias for 'distinct' in aggregate function.
* [Oracle] able to consider 'return' to be an alias for 'returning' in return clause
* [Oracle] support partition clause in insert statement
* [Oracle] support xmlforest
* [Oracle] support xmlroot, XMLSERIALIZE, XMLELEMENT and XMLATTRIBUTES.
* [Oralce] support fully qualified column names: user.table.column in insert column list.
* [Oracle] support skip locked in for update clause.
* [Oracle] fix a bug can't regonize != if follows by - diretly.
* [Oracle] fix a bug lexer can't tokenize host variable start with number in some place.
* [Oracle] support nested subquery in from clause.
* [Oracle] support syntax like this: update abc set (a) = 1;
* [Oralce] support syntax like sample(1,2)
* [plsql] recognize nvarchar datatype correctly


version Java 1.4.4.5(2013-01-28)
* fix a bug can't parse merge statement without merge_update_clause/merge_insert_clause
* fix a bug in merge statement that liste table twice

version Java 1.4.4.5(2013-01-25)
* [Informix] support following SQL statements.
	select/delete/insert/update/merge/truncate
	alter index/sequence/table
	create index/row type/sequence/synonym/table/view
	drop index/row type/sequence/synonym/table/view
	rename column/table/sequence/synonym
	

* [PostgreSQL] fix a bug can't handle escape character \ in string literal.

version Java 1.4.4.5(2013-01-24)
* introce new class: TDropSynonymStmt, TDropSequenceStmt
* create new class TCreateSequenceStmt to replace TOracleCreateSequenceStmt
* create new class TCreateSynonymStmt to replace TOracleCreateSynonymStmt

version Java 1.4.4.4(2013-01-22)
* [Oracle/Informix] add THierarchical.isNoCycle() to get NOCYCLE keyword in hierarchical clause of select statement.
* [Teradata] fix a bug can't parse select statement start with ( sel ... )
* [Teradata] support empty expression list () in IN expression.

version Java 1.4.4.3(2013-01-16)
* [plsql] full parse tree of merge statement inside stored procedure is available
* [plsql] support LANGUAGE JAVA NAME in procedure specification in create package
* [MDX] support create set syntax


version Java 1.4.4.3(2013-01-14)
* [plsql] fix a bug can't recognize plsql datatype: SIGNTYPE

version Java 1.4.4.2(2013-01-12)
* [Oracle] support pivot clause
* [plsql] recognize following plsql datatype more accurate:  NATURALN, POSITIVE, POSITIVEN, SIGNTYPE, SIMPLE_INTEGER, DOUBLE_PRECISION, STRING and BOOLEAN.
* [plsql] able to parse call spec of language C correctly.
* [Oracle] support for update clause before order by clause.


version Java 1.4.4.0(2012-12-04)
* [Oracle] support xmlcast and xmltable function
* [Oracle] support outer join in table collection expression
* [Oracle] support select statement around by multi-level parenthesis in create view statement
* [Oracle] fix a bug can't parse sysdate-?, sysdate*?,sysdate/? correctly.
* [demo] able to analyze Insert statement in demos.analyzescript


version Java 1.4.3.9(2012-11-22)
* [sql formatter] fix a bug can't hanlde single line comment (--) after/before comma in select list

version Java 1.4.3.9(2012-11-19)
* [Oracle] fix a bug can't parse sysdate+? correctly.

version Java 1.4.3.8(2012-11-14)
* [DB2] fix a bug can't parse a !=-9
* [DB2] support day keyword after function call.
* [DB2] support IN keyword as table name
	
version Java 1.4.3.7(2012-11-13)
* [DB2] able to parse main body of create table statement with select statement if other clause can't be parsed correctly.
* [DB2] support create summary table syntax
* [DB2] support OR REPLACE clause in create view statement. (new in V9.7)

version Java 1.4.3.7(2012-11-12)
* [Teradata] support syntax like timestamp(6)
* [netezza] support tablename.* 

version Java 1.4.3.7(2012-11-1)
* [demo] add a new demo sqltranslator, start to support sql translation among different database vendors.
* [demo] rewrite demo removeCondition
* able to parse main body of create table statement if storage or other property can't be parsed correctly.
* [SQL Server] fix a bug that throw unhandled exception while parse some syntax invalid SQL.
* [SQL Server] more accurate report while if found syntax error
* [Oracle] add new class TObjectAccess that represents object access expression when expression type is object_access_t.


version Java 1.4.3.7(2012-10-20)
* [Oracle] introduce TCreateViewSqlStatement.getStForce() and getStReplace()
* [MySQL] support ON DUPLICATE KEY UPDATE in insert statement.

version Java 1.4.3.6(2012-10-08)
* [MySQL] support identifier start with number
* [Netezza] support function: trim(arg1, arg2)
* [Oracle] able to parse scripts correctly even if there are no / betweeen plsql block and select statement.
* [Oracle] support EXTRACT function in XML document

version Java 1.4.3.5(2012-09-27)
* [Oracle] support PRAGMA INTERFACE
* [Oracle] fix a bug can't handle TRANSLATE function correctly.

version Java 1.4.3.5(2012-09-26)
* [Teredata] support collect statistics statement.

version Java 1.4.3.5(2012-09-25)
* [Teredata] support DEL keyword in delete statement.
* [Teredata] fix a bug can't support 'X' literal.
* [Teradata] support syntax of put group by clause after select list directly.

version Java 1.4.3.4(2012-09-21)
* [Sybase] support paritial parsing inside stored procedure.

version Java 1.4.3.4(2012-09-13)
* [Sybase] support noholdlock/holdlock table hint
* [Sybase] able to support hint like this: from TNL tnl1 (index 1)		
* [Sybase] support Schema5.Table1.Column1 in insert column clause.

version Java 1.4.3.3(2012-09-12)
* EExpressionType.group_t not used since 1.4.3.3.
* TExpression.getInExpr() not used since 1.4.3.3, use getRightOperand() instead
* TInExpr not used since 1.4.3.3, replaced by TExpression
* TGroupingExpressionItemList not used since 1.4.3.3, replaced by TExpressionList
* TGroupingExpressionItem not used since 1.4.3.3, by TExpression
 

version Java 1.4.3.3(2012-09-07)
* able to get comparision operator token via getOperatorToken 
* add public void accept(TParseTreeVisitor v) to TTruncateStatement
* [Oracle] support access to multidimensional arrays such as array(x)(y)(z).
* [SQL Server] support Compound Assignment Operators in set clause of update statement.
* support cte with merge statement

version Java 1.4.3.3(2012-09-06)
* [Oracle] keyword 'type' can be used as column name.

version Java 1.4.3.2(2012-09-05)
* fix a bug when traverse in condition via inOrderTraverse/preOrderTraverse/postOrderTraverse method
  this bug was introduced in v1.4.3.0

version Java 1.4.3.1(2012-08-31)
* able to link columns to CTE table correctly.
* introduce a new method TGSqlParser.checkSyntax

version Java 1.4.3.0(2012-08-26)
* [changes]	 static fields TFunctionCall.fntXXX replaced by EFunctionType. 
* [changes]	 static fields TTypeName.lfdXXX replaced by EDataType.
* [changes]	 static fields TExpression.XXXOperator replaced by EExpressionType
	 check Deprecated API in JavaDoc: javadoc/deprecated-list.html for detailed information.
* [changes]  expressionType in TExpression.setExpressionType(int expressionType) change from int to EExpressionType
* [changes]	 return value of int TExpression.getExpressionType() change from int to EExpressionType


version Java 1.4.3.0(2012-08-20)
* add new enum value of EDbVendor : dbvansi,dbvodbc

version Java 1.4.3.0(2012-08-09)
* change type of TTypeName.datatypeAttributeList from TDatatypeAttributeList to TPTNodeList <TDatatypeAttribute> 


version Java 1.4.2.9(2012-08-02)
* make lexer in TGSqlParser public available: TGSqlParser.getFlexer()
* public int TCustomLexer.iskeyword(String str) can be used to check whether a string is a keyword.
  return value > 0 means it's a keyword of targeted database.


version Java 1.4.2.8(2012-07-20)
* [Sybase] able to recognize contract as table/colum name
* [Oracle] support use of an IN keyword followed by a string literal like source_entity_cd IN 'D7'
* [DB2] fix a bug can't handle qualified name after NEXT VALUE FOR
* [Sybase] support set @AccountNumber=NULL, @AccountSystem=NULL, @retval=0
* able to access GROUP BY, HAVING keyword in TGroupBy class
* add accept method for class: TArrayAccess, TGroupingSet, TGroupingSetItem, TRollupCube and TOracleCreateSynonymStmt.

version Java 1.4.2.7(2012-07-13
* [DB2] support named parameter like: CALL TEST2( parm1=>0, parm2=>'EURO'))

version Java 1.4.2.7(2012-07-09)
* [Teradata] support not null constraints in create table.
* [Oracle] support alter session set NLS_TERRITORY=AMERICA; 

version Java 1.4.2.6(2012-06-20)
* [MySQL] fixed a bug introduce in V1.4.2.5 to support parameter like this @`a`

version Java 1.4.2.5(2012-06-19)
* un-qualified column in subquery able to link up level table if it's in select list
* [MySQL] support parameter like this @`a`
* [Teradata] support ${XXXDB} as an identifier 
* [SQL Server] support SQLCMD variable by treat it as an identifier 

version Java 1.4.2.4(2012-06-11)
* [MySQL] support call statement, add new class: TMySQLCallStmt
* [DB2] support default keyword in parameters of procedure/function.
* [DB2] support call function without parameters like this: CALL test2()
* [DB2] support name parameters like CALL FOO (parm1=10, parm2=>20, parm3=>30)
	
version Java 1.4.2.3(2012-06-05)
* [Teradata] support qualified name like this: dbname..tablename
* [Oracle] able to parse the Package Declaration and Package Body that written in the same file, 
	without need to be separated by delimiter character ‘/’. 

version Java 1.4.2.2(2012-05-31)
* [netezza] support next [integer expression] value for <sequence name>

version Java 1.4.2.1(2012-05-23)
* fix a bug that treats level keyword in oracle as a physical column
* fix a bug that column alias in order by clause will be treated as a physical column
* change TBaseType.trial_editoin to full_edition.
* fix a bug can't recoginze datetime as TTypeName.lfdDatetime correctly


version Java 1.4.2.0(2012-05-15)
* All available expression type constant field values of gudusoft.gsqlparser.nodes.TExpression was documented.
* fix a bug that TInsertSqlStatement.getInsertToken() return null when process Oracle multi table insert statement.
* able to access syntax errors by calling TGSqlParser.getSyntaxErrors() which returns list of TSyntaxError
* add a new demo: columnImpact analysis

[version Java 1.4.1.9][2012-05-11]
* [Oracle] support multi table insert.
* [MySQL] fixed a bug can't list in/out mode of function/procedure parameters.
* add accept method to support preVisit and postVisit for the 
	TOracleExecuteProcedure,TOracleCommentOnSqlStmt,TOracleCreateSynonymStmt
	
[version Java 1.4.1.8][2012-05-09]
* [Oracle] support truncate table 
* able to get table information from TCustomSqlStatement.tables for alter table, truncate table and drop table statement.
* [MySQL] support [DEFINER = { user | CURRENT_USER }] in create procedure/function/trigger


[version Java 1.4.1.7][2012-05-06]
* [oracle] support execute procedure command, introduce a new class: TOracleExecuteProcedure
* fix a bug can't use TJoin.setString
* [db2] support alter table alter column drop identity|default
* [db2] support alter table drop column.
* [db2] case keyword can be used as table name.
* [sql server] able to get detailed table hint information.
* able to add a new order by clause if it is not already exist.
* [sybase] had a dedicated engine now.
* [sybase] support lock allpages in create table.
* [sybase] support || operator

[version Java 1.4.1.4][2012-04-01]
* add public interface IMetaDatabase to help SQL parser to determine relationship of column and tables.
  user can implements IMetaDatabase to provide detailed meta information from database.
  
* [MySQL] add support for Automatic Initialization and Updating for TIMESTAMP
* typo: type_table_constarint renamed to type_table_constraint


[version Java 1.4.1.3][2012-03-21]
* Fix a bug can't add where clause at the end of sql correctly.
* introduce a new method: public TTableElementList getTableElementList() represents add <column|constraint>[,...n] clause in alter table statement.
  public TConstraintList getConstraintList() and public TColumnDefinitionList getColumnDefinitionList() in class TAlterTableOption 
  not used to represents column|constraint list in add clause of alter table statement.

* fix a bug that subquery in exist condition not parsed in if statement
* fix a tokenlize error if only a single update statement in if statement
* support NOT FOR REPLICATION in foreign key ... reference clause of table constraint

[version Java 1.4.1.2][2012-03-12]
* able to get cursor name in declare cursor statement.
* support join clause in update statement.
* TMssqlDropDbObject includes full information about drop procedure/function/trigger
* use key_actions which is type of TPTNodeList  to represents all information of key action clause in constraints
* able to get database name in sql server: use dbname statement.
* [oracle] support siblings keyword of  order by clauses.
* fix a bug can't parse condition if there is no space between = and ?.
* [MySQL] support relpace into statement
* [MySQL] support ignore keyword in insert statement
* [MySQL] support multi \ escape character in literal
* fix a null bug when calling TSelectSqlStatement.getSelectDistinct() of sql server statement
* default setting of html output set correctly.
* [oracle] support integer with length definition
* [oracle] support PARALLEL_ENABLE put after DETERMINISTIC
* [oracle] support memeber of operator
* [oracle] support parenthesis around group by item
* [MySQL] support mysql STRAIGHT_JOIN join


[version Java 1.4.0.8][2012-02-07]
* support MDX, fully access parse tree nodes, check demos\visitors\toXml.java for detailed information.
* start to support html output of formatted sql
* [oracle] support String/Integer with length definition
* [oracle] support PARALLEL_ENABLE put after DETERMINISTIC
* [oracle] support memeber of operator
* [oracle] support parenthesis around group by item
* [oracle] support plsql read from array of array
* [mysql] support  STRAIGHT_JOIN join syntax
* [mysql] full outer join is not valid in mysql.
* [teradata] support quaify clause after from clause directly.
* [teradata] database/table/view keyword can be omitted in locking clause.
* [netezza] suppot exclusion clause.
* [mysql] support BTREE/HASH in alter table add index statement.
* [mysql] introduce TMySQLCreateTableOption to get create table option easily.
* fix a typo: 	gudusoft.gsqlparser.pp.stmtformattor.FormattorFactory; o -> e (stmtformattor.FormattorFactory)
* [mysql] able to get full parse tree information of drop table correctly.
* [sql server] able to support sql server single quote escape
* able to get table name, colum list and index type for create index statement in all supported databases.
* [oracle] able to access renamed table name via TAlterTableOption.
* enhanced TAnalyticFunction class to support getKeepDenseRankClause, getOrderBy and getPartitionBy_ExprList.
* [netezza] fix a bug can't tokenlize identifier start with $ character.
* [oracle pl/sql] support language java in procedure inside package body
* CTE can be parsed correctly in subquery.

======================================
[version Java 1.4.0.3][2012-01-10]
* support MDX, syntax check only.
* support Netezza SQL, fully supported statement: select/insert/delete/update/truncate/create view/create table
* support this Oracle sql: SELECT B.* FROM ((SELECT 2 FROM DUAL) B)
* fix a bug in teradata, with check option don't had start and end token.
* add TCTE.getPreparableStmt, so it will return one of following statement: subquery/insert/update/delete
* support wrapped Oracle plsql
* support "-" character in identifier of DB2.
* support having clause without group by clause
* support execute_immediate_statement in forall statement of Oracle plsql.
* able to recognize connect sqlplus command if it after a sql statement not ended with semicolon.
* rewrite TParseTreeNode.toString() method, make it more robust to modify parse tree node.
* Introduce  public String TTable.getFullNameWithAliasString()
* AND,OR,NOT keyword in expression  can be obtained from getOperatorToken() of TExpression


======================================
[version Java 1.3.8][2011-11-29]
* support length of long datatype of Oracle.
* fix a bug that can't handle Oracle substitution variable that followed with semicolon.
* support dynamic string in open cursor of Oracle.
* add 'accept' method for class:	TViewAliasClause,	TViewAliasItem,	TViewAliasItemList.
* support drop Public synonym
* able to handle nested procedure/function correctly in Oracle PLSQL package.
* fix a bug that after parse this sql: SELECT 'Test' FROM dual, System.out.println(table.toString()); will raise an null exception.
* support qualified type name of DB2.
* support period function of Teradata:  INTERVAL (period_expression) interval_qualifier
* support new logical predicates of Teradata: IS UNTIL_CHANGED/IS NOT UNTIL_CHANGED
* columns in SQL Server OGC Methods on Geography Instances will be recoginzed correctly.
* offset and row count of limit clause of MySQL will be handled correctly.
* able to get oracle hint from select statement.
* join clause in a hiberarchy level processed correctly.


[version Java 1.3.4][2011-07-28]
* support merge statement of Oracle, SQL Server and DB2.

[version Java 1.3.3]
* support function call in IN condition.


[version Java 1.3.1][2011-06-23]
* support postgresql(select/insert/delete/update/create table/create view)
* in SQL statement: select * from tab, * was treated as a column name of tab.
* column a,b,c in this SQL statement was treated as un-determined of tableB
	SELECT a, b, c
	FROM tableB, tableA
* better support to parse plsql package
* plsql, support label before a function call
* support plsql inner procedure
* oracle, support concatenating two strings (or a string and a variable) in an open cursor statement.
* oracle, support l_val(1) in using clause
* oracle, enhanced support for table variable
* add accept() method for TParameterDeclaration and TParameterDeclarationList
* add missing getters : getExpr(), getRollupCube(), and  getGroupingSet() for TGroupByItem
* oracle, support $ in bind variable
* oracle, support pl/sql code calling a java method.
* microsoft access, fully support DROP TABLE statement
* add labelName and endlabelName property in TPlsqlStmt,
* add labelName and endlabelName property in TStatementSqlNode, TCustomSqlStatement
* add labelName property in  TCustomSqlStatement
* add gotolabelName property in  TPlsqlGotoStmt
* add exitlabelName property in  TPlsqlExitStmt 
* oracle, fix a bug than can't support when condition in create trigger statement.
* oracle, support float number: 1.0E28 in MAXVALUE clause of create sequence SQL statement.

[version Java 1.2.9][2011-06-07]
* db2, support with check option.
* db2, fix a bug that select statement with "with clause" can't be used in create view statement.
* teradata, group by clause can appeared before where clause.
* teradata, with clause can appeared before order by clause.
* teradata, support create/replace view statement.
* teradata, fix a bug not support SEL keyword.
* teradata, support entire LOCKING/LOCK clause.
* teradata, support named alias like: 
	SELECT Name, ((Salary + (YrsExp * 200))/12) (NAMED Projection)
	FROM Employee
	WHERE DeptNo = 600 AND Projection < 2500;
* teradata, support PERIOD Functions and Operators.
* introduce a new property TObjectName.isTableDetermined().
* Introduce a new method TGSqlParser.setSqlInputStream(InputStream sqlInputStream), able to set input sql via InputStream.


[version Java 1.2.6][2011-05-04]
* fix a bug in demo: columnsInResultColumn, that can't find column in function arguments.
* [changes] replace following constant integer with enum type: ETableSource

public class TFromTable
    public final static int ftt_objectname = 1;
    public final static int ftt_subquery = 2;
    public final static int ftt_tableExpr = 3;
    public final static int ftt_join = 4;
    public final static int ftt_function = 5; //sql server
    public final static int ftt_containsTable = 6; //sql server
    public final static int ftt_freetextTable = 7;//sql server
    public final static int ftt_openrowset = 8;//sql server
    public final static int ftt_openxml = 9;//sql server
    public final static int ftt_opendatasource = 10;//sql server
    public final static int ftt_openquery = 11;//sql server
    public final static int ftt_datachangeTable = 12;//db2

* support this Oracle SQL syntax:
  alter table testtable modify mycolumn null;
  

[version Java 1.2.5][2011-04-28]
* support Oracle partition by range clause:

[version Java 1.2.4][2011-04-26]
* Fix a bug can't handle Oracle translate function correctly.
   select fp.id from tab1 fp where trim(translate(fp.val,'-0123',' ')) is null

[version Java 1.2.3]
* query size limitation in trial version was increased to 10000 characters which is adequate to evaluate for the most sql script.
* support this oracle sql syntax:
  alter table testtable modify (mycolumn  null); 


[version Java 1.2.1][2011-04-19]
* support float constant in oracle like 1.57F
* support oracle create table sytnax like this:
	create table myTable (
		myColumn number  default null null
	);


[Java version 1.2.0][2011-04-14]
* rewrite all demos.
* add some public getter functions of TAlterTableOption.
* [changes]
   
   replace following integer constant with enum type: EJoinType

    // join type
    public static int join_cross = 1;
    public static int join_natural = 2;
    public static int join_full = 3;
    public static int join_left = 4;
    public static int join_right = 5;
    public static int join_fullouter = 6;
    public static int join_leftouter = 7;
    public static int join_rightouter = 8;
    public static int join_inner = 9;
    public static int join_crossapply = 10;
    public static int join_outerapply = 11;
    public static int join_straight = 12;
    public static int join_union = 11;
    public static int join_nested = 20;
    public static int join_natural_left = 30; //mysql
    public static int join_natural_right = 32; //mysql
    public static int join_natural_leftouter = 34; //mysql
    public static int join_natural_rightouter = 36; //mysql

   replace following integer constant with enum type: EConstraintType

    // constraint type
    public final static int constraint_type_notnull = 1;
    public final static int constraint_type_unique = 2;
    public final static int constraint_type_primary_key = 3;
    public final static int constraint_type_foreign_key = 4;
    public final static int constraint_type_check = 5;
    public final static int constraint_type_reference = 6;
    public final static int constraint_type_default = 7; // valid in sql server
    public final static int constraint_type_index = 8; //mysql
    public final static int constraint_type_key = 9; //mysql

    public final static int constraint_type_fake_null = 8;
    public final static int constraint_type_fake_collate = 9;
    public final static int constraint_type_fake_identity = 10;
    public final static int constraint_type_fake_rowguidcol = 11;
    public final static int constraint_type_fake_auto_increment = 12 ; //mysql
    public final static int constraint_type_fake_comment = 13 ; //mysql
    public final static int constraint_type_fake_db2 = 14 ; //db2


   replace following integer constant with enum type: EAlterTableOptionType

   // TLzAlterTableOptionType
    public final static int atoAddColumn = 0;
    public final static int atoModifyColumn = 1;
    public final static int atoAlterColumn = 2;
    public final static int atoDropColumn = 3;
    public final static int atoSetUnUsedColumn = 4;
    public final static int atoDropUnUsedColumn = 5;
    public final static int atoDropColumnsContinue = 6;
    public final static int atoRenameColumn = 7;
    public final static int atoChangeColumn = 8;
    public final static int atoRenameTable = 9;
    public final static int atoAddConstraint = 10;
    public final static int atoAddConstraintIndex  = 11;
    public final static int atoAddConstraintPK = 12;
    public final static int atoAddConstraintUnique = 13;
    public final static int atoAddConstraintFK = 14;
    public final static int atoModifyConstraint = 15;
    public final static int atoRenameConstraint = 16;
    public final static int atoDropConstraint = 17;
    public final static int atoDropConstraintPK = 18;
    public final static int  atoDropConstraintFK = 19;
    public final static int  atoDropConstraintUnique = 20;
    public final static int  atoDropConstraintCheck = 21;
    public final static int  atoDropConstraintPartitioningKey = 22;
    public final static int  atoDropConstraintRestrict = 23;
    public final static int  atoDropConstraintIndex = 24;
    public final static int  atoDropConstraintKey = 25;
    public final static int  atoAlterConstraintFK = 26;
    public final static int  atoAlterConstraintCheck = 27;
    public final static int  atoCheckConstraint = 28;

    public final static int  atoOraclePhysicalAttrs  = 29;
    public final static int   atoOracleLogClause = 30;
    public final static int  atoOracleTableP = 31;
    public final static int  atoMssqlEnableTrigger = 32;
    public final static int  atoMySQLTableOptons = 33;
    public final static int  atoDb2PartitioningKeyDef = 34;
    public final static int  atoDb2RestrictOnDrop = 35;
    public final static int  atoDb2Misc = 36;
    public final static int  atoUnknown = 50;

[.NET version 2.0.9][2011-04-13]
* TSourceToken.Location can be used to check which clause a column belongs to.
*	datepart argument in DATEADD, DATENAME,DATEDIFF,DATEPART function 
  wouldn't be recognized as a column name.


[Java version 1.1.12][2011-04-12]
* MySQL, add syntax support for natual left join,
  natual left outer join,natual right join,natual right outer join

[Java version 1.1.11][2011-04-08]
* able to find out what clause a TObjectName belongs to.
* [changes]introduce a new enum: ESqlClause replace following integer constant in TBaseType
    public final static int unknownClause = 0;     
    public final static int selectClause = 1;
    public final static int whereClause = 2;
    public final static int havingClause = 3;
    public final static int groupbyClause = 4;
    public final static int orderbyClause = 5;
    public final static int joinCondition = 6;
    public final static int joinClause = 7;
    public final static int hierarchicalClause = 8;
    public final static int computeClause = 9;
    public final static int topClause = 10;
    public final static int outputClause = 11;
    public final static int loc_deletestmt = 12;
    public final static int loc_updatestmt = 13;
    public final static int loc_insertstmt = 14;
    public final static int updateSetClause = 15;
    public final static int insertColumnClause = 16;
    public final static int insertValuesClause = 17;
    public final static int intoClause = 18;
    public final static int qualifyClause = 19;
    public final static int sampleClause = 20;
    public final static int teradataWithClause = 21;
    public final static int limitClause = 22;
    public final static int valueClause = 23;

* support Oracle MULTISET operator


[Java version 1.1.10][2011-04-06]
* support Oracle translate function, qualified type name in Oracle sql.
* support Oracle treat function.
* support Oracle extract(XML) function, introduce new funtion type: TFunctionCall.fntExtractXML


[Java version 1.1.9]
* support Oracle syntax like this:
	update zzz
	set (id) = (select 1, 'Test' from dual);
	
* Type keyword can be column name in update statement.
* fix a bug can't handle comment like this where clause:  2= 1/*Comment*/+1;
* support deterministic keyword in function declaration.
* support java language call specification in plsql function declaration.
* support => operator in open statement
* support inner procedure in procedure declaration of Oracle PLSQL


[.NET version 2.0.7]
* Fix a bug that SQL statement inside plsql block will be visited twice when iterate SQL statement using visitor pattern.

[Java version Java 1.1.7]
* Fix a bug that not handle set/create index/alter table statement in sql server block.

[.NET version 2.0.6]
* [2011-03-30][oracle, format option] gfmtopt.BEStyle_Function_BodyIndent was replaced by BEStyle_BlockIndentSize


[Java version 1.1.3][2011-03-16]
* Introduce new class: TBlockSqlStatement: base class of all sql statement class that includes multiple sql statement.
* Introduce new class: TStoredProcedureSqlStatement: base class of all stored procedure class such as create function/procedure/trigger
* Introduce new class: TOracleStoredProcedureSqlStatement: base class of all oracle stored procedure function/procedure/trigger/package/anonymous block
* [2011-03-10][MySQL] Support Full-Text Search Functions, Match...AGAINST,


[.NET version 2.0.5][2011-03-08]
* RTF output, when keep layout, fix a bug can't preserve space before linebreak.
* [2011-03-23] Add support for MS Access transform, parameters statement


[java version v1.1.3][2011-03-10]
* Support MySQL Full-Text Search Functions, Match...AGAINST

[java version v1.1.2][2011-03-08]
* SQL Server keyword can't be column name.
* Add TAliasClause.getColumns() to get columns in alias clause like this:
 as alias_name(column1,column2)

[java version v1.1.1][2011-03-03]
* add a demo to illustrate how to use sql parser to prevent sql injection.
* view alias name in create view is available in Oracle, sql server, DB2 and MySQL.
* change class name from 
	TOracleViewAliasClause to TViewAliasClause
	TOracleViewAliasItemList to TViewAliasItemList
	TOracleViewAliasItem to TViewAliasItem

*	change value of enum ENodeType from 	
	T_OracleViewAliasItem to T_ViewAliasItem
	T_OracleViewAliasItemList to T_ViewAliasItemList
	T_OracleViewAliasClause to T_ViewAliasClause

* fix a bug that expression will be traversed in-correctly in multitimes when call TExpression.postOrderTraverse
* fix a bug can't handle comment like this:
	SELECT a,b /*--*/ FROM YYY

version 2.0.4 (2011-02-23)
* Support BEGIN;...END; syntax of SQL Server. 
* Add 3 new format options: gfmtopt.expr_parenthesis_innewline, gfmtopt.expr_remove_redundant_brackets,gFmtOpt.Insert_Parenthesis_in_separate_line 
* Format comment in parameters declaration of stored procedure was enhanced 
* Having clause before group by clause in select statement was supported. 
* Syntax like this in PL/SQL was supported: Insert into g_price_marginal_rule values marginal 
* Support qualified name like this: dbo.##BondDetail2. 
* Fully support of SQL Server truncate table. 
* Tested on .NET framework 4, and fixed a minor bug. 
* Add a new function lzbasetype.AutoDetectCharacterSet to detect sql file encoding. 
* Easy to check what's type of sql statement those class were represented by using 
 SqlStatementType of TMssqlIfElse,TMssqlCreateprocedure, TMssqlCreatefunction and TMssqlCreatetrigger. 
 
* Introduce a new class: TMssqlDropProcedure 
* Sql statement in exec_string can be fetch via execute statement's ChildNodes. 
* Add a new demo: affectedObject to determine affected database objects in sql file. 
* refine alter option in alter table statement. and add some new code in analyzscript to illustrate how to use this option. 
* add new property: TLzAlterTableOption._ndColumnName 
* remove TLzAlterTableOption.ColumnConstraintList 
* Introduce a new class: TLz_AttrList, represents a list of qualified name 
* TLzConstraint.ConstraintColumnList was removed, and replaced with ColumnNameList 
* New property: TLz_Attr.sortToken, this property was used when column names in 
primary key/foreign key had sort(asc,desc) information.(this is for sql server only) 

* fix a bug that missing distinct/top clause information in TSelectSqlStatement.GetAsXmlText 
* [sql server] full support of SQL Server Drop Index statement, and add demo code in analyzescript to show how to use TMssqlDropIndex. 


[java version v1.1.0][2011-02-20]
* 10 times faster if create more than 100 instance of SQL Parser.
* All getRightOperand() and getLeftOperand() should return type TExpression if not null, 
	so we remove TParseTreeNode getLeftNode(), TParseTreeNode getRightNode()
	TInExpr and TExprList shoud be leaf node of a new TExpression
* Able to remove colums from select list, and rebuild sql.
* Able to add new column to select list, and rebuild sql.
* Able to add where clause to select statement.
* Able to add order by item, the order by clause must be already exists.
* Able to remove an order by item,remove all items means remove the whole order by clause.
* Improved API of PL/SQL loop statement.
* Parser don't recover from FROM keyword.

Java Version 1.0.0 (2011-01-06)
* This is the first official released Java version as stable as .NET version, support Oracle, SQL Server, DB2, MySQL, Access, and Teradata. 
  All features in .NET version were available except sql formatter. 


version 2.0.0 (2011-01-06)
* Change license mode to enterprise edition license(support all following database: oracle, sql server, db2, mysql, 
   and enable all developers in a physical site to use this library) and professional edition 
   license(support one of following database: oracle, sql server, db2, mysql, and enable one developer in a physical site to use this library). 
* If you need to distribute this library together with your application to end users, please contact sales@sqlparser.com for a distribution license. 

* [Oracle] support comment on statement. 
* [Oracle] support create synonym statement. 
* [Oracle] support compress/uncompress clause in physical_properties. 
* [Oracle] able to get sequence name and options. 
* [internal] adjust max_matches value to reduce usage of memory, improve performance. 


version 1.12.17 (2010-12-02)
* introduce a new property: TLzField.DisplayName, this property returns alias name of
  a column if any, otherwise, return column name.
* fix bug that TLzField.Name returns a dot before fieldname.
* support "not for replication" clause in IDENTITY property of sql server.
* intorduce 9 format options
	gFmtOpt.IntoClauseInNewline
	gFmtOpt.WhereClauseInNewline
	gFmtOpt.GroupByClauseInNewline
	gFmtOpt.OrderByClauseInNewline
	gFmtOpt.HavingClauseInNewline
	gFmtOpt.Update_Columnlist_Style 
	gFmtOpt.LinefeedsAndOr_option
		control and/or keyword in condition before newline or after newline or no linebreak.
 	gFmtOpt.Select_Groupby_Style
	gFmtOpt.Select_Orderby_Style

* Handle "TOP X" the same as "DISTINCT"
* [sql server] support Sparse Columns of sql server 2008.
* [sql server] support SQL Server 2008 new introduced several extensions to the GROUP BY clause:
	GROUPING SETS, CUBE, and ROLLUP subclauses of the GROUP BY clause and the GROUPING_ID function.
* [sql server] support delete in merge not matched clause.
* [sql server] support sql server 2008 HIERARCHYID Data Type
* [sql server] support Compound Assignment Operators
* [sql server] support new sql server 2008 spatial function like: ([geom].Reduce(10)).STAsText()
* [sql server] support the geometry and geography feature of SQL Server 2008.
* [oracle] support oracle XMLQUERY sytnax.
* able to control format of expression in case expression.
* better support to format case expression.
* < character in html output not show correctly.


version 1.12.15
* fix bug: can't process empty block in SQL Server like this:
	BEGIN CATCH         
	END CATCH         

* support SQL Server kill statement.
* new tokentype: ttUserCustomized.
* new element of TLzHighlightingElement: sfkUserCustomized
* new event handle: TGSqlParser.BeforeGenerateFormattedSQL
	will be fired before generate formatted SQL when a event hanlder was set.
	it can be useful if you want to change color of some source token work together with ttUserCustomized,sfkUserCustomized
	please check customizedColor demo shipped together with this library to see how to customize
	color of certain tokens in RTF and HTML output.
	
* rtf output support multibytes character set language like chinese, korean.
* fix a bug in TLzCaseExpression.GetAsXmlText.


version 1.12.14
* sql formatter ugly mode, when convert to single line, remove extra spaces in output sql.
* support ; character before CTE of SQL Server.

version 1.12.13
* support following syntax:
	IF Update (OrderTypeID) BEGIN
	end
	else
	begin
	end

* able to recognize table alias in delete, update statement correctly.
	update A set A.text='x'
	from myTable A
	join otherTable B on A.Id=B.Id
	
	delete  A
	from  myTable A
	join otherTable B on A.Id=B.Id

* support readonly keyword in variable declare of SQL Server.
* support string like this of ms access: #4/1/2008 3:09:29 PM#
* fix a bug that can't find hint in select after comment like this:
	SELECT /* TEST SQL */ /*+ FULL(EMP) */ EMPNAME FROM EMP WHERE EMPID = 1;
	
* can't handle if statement correctly if there is a case...end(with else) expression inside.
* \ character is not a escape char of oracle string literal.
* fix a bug that remove space around DEFAULT keyword in following sql when WSPadding_OperatorArithmetic is false.
	PROCEDURE report_create (v_ts IN DATE, p_msg IN VARCHAR2,p_file_mode IN VARCHAR2 DEFAULT 'A');

* subtype keyword can be a qualified name in plsql.
* column datatype can't be empty in create table statement.
* default and null keyword can't be a datatype name.
* support connect_by_root unary operator in Oracle.
* able to detect syntax error of select in cursor declare of plsql.
* support mod operator in plsql.

version 1.12.11
* support qualified name of SQL Server pivot column.
* bug of processing unpivot clause in from clause was fixed.
* qualified data type name was supported.
* support variable of LANGUAGE @language in CONTAINSTABLE clause.
* output can be table alias in insert statement.
* html output was checked as XHTML 1.0 Strict.
* when convert SQL to vb and vb string builder, change escape char of " from \ to ".
* able to handle 0X8000 literal.
* able to handle 
	(SELECT Name, ListPrice FROM Production.Product WHERE ProductID = 720)
	in values clause of insert statement like this:
	
	INSERT INTO dbo.MyProducts (Name, ListPrice)
	VALUES ('Helmet', 25.50),
    	   ('Wheel', 30.00),
       	(SELECT Name, ListPrice FROM Production.Product WHERE ProductID = 720);

* new format option: gfmtopt.AlignJoinWithFromKeyword.
* partially support of sql server merge statement.
* MySQL stored procedure such as create function/procedure/trigger can be ended by string like "end;"
* start with and connect by clause were formatted correctly.
* support return keyword in declare statement of MySQL.
* fix a bug when select_columnlist_style = asWrapped, following SQL is not formatted correctly.
	SELECT last_name,a+(select a,b from c)
	FROM   employees

* fix a bug that can't process format option correctly: gfmtopt.FunctionCall_Parameters_Style = stacked
* better support to format multiline comments in html and rtf output.
* new format option: gfmtopt.FunctionCall_Parameters_Style, gfmtopt.FunctionCall_Parameters_Comma control parameters layout of function call.
* new foramt option: gfmtopt.NoEmptyLinesBetweenMultiSetStmts, able to control empty lines between consecutive set/declare statements in sql server.
* Unify the way to access statements in plsql statement (TPlsqlStatement) by visiting childnodes.
* fix a bug that can't hanlde literal like '%\_INF'.
* support concat operator in select list expression of DB2.
* Change default value of format option case_identifier from  coLowercase to coNoChange;
* IDENTITY keyword can't be used as typename, but gsp can't detect this error.
* right keyword can be arguments of function of Oracle.
* year keyword can be field name of TYPE.
* year keyword can be plsql column name like tablename.year%type
* RIGHT keyword can be column name in into clause of insert statement of Oracle.
* better support to format multiline comments.
* support dbms_lobs.open() function of Oracle.
* support last_value, first_value function of Oracle.

version 1.12.7
* execute statement can be at the top level of plsql script.
* Access Violation to process this SQL which is syntax invalid.
	if select object_id('cr_trd_me_110') is not null
  	drop procedure cr_trd_me_110


version 1.12.6
* improved: yyaction in lzyaccXXXsql unit was splitted into small functions by program utils\split_yyaction\split_yyaction.exe
	this speed up .NET version under vista (it takes 10 seconds to parse a simple SQL before, now it's about 2-3 seconds)


version 1.12.5
* [oracle] fixed: support this syntax: ALTER TABLE _name_of_table MODIFY _name_of_field NUMBER(5,0)
* [lex] improved: improve max_matches from 1024*20*10 to 1024*20*10*10, able to deal big quoted string.
* [sybase] improved: +1 was supported like this: EXEC Proc "param1", "param2", +1
* [sybase] improved: multitable in drop table.
* [mysql] fixed: decimal datatype was supported in cast function.
* [oracle] fixed: update clause and insert clause can be optional in merge statement.
* [oracle] improved: Able to recovery from a keyword error from plsql by using OnParserTokenError event.


version 1.12.4
* fixed: Merge statement table alias is optional.
* support syntax: FOR R1 IN C1() LOOP, no parameters in C1().
* type keyword can be in function parameters, variable name in for clause.
* support syntax: WHEN NOT MATCHED THEN is preceded by WHEN MATCHED THEN  in merge statement.
* comment keyword can be used in typename
* supported syntax: Lob_storage_clause in column_properties of create_table_properties.
* NUMBER(*,0) was supported in create table statement of Oracle.
* pipe row statement is supported in create function statement.
* pipedlined is supported in create function statement.
* improved: all DoParseStatement, DoParse functions return value.
* improved: all parse error messages log into top level tcustomsqlstatement.
* partially support log clause of create table statement.
* support pipedlined in return type of function in create package
* supported following Oracle sql syntax:
	create table tablename tablespace tn nologging parallel as select f from t
	
[2009-11-24][general] fixed: select statement in create table not indent correctly.
Remove this duplicate code in p3_linebreak, already exists in p3_subnode
   if assigned(SelectStmt) then
    begin
      selectStmt.ppv3(self,true,gfmtopt.IndentLen,0,nil);
    end;

version 1.12.3
* fixed: TMssqlIfElse.ProcessFuncExpr, infinite loop cause program halt for some sql.
* support for "if not update(colid)" in create trigger.


version 1.12.2
* method_specifier in create procedure was supported.

version 1.12.1
* able to beautify query inside openrowset function.
* --begin_no_format align with previous sql statement.
* fixed: rtf output can not handle multiline string correctly.
* fixed: emptylines between multiline comments and sql statement not handle correctly.


version 1.12.0
* able to show line number of formatted sql.
* better support for AndOrUnderWhere format option.
* support recompile hint in option of SQL Server.
	select top 10 * from aa	option(recompile)
* mssql xml method query(),value(),exist(),modify(),nodes() keep lowercase no matter what case option was choosen for function case option.
* sql formatter, from keyword in from clause of update statement not in newline.
* sql formatter, into clause start in a newline.
* better support for --begin_no_format, --end_no_format format directive.

version 1.11.1
* support this SQL syntax of Sybase
	SELECT 
		sinkingtable.Principal 
	FROM 
		kplus..BondsSchedule sinkingtable(INDEX BondsScheduleIdx1) 

* able to handle drop table statement of DB2.
* when emptyline=mergeintoone, insertblanklineinbatchsqls is false, emplty lines after
select in create function is removed but not merge into one.