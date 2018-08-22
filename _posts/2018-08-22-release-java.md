---
layout: page
title: "General SQL Parser Java version released 2018-08-22"
categories:
  - changelog
---

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
 
Please more changelog, please [check here](/changelog/changelog-java/).