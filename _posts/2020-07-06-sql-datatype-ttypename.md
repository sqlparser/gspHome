---
layout: page
title: "SQL Datatype and TTypeName"
categories:
  - sql-syntax
  - get-started-cn  
---

SQL Datatype and TTypeName

SQL的数据类型，GSP中的对应类：TTypeName。

### SQL Datatype的类型
TTypeName 表示SQL中的数据类型，例如：
```sql
char(10),
int,
float(24),
decimal(8,2)
```

#### 基本属性
以表示 `decimal(8,2)`为例，TTypeName的基本熟悉值如下：
```
getDataType() = decimal_t
toString() = decimal(8,2)
getDataTypeName() = decimal
```

#### 扩展属性

扩展属性仅适用于部分特定的datatype。

##### getLength()
以 `char(10)`为例
```
getLength() = 10
```

##### getPrecision(), getScale()
以 `decimal(8,2)`为例
```
getPrecision() = 8
getScale() = 2
```


### 参考资料
SQL2003 datatypes 的详细列表见 "SQL in a Nutshell, 3rd Edition" p30, Table 2-8. SQL2003 categories and datatypes

### EDataType的完整列表
```java
package gudusoft.gsqlparser;

/**
* @since v1.4.3.0
*/

public enum EDataType {
    unknown_t,
    /**
     * user defined datetype
     */
    generic_t,
    bfile_t,
    /**
     * ansi2003: bigint
     * postgresql
     */
    bigint_t,
    /**
     * ansi2003: blob
     */
    binary_t,
    binary_float_t,
    binary_double_t,
    /**
     * plsql binary_integer
     */
    binary_integer_t,
    /**
     * binary large object
     * Databases: DB2, teradata
     */
    binary_large_object_t,
    bit_t,
    bit_varying_t, // = varbit
    blob_t,
    /**
     * bool, boolean, ansi2003: boolean
     */
    bool_t,
    box_t,
    /**
     * teradata: byte
     */
    byte_t,
    bytea_t, //ansi2003 blob
    /**
     * teradata byteint
     */
    byteint_t,
    /**
     * char, character,  ansi2003: character
     */
    character_t,
    char_t,
    char_for_bit_data_t,
    /**
     * teradata: character large object
     */
    char_large_object_t,
    cidr_t,
    circle_t,
    clob_t,
    cursor_t,
    datalink_t,
    date_t,
    /**
     *  ansi2003: timestamp
     */
    datetime_t,
    datetimeoffset_t,// ansi2003: timestamp
    datetime2_t, //  ansi2003: timestamp with time zone
    /**
     * ansi2003: nclob
     * Databases: DB2
     */
    dbclob_t,
    /**
     * dec,decimal, ansi2003: decimal
     */
    decimal_t,
    dec_t,
    /**
     * double, double precision, ansi2003: float
     */
    double_t,
    enum_t,
    float_t,// ansi2003: double precision
    float4_t,// ansi2003: float(p)
    float8_t, // ansi2003 float(p)
    /**
     * ansi2003 blob
     */
    graphic_t,
    geography_t,
    geometry_t,
    hierarchyid_t,
    image_t,
    inet_t,
    /**
     * int, integer, ansi2003: integer
     */
    integer_t,
    int_t,
    int2_t, // ansi2003: smallint
    int4_t, // ansi2003: int, integer
    /**
     * Postgresql
     */
    interval_t,
    /**
     * teradata: interval day
     */
    interval_day_t,
    /**
     * teradata: interval day to hour
     */
    interval_day_to_hour_t,
    /**
     * teradata: interval day to minute
     */
    interval_day_to_minute_t,
    interval_day_to_second_t,
    /**
     * teradata: interval hour
     */
    interval_hour_t,
    /**
     * teradata: interval hour to minute
     */
    interval_hour_to_minute_t,
    /**
     * teradata: interval hour to second
     */
    interval_hour_to_second_t,
    /**
     * teradata: interval minute
     */
    interval_minute_t,
    /**
     * teradata: interval minute to second
     */
    interval_minute_to_second_t,
    /**
     * teradata: interval month
     */
    interval_month_t,
    /**
     * teradata:interval second
     */
    interval_second_t,
    /**
     * teradata interval year.
     */
    interval_year_t,
    interval_year_to_month_t,
    line_t,
    long_t,
    long_varchar_t,
    /**
     * long varbinary, mysql
     * MySQL Connector/ODBC defines BLOB values as LONGVARBINARY and TEXT values as LONGVARCHAR.
     */
    long_varbinary_t,
    longblob_t, // ansi2003: blob
    /**
     *  ansi2003: blob
     */
    long_raw_t,
    long_vargraphic_t,
    longtext_t,
    lseg_t,
    macaddr_t,
    mediumblob_t,
    /**
     * mediumint, middleint(MySQL) , ansi2003:  int
     */
    mediumint_t,
    mediumtext_t,
    money_t, // = decimal(9,2),INFORMIX
    /**
     * national_char_varying,nchar_varying,nvarchar, ansi2003: national character varying
     */
    nvarchar_t,
    /**
     * nchar, national char, national character,ansi2003: national character
     */
    nchar_t,
    ncharacter_t,
    /**
     * ansi2003: nclob
     */
    nclob_t,
    /**
     * ntext, national text, ansi2003: nclob
     */
    ntext_t,
    /**
     * nvarchar2(n)
     */
    nvarchar2_t,
    /**
     * number, num
     */
    number_t,
    /**
     *  ansi2003: numeric
     */
    numeric_t,
    oid_t,
    path_t,
    /**
     * teradata: period(n)
     */
    period_t,
    /**
     * plsql pls_integer
     */
    pls_integer_t,
    point_t,
    polygon_t,
    raw_t,
    /**
     * ansi2003: real
     */
    real_t,
    rowid_t,
    rowversion_t,
    serial_t,// = serial4
    serial8_t,// = bigserial
    bigserial_t,//informix
    smallfloat_t,//informix
    /**
     * MySQL: set
     */
    set_t,
    smalldatetime_t,
    /**
     * ansi2003: smallint
     */
    smallint_t,
    smallmoney_t,
    sql_variant_t,
    table_t,
    text_t,
    /**
     * ansi2003: time
     */
    time_t,
    /**
     * teradata: time with time zone
     */
    time_with_time_zone_t,
    time_without_time_zone_t,
    timespan_t, // ansi2003: interval
    timestamp_t, // ansi2003: timestamp
    /**
     * timestamp with local time zone,
     * Database: Oracle,SQL Server
     */
    timestamp_with_local_time_zone_t,
    /**
     * timestamp with time zone, timestamptz, ansi2003: timestamp with time zone
     */
    timestamp_with_time_zone_t,
    timestamp_without_time_zone_t,
    /**
     * time with time zone,  ansi2003: time with time zone
     * Databases: teradata
     */
    timetz_t,
    timentz_t,
    tinyblob_t,
    tinyint_t,
    tinytext_t,
    uniqueidentifier_t,
    urowid_t,
    /**
     *  ansi2003: blob
     */
    varbinary_t,
    /**
     * netezza, bit varying
     */
    varbit_t,
    /**
     * teradata: varbyte
     */
    varbyte_t,
    /**
     * varchar, char varying, character varying, ansi2003:character varying(n)
     */
    varchar_t,
    /**
     * ansi2003: character varying
     */
    varchar2_t,
    varchar_for_bit_data_t,// ansi2003:    bit varying
    lvarchar_t, //informix,openedge
    idssecuritylabel_t,//informix
    /**
     *  ansi2003: nchar varying
     */
    vargraphic_t,
    row_data_types_t, //informix
    collection_data_types_collection_t,
    collection_data_types_set_t,
    collection_data_types_multiset_t,
    collection_data_types_list_t,
    /**
     * ansi2003: tinyint
     */
    /**
     * datatypeAttribute in cast function will be treated as a datatype without typename
     * RW_CAST ( expr AS datatypeAttribute )
     */
    no_typename_t,
    year_t,
    xml_t, // ansi2003: xml
    xmltype_t, // ansi2003: xml
    natural_t, //plsql
    naturaln_t,//plsql
    positive_t,
    positiven_t,
    signtype_t,
    simple_integer_t,
    double_precision_t,
    boolean_t,
    string_t,
    listType_t, //hive array <type>
    structType_t,//hive
    mapType_t,
    unionType_t,
    refcursor_t,//postgresql
    json_t, //postgresql
    jsonb_t,//postgresql
    self_t,//oracle, constructor function
    seconddate_t,//hana
    smalldec_t,//hana
    array_t,//hana,bigquery
    alphanum_t,//hana
    shorttext_t,//hana
    bintext_t,//hana
    currency_t,//dax
    int8_t,
    lvarbinary_t,//openedge
    long_byte_t,//mysql
    object_t,//snowflake
    variant_t,//snowflake
    unsigned_int_t,//
    decfloat_t,//db2
    struct_t,//bigquery
    int64_t,//bigquery
    float64_t,//bigquery

}
```