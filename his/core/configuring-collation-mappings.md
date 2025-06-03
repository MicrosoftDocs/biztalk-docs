---
description: "Learn more about: Configure Collation Mappings"
title: "Configure Collation Mappings"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: how-to
---
# Configure Collation Mappings
SQL Server may collate query results in a different order than what is expected by the DRDA client program. For example, an IT professional may configure a SQL Server database to use an ANSI collation and a DB2 for z/OS database to use EBCDIC collation.  
  
## Automatic Collation  
 The DRDA Service can add a `COLLATE` clause to an `ORDER BY` clause, based on a default `ORDER BY` collation name.  
  
```  
  
SELECT * FROM CONTOSO.DSN8910.DEPT ORDER BY DEPTNAME  
  
SELECT * FROM [CONTOSO].[DSN8910].[DEPT] ORDER BY DEPTNAME COLLATE SQL_EBCDIC037_CP1_CS_AS  
  
DB2 SELECT ORDER BY syntax automatically transformed to SQL Server ORDER BY COLLATE.  
  
```  
  
 The **defaultCollationName** element instructs the DRDA Service to add a SQL Server `COLLATE` (collation_name) clause, when transforming a DB2 `SELECT` statement with `ORDER BY` clause into a SQL Server `SELECT` statement with `ORDER BY` clause. This **optional** attribute accepts a **string** value. The default value is **SQL_Latin1_General_CP1_CI_AS**.  
  
## Mapping Collation Names  
 The DRDA Service can transform a SELECT statement from DB2 ORDER BY COLLATION_KEY (collation-name) syntax to SQL Server T-SQL ORDER BY COLLATE (collation_name) syntax, mapping from a DB2 collation-name value to a SQL Server collation_name value, to provide more compatible query results. See collation syntax conversion below.  
  
```  
  
SELECT * FROM CONTOSO.DSN8910.DEPT ORDER BY COLLATION_KEY (DEPTNAME, 'UCA400R1_LEN_AN')  
SELECT * FROM [CONTOSO].[DSN8910].[DEPT] ORDER BY DEPTNAME COLLATE SQL_EBCDIC037_CP1_CS_AS  
```  
  
 `DB2 SELECT ORDER BY` syntax compared to SQL Server.  
  
 The **collationNames** element within the service element can contain one or more collationName elements to instruct the DRDA Service to convert from a DB2 collation-name value to a SQL Server collation_name value, when transforming a DB2 `SELECT` statement with `ORDER BY COLLATION_KEY (collation-name)` clause into a SQL Server `SELECT` statement with `ORDER BY COLLATE (collation_name)` clause.  
  
```  
<collationNames>  
          <collationName from="UCA400R1_LEN_AN" to="SQL_EBCDIC037_CP1_CS_AS"/>  
        </collationNames>  
  
```  
  
 Collation Names element and attributes.  
  
## Collation Name  
 The **collationName** element must contain a **from** attribute and a **to** attribute to define a collation name mapping.  
  
## Mapping from Collation Name  
 The **from** attribute instructs the DRDA Service SQL Transformer to convert from the specified collation-name string within a DB2 SELECT ORDER BY COLLATION_KEY clause. This **required** attribute accepts a **string** value. There is no default value.  
  
## Mapping to Collation Name  
 The **to** attribute instructs the DRDA Service SQL Transformer to convert to the specified collation_name string within a SQL Server SELECT ORDER BY COLLATE clause. This **required** attribute accepts a **string** value. There is no default value.  
  
 For more information, see [SQL Server COLLATE](/sql/t-sql/statements/collations).
