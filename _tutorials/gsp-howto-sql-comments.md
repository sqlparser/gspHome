---
layout: page
title: "How to process commnets used in the SQL scripts"
excerpt: "Parsing of comments and accessing of the block and inline comments of a SQL script"
categories:
  - "How to"
---

Comments used in the SQL script clarify the purpose or effect of the SQL statements. It will be ignored by the database server during the execution.
Single line comments start with `--`. Multi-line comments start with `/*` and end with `*/`. Some databases have their extension to the ANSI/ISO standard,
Braces `{ }` are the Informix extension to the ANSI/ISO standard. Start a line comment from a `#` character to the end of the line is the MySQL extension.

{% include toc %}
	
### Parsing SQL comment in GSP

After parsing the SQL script, single/multi line comment inside SQL script is recoginzed as a source token(`TSourceToken`) by GSP 
with `tokentype` set to `ttsimplecomment` or `ttbracketedcomment`, 
so you can find comment inside a SQL statement by iterating the `TCustomSqlStatement.sourcetokenlist` or `TGSqlParser.getSourcetokenlist()` 
if you need to find comment in the whole SQL script.

However, comment is not included in the syntax tree like other SQL clauses which makes it difficult to link the comment to a specific SQL clause. 
But it's still possible to know the relation between comment and SQL clause by using the position information 
of the comment( __TSourceToken.lineNo__,  __TSourceToken.columnNo__) and  start/end token( __TSourceToken.lineNo__,  __TSourceToken.columnNo__) of the SQL clause.

It's possible to link comment to the SQL clause by using line and column position provided by GSP. Below is the demo list the comments to the select list.

```java
import gudusoft.gsqlparser.*;
import gudusoft.gsqlparser.nodes.TParseTreeVisitor;
import gudusoft.gsqlparser.nodes.TResultColumn;
import junit.framework.TestCase;

public class testComment extends TestCase {

	public void test0(){
		TGSqlParser sqlparser = new TGSqlParser(EDbVendor.dbvoracle);
		sqlparser.sqltext = "SELECT last_name,                    -- select the name\n" +
				"    salary + NVL(commission_pct, 0),-- total compensation\n" +
				"    job_id,                         -- job\n" +
				"    e.department_id                 -- and department\n" +
				"  FROM employees e,                 -- of all employees\n" +
				"       departments d\n" +
				"  WHERE e.department_id = d.department_id\n" +
				"    AND salary + NVL(commission_pct, 0) >  -- whose compensation \n" +
				"                                           -- is greater than\n" +
				"      (SELECT salary + NVL(commission_pct,0)  -- the compensation\n" +
				"    FROM employees \n" +
				"    WHERE last_name = 'Pataballa')        -- of Pataballa.";
		assertTrue(sqlparser.parse() == 0);

		// fetch all comments
		for(int i=0;i<sqlparser.getSourcetokenlist().size();i++){
			TSourceToken st = sqlparser.getSourcetokenlist().get(i);
			if ((st.tokentype == ETokenType.ttsimplecomment)||(st.tokentype == ETokenType.ttbracketedcomment)){
				System.out.println(st.toString());
			}
		}

		
		for(int i=0;i<sqlparser.sqlstatements.size();i++){
			TCustomSqlStatement sqlStatement = sqlparser.sqlstatements.get(i);
			analyzeStmt(sqlStatement);
		}

	}

	void analyzeStmt( TCustomSqlStatement stmt ){
		System.out.println(stmt.sqlstatementtype);
		selectItemVisitor itemVisitor = new selectItemVisitor();
		stmt.acceptChildren(itemVisitor);

		for ( int i = 0; i < stmt.getStatements( ).size( ); i++ )
		{
			analyzeStmt( stmt.getStatements( ).get( i ) );
		}
	}
}

class selectItemVisitor extends TParseTreeVisitor {

	public void preVisit(TResultColumn node){
		System.out.println("--> select item: " + node.toString());
		TSourceToken endToken = node.getEndToken();
		TSourceToken commentToken =  searchComment(endToken);
		if (commentToken != null){
			System.out.println("comment: "+commentToken.toString());
		}

	}

	TSourceToken searchComment(TSourceToken currentToken){
		// check next solid token to see whether it is a comment
		TSourceToken resultToken = null;
		TSourceToken st = currentToken.nextSolidToken(true);
		if (st != null){
			if ((st.tokentype == ETokenType.ttsimplecomment)||(st.tokentype == ETokenType.ttbracketedcomment)){
				resultToken = st;
			}else if (st.tokencode == ','){
				resultToken = searchComment(st);
			}
		}

		return resultToken;
	}
}
```

 

### Oracle instructions/hints

Oracle uses comments in a SQL statement to pass instructions, or hints, to the database.
	
	```
	{DELETE|INSERT|SELECT|UPDATE} /*+ hint [text] [hint[text]]... */
	or
	{DELETE|INSERT|SELECT|UPDATE} --+ hint [text] [hint[text]]...
	```

The hint in select statement can be fetched by using `TSelectSqlStatement.getOracleHint()` method. There is no specific method to get the hint in delete/insert/update statement yet.
	
### MySQL-specific code

MySQL Server supports some variants of C-style comments. These enable you to write code that includes MySQL extensions, but is still portable, by using comments of the following form:

	```
	/*! MySQL-specific code */ 
	```

There is no specific method to get the MySQL-specific code yet.	
	
	
Reference:
* [Informix](https://www.ibm.com/support/knowledgecenter/en/SSGU8G_12.1.0/com.ibm.sqls.doc/ids_sqs_0210.htm)
* [MySQL](https://dev.mysql.com/doc/refman/8.0/en/comments.html)

 
 