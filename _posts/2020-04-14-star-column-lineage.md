---
layout: post
title: "The star column (*) in the process of the column level lineage"
categories:
  - data-lineage
---

How to handle the star column (*) during the process of the column level lineage

```sql
create view v as select * from t;
```

The SQL will create a view: `v` by using the column name in the table `t`.
However, without the additional metadata, the GSP doesn't know the column name in table `t`.
So, use `*` to link the relation between view and table like this: `t.* -> RS-1.* -> v.*`

```xml
<relation id="1" type="fdd" effectType="select">
  <target id="6" column="*" parent_id="5" parent_name="RS-1" coordinate="[1,25],[1,26]"/>
  <source id="3" column="*" parent_id="2" parent_name="t" coordinate="[1,25],[1,26]"/>
</relation>
<relation id="2" type="fdd" effectType="create_view">
  <target id="9" column="*" parent_id="8" parent_name="v" coordinate="[1,25],[1,26]"/>
  <source id="6" column="*" parent_id="5" parent_name="RS-1" coordinate="[1,25],[1,26]"/>
</relation>
```

The GSP can do a little better if the SQL is something like this:
```sql
create view v as select * from t where column1 + column2 > 0;
```

[Visualize the SQL](https://www.gudusoft.com/sqlflow/#/?setting=01010&dbv=mssql&sql=create%20view%20v%20as%20select%20%2A%20from%20t%20where%20column1%20%2B%20column2%20%3E%200%3B)

The GSP will know `column1` and `column2` must belonged to table `t`, so this relation is created:
```xml
<relation id="1" type="fdd" effectType="select">
  <target id="7" column="*" parent_id="6" parent_name="RS-1" coordinate="[1,25],[1,26]"/>
  <source id="3" column="column1" parent_id="2" parent_name="t" coordinate="[1,40],[1,47]"/>
  <source id="4" column="column2" parent_id="2" parent_name="t" coordinate="[1,50],[1,57]"/>
</relation>
```

and the resultset outputed in the `select *` must include `column1` and `column2`.

```xml
<relation id="1_0" type="fdd" effectType="select">
  <target id="7_0" column="column1" parent_id="6" parent_name="RS-1" coordinate="[1,25],[1,26]"/>
  <source id="3" column="column1" parent_id="2" parent_name="t" coordinate="[1,40],[1,47]"/>
</relation>
<relation id="1_1" type="fdd" effectType="select">
  <target id="7_1" column="column2" parent_id="6" parent_name="RS-1" coordinate="[1,25],[1,26]"/>
  <source id="4" column="column2" parent_id="2" parent_name="t" coordinate="[1,50],[1,57]"/>
</relation>
```

Please note that the relation id is in the format of `1_index`, where the index is 0,1. 
This means that those columns are not really listed in the select list, but derived from the star column in the select list
whose relation id is `1`.

Also, `column1` and `column2` listed in the view: `t` is derived from the star column with the following relation map.

```xml
<relation id="3_0" type="fdd" effectType="create_view">
  <target id="10_0" column="column1" parent_id="9" parent_name="v" coordinate="[1,25],[1,26]"/>
  <source id="7_0" column="column1" parent_id="6" parent_name="RS-1" coordinate="[1,25],[1,26]"/>
</relation>
<relation id="3_1" type="fdd" effectType="create_view">
  <target id="10_1" column="column2" parent_id="9" parent_name="v" coordinate="[1,25],[1,26]"/>
  <source id="7_1" column="column2" parent_id="6" parent_name="RS-1" coordinate="[1,25],[1,26]"/>
</relation>
<relation id="3" type="fdd" effectType="create_view">
  <target id="10" column="*" parent_id="9" parent_name="v" coordinate="[1,25],[1,26]"/>
  <source id="7" column="*" parent_id="6" parent_name="RS-1" coordinate="[1,25],[1,26]"/>
</relation>
```