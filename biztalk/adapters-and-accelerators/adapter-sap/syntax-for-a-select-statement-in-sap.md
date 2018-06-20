---
title: "Syntax for a SELECT Statement in SAP | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "SELECT statement, syntax for"
ms.assetid: 47120d74-bf41-4622-a6bc-7b8ddc959305
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Syntax for a SELECT Statement in SAP
The following sections describe grammar specifications for implementing SELECT queries against the [!INCLUDE[adoprovidersaplong](../../includes/adoprovidersaplong-md.md)]. Notice that in several cases, the syntax is somewhat different from the base Transact-SQL syntax.  
  
```  
SELECT {TOP <const> }[0,1] <select_list>  {INTO FILE [‘file_name’ | “file_name”]   
{DELIMITED}[0,1]}[0,1]  FROM table_name  {AS alias_name }[0,1]    
{INNER JOIN table_name {AS alias_name}[0,1] ON  <Join_Condition>}[0,1]  
{ WHERE <predicate> } [0,1] {;}[0,1]   
[OPTION 'no_conversion' | 'batchsize <size>' | 'disabledatavalidation'  
```  
  
 Where:  
  
- **<select_list>** = `[ {table_name.}[0,1]column_name { AS alias_name } [0,1] } [ 1, …n ]`  
  
- **<Join_Condition>** = `[Alias_name.|table_name.]column_name <expr> [Alias_name.|table_name.]column_name`  
  
- **\<predicate\>** = `[ predicate [AND|OR] predicate [between|not between] predicate |  NOT predicate |  ‘(‘ predicate ‘)’ | condition ]`  
  
  The supported conditions and expressions are:  
  
- **\<condition\>** = `[ expr | expr [NOT | ] BETWEEN const AND const | expr [NOT | ] LIKE const ]`  
  
- **\<expr\>** = `[ const | column_name [= | ! = | > | > = | ! > | < | < = | ! < ] const | column_name | - const  | const | column_name ]`  
  
  Where **\<const\>** = `integer | real | string | ? | NULL | xml_element`.  
  
  **Values for the OPTION Keyword**  
  
  You can specify the options as `OPTION '<option>'`, where `<option> = 'no_conversion' | 'batchsize <size>' | 'disabledatavalidation'`  
  
- The **no_conversion** option:  
  
  -   If the **no_conversion** option is used then the fields in the table are exposed using the equivalent .NET types. For information about the .NET equivalent of the SAP data types, see [Basic SAP Data Types](../../adapters-and-accelerators/adapter-sap/basic-sap-data-types.md).  
  
  -   If the **no_conversion** option is not used, and if a field does not have a conversion exit defined then those fields in the table are exposed using the equivalent .NET types. For information about the .NET equivalent of the SAP data types, see [Basic SAP Data Types](../../adapters-and-accelerators/adapter-sap/basic-sap-data-types.md).  
  
  -   When the **no_conversion** option is not used, and if a field has a conversion exit defined then those fields in the table are exposed as .NET String.  
  
- When set to **batchsize \<size\>**, the execution of the SELECT statement causes multiple calls to be made to the SAP system, and in each call, only \<size\> number of records are retrieved. For example, if you specify 'batchsize 100', the SELECT query retrieves 100 records only in each call to the SAP system. If **batchsize \<size\>** is not specified, the default value of 10,000 is assumed for the batch size. Note that you should specify an optimum value for the batch size based on the physical memory of the computer and the number of rows in the SAP system. Failure in specifying an optimum value for batch size may result in out of memory exceptions.  
  
- When set to **disabledatavalidation**, the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] does not validate the values present in the DATS, TIMS, and NUMC columns but instead exposes them as string.  
  
   This is useful in scenarios where ADO.NET clients fail to retrieve data from an SAP table having invalid data in DATS, TIMS, and NUMC columns. Because SAP allows invalid data to be present in DATS, TIMS, and NUMC columns, ADO.NET clients attempting to read the data will not be able to parse the invalid data and will throw an exception. If the **disabledatavalidation** option is set on the SELECT query, the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] does not parse the invalid data but extracts them as strings.  
  
> [!IMPORTANT]
>  You must always provide the values for the OPTION keyword within single quotes, for example, '*disabledatavalidation*'.  
  
 For example statements, see [Examples for SELECT Statement](../../adapters-and-accelerators/adapter-sap/examples-for-select-statement.md).  
  
## Predicates Syntax  
 The following specifies the grammar for using predicates in a SELECT statement:  
  
 `Predicate`:  
  
```  
Predicates [AND | OR] Predicates [between|not between] Predicates | [NOT] Predicates | '(' Predicates ')' | Condition  
```  
  
 `Condition`:  
  
```  
Expr | LExpr [NOT] BETWEEN RExpr AND RExpr | LExpr [NOT] LIKE Const  
```  
  
 `Expr`:  
  
```  
LExpr [=|!=|>|>=|!>|<|<=|!<] RExpr>  
```  
  
 `LExpr`:  
  
```  
ColumnName  
```  
  
 `RExpr`:  
  
```  
Const | PlaceHolder  
```  
  
 `ColumnName`:  
  
```  
Column | TableName.Column | '['Column']'  
```  
  
 `Tablename`:  
  
```  
Table | '['Table']'  
```  
  
## Considerations When Calling a SELECT Statement  
 This section lists the points that you must keep in mind when using the SELECT statement with [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)].  
  
- When specifying date-time values in parameters or queries, provide the values as a string. Provide date-time strings in the SAP date-time format.  
  
  - `SAP date format`: YYYYMMDD  
  
     For example, the date 2004 November 10 in a SAP query is expressed '20041110'.  
  
     The date 2004 November 10 in a SAPParameter p1 is the string p1.Value='20041110'.  
  
  - `SAP time format`: HHMMSS  
  
     For example, the time 10:34:32 in a SAP query is expressed '103432'.  
  
     The time 10:34:32 in a SAPParameter p2 is the string p2.Value='103432'.  
  
    For a SELECT statement, the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] returns `DATE` field values as .NET `System.DateTime` objects, and returns `TIME` field values as `System.TimeSpan` objects. If the value of the SAP `DATE` object is less than the minimum allowable SQL Server value (`1/1/1753`), the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] returns this minimum value, `1/1/1753`.  
  
- In the TOP clause of a SELECT query, when using the special characters "#", "^", "&", and "%" before or after an integer, the special characters are ignored, although no error message is raised. For example, the following are ignored in the TOP clause of a SELECT query:  
  
   \#5, 5^, %5%, or &5  
  
   However, using these characters between integers, as in 5$5, does throw an error.  
  
- Column names returned in a schema for a table are returned as all uppercase characters. For example, a query result set on the field `Last Name` returns the column heading `LAST NAME`. To avoid uniqueness conflicts, using all uppercase in SELECT statements is recommended.  
  
- In the LIKE clause of a SELECT query, only the percent sign, "%" (for any string of zero or more characters), and underscore, **"_"** (for any single character), are allowable special characters. All other special characters are considered string values and are ignored.  
  
- The [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] uses the Z_EXTRACT_DATA_OO RFC to perform SELECT queries on the SAP system. The RFC supports reading data from tables that satisfy the following conditions:  
  
  - TabClass for the table is TRANSP, CUSTER, or POOL.  
  
  - TabClass is VIEW and ViewClass is either D or P.  
  
    Make sure the SELECT statement reads data from tables that satisfy these conditions.  
  
- Values of data types that can take more than 255 characters, for example STRING, RAWSTRING, LRAW, VARC, and LCHAR cannot be used in a SELECT query. The [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] uses a custom RFC shipped with the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)], Z_EXTRACT_DATA_OO, to perform SELECT queries on the SAP system. This custom RFC does not support any data type that can take more than 255 characters.  
  
- The maximum number of columns or fields that are supported in a SELECT statement is 1000.  
  
- The maximum number of predicates supported in a WHERE clause is 100.  
  
- Selecting the same field multiple times in the same SELECT statement is not supported. The custom RFC (Z_EXTRACT_DATA_OO) used by the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] removes the duplicate fields from the statement before executing. For example, this statement:  
  
   `SELECT BUKRS, BUKRS, BUKRS from T001`  
  
   executes as though written like this statement:  
  
   `SELECT BUKRS from T001`  
  
- [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] does not support duplicate alias names in a SELECT statement. Therefore, the following SELECT statement throws an error:  
  
  ```  
  SELECT KUNNR AS [MYKNA1], JMJAH AS MYKNA1 from KNA1 where KUNNR LIKE 'T-S62A08' AND JMJAH=1995  
  ```  
  
- [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] does not support a SELECT statement with duplicate column names. Therefore, the following SELECT statement throws an error:  
  
  ```  
  SELECT KUNNR AS [MYKNA1], KUNNR AS MYKNA2 from KNA1 where MYKNA2='T-S62A08'  
  ```  
  
- SAP does not store NULL values in the tables. As a result, the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] does not support an "IS NULL" value in a SELECT statement. Therefore, the following SELECT statement throws an error:  
  
  ```  
  SELECT NAME1, PSTLZ  from KNA1 where CITY IS NULL AND NAME1 LIKE '%MODE%'  
  ```  
  
- [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] does not support an ORDER BY clause in a SELECT statement. Therefore, the following SELECT statement throws an error:  
  
  ```  
  SELECT NAME1  AS [MYNAME],  LAND1, KUNNR  from KNA1 where NAME1 LIKE '%MODE%'  ORDER BY NAME1  ASC  
  ```  
  
- [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] does not support specifying an asterisk (*) to select all the fields in an SAP table. Therefore, the following SELECT statement throws an error:  
  
  ```  
  SELECT spfli.* from spfli inner join sflight on spfli.carrid = sflight.carrid  
  ```  
  
   To select all the fields, you must specify the field names individually.  
  
- As part of the SELECT statement, you can specify a file to which the output of the SELECT statement will be written. However, if the output file is on a network share, make sure the SAP service account under which the SAP service is running has write permission to the network share. For example:  
  
  ```  
  SELECT * into file '\\share\output.txt' from spfli inner join sflight on spfli.carrid = sflight.carrid  
  ```  
  
   In the preceding example, the SAP service account must have write permission to the network share with the name "share."  
  
- A SELECT statement using [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] supports parameter names for argument values in a SELECT query. However, make sure you follow these rules with respect to parameter names:  
  
  -   In the SELECT query, an "\@" symbol must precede the parameter name.  
  
  -   The "\@" symbol must be followed by an alphabetic character (A-Z or a-z).  
  
  -   The parameter name can contain alphanumeric characters (A-Z, a-z, or 0-9) and special characters. The only special characters that can be included in the parameter name are underscore "_" and hash "#".  
  
- When you run a SELECT query on a View, make sure that all the primary key columns of the base table are also present in the View. Also, as a practice, you must mark the columns as primary key columns in the View also.  
  
   If the primary key columns are not present in the View, a SELECT query on the View will result in an exception.  
  
- When you run a SELECT query on a table to select fields of type LRAW, make sure you select the corresponding PREC field. Also, the PREC field must appear immediately before the LRAW field in the SELECT clause.  
  
   Every LRAW field in a table has a corresponding PREC field that stores the length of data in the LRAW field. Specifying just the LRAW field in the SELECT clause without the PREC field may result in incorrect data being extracted.  
  
- In an SAP system, character comparisons are case sensitive. So, the following two queries may return different results.  
  
  ```  
  SELECT * FROM KNA1 WHERE LAND1 LIKE 'D%'  
  ```  
  
   And  
  
  ```  
  SELECT * FROM KNA1 WHERE LAND1 LIKE 'd%'  
  ```  
  
   Make sure you use the right cases when framing a select query. Also, in an SAP system, not all columns can contain lowercase or uppercase characters. You can use the SAP GUI to find out whether a column in a table stores lowercase or uppercase characters. For instructions on using the SAP GUI, see [Determining Whether a Column Stores Lowercase or Uppercase Values](../../adapters-and-accelerators/adapter-sap/determining-whether-a-column-stores-lowercase-or-uppercase-values.md).  
  
- The WHERE condition is supported only for comparison of a field value with some data value, and *not* with some other table field value. Because the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] supports only one table SELECT query, table field queries in join conditions should use the join condition to support the same.  
  
- A join condition must contain a table name.  
  
   The following is a correct SELECT statement  
  
  ```  
  select A.x, B.y from A inner join B on A.m = B.n  
  ```  
  
   The following is an incorrect SELECT statement  
  
  ```  
  select A.x, B.y from A inner join B on m = n  
  ```  
  
- In a join condition, the left table in a join condition should be on the left side of the condition, and the right table of the join condition should be specified on the right side of the join condition.  
  
   The following is the correct way of specifying a join condition:  
  
  ```  
  select A.x, B.y from A inner join B on A.m = B.n  
  ```  
  
   The following is an incorrect way of specifying a join condition:  
  
  ```  
  select A.x, B.y from A inner join B on B.n = A.m  
  ```  
  
- A SELECT statement can only contain an “equal to” condition in a JOIN clause. For example:  
  
  ```  
  select * from spfli inner join sflight on spfli.carrid = sflight.carrid  
  ```  
  
- A SELECT statement does not retrieve columns of type STRING from the SAP system.  
  
- A SELECT statement must contain only a single JOIN. For example:  
  
  ```  
  select * from spfli inner join sflight on spfli.carrid = sflight.carrid  
  ```  
  
## See Also  
 [About the .NET Framework Data Provider for mySAP Business Suite](../../adapters-and-accelerators/adapter-sap/about-the-net-framework-data-provider-for-mysap-business-suite.md)
