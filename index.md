---
layout: page
excerpt: "Documents and demos for general SQL parser"
show_excerpts: true
paginate: true
entries_layout: list
---

### Introduce

General SQL Parser is a Java/.NET library. It provides a rich set of APIs to parse, decode, analyze and rewrite SQL scripts. 
Supports more than 10 major database platforms by covering the most used SQL syntax of those databases including PL/SQL.

##### Basic features
- Offline SQL syntax check
  Validates SQL syntax without connecting to a database.
  
- Fully access to SQL query parse tree  
  After parsing the SQL, preparing a detailed SQL parse tree node structure, accessing, modifying and rewriting SQL segment have never been so easy.
  
- SQL formatter
  Produce clean SQL layout to improve SQL readability.
  
##### Advanced features

- Extract table column from SQL

  Scan, analyze SQL scripts and stored procedures to find relationship between table and column in various clauses like where, join condition and etc.
  
- Data lineage and impact analysis  
- SQL rewrite technology
- SQL converter among the major database vendors
- Anti SQL injection
- Fully output of the SQL syntax tree in XML

### Get started
- [Install and use the Genearl SQL Parser package using the dotnet CLI](/gsp-dotnet-library-install.html)

### Tutorials

{% for item in site.tutorials %}
  - <a href="{{ item.url }}">{{ item.title }}</a>
{% endfor %}

### Inside SQL parse tree

### API Reference
- [Java doc for the library](http://sqlparser.com/kb/javadoc)

### FAQ
- [General SQL Parser FAQ](gsp-faq.html)

### More demos and use cases

### Contact
-  <a href="#" onclick="window.FreshWidget.show()">CLICK HERE FOR HELP</a>

