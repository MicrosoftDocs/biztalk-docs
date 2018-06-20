---
title: "Configuring Database Alias Mappings | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: df990679-c137-4e52-8dc9-c58d7de57917
caps.latest.revision: 4
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Configuring Database Alias Mappings
IBM DB2 and Microsoft SQL Server databases utilize different terminology for naming objects, as can be seen in the following table defining the fully-qualified three-part object identifier for a table. The DRDA Service can map DB2 catalog and schema names to SQL Server catalog and schema names.  
  
|Platform|Catalog|Schema|Table|  
|--------------|-------------|------------|-----------|  
|DB2 for z/OS|LOCATION|COLLECTION (aka OWNER)|TABLENAME|  
|DB2 for i5/OS|RELATIONAL DATABASE NAME (RDBNAM)|COLLECTION (aka LIBRARY)|TABLENAME|  
|DB2 for LUW|DATABASE|SCHEMA|TABLENAME|  
|SQL Server|DATABASE|SCHEMA|TABLENAME|  
|DRDA|RELATIONAL DATABASE NAME (RDBNAM)|COLLECTION|TABLENAME|  
  
 <em>**Table.</em>* Three-part table naming conventions.*  
  
 The **databaseAliases** element instructs the DRDA Service to map in-bound catalog and schema names to outbound catalog and schema names, for use when executing static SQL packages for DB2 commands mapped to SQL Server stored procedures. The **databaseAlias** element contains a **sourceLocation**, **sourceCollection**, **targetDatabase**, and **targetSchema** to define one or more optional object name mappings.  
  
> [!NOTE]
>  The databaseAliases element is not used when binding packages or executing dynamic SQL statements.  
  
#### Source Location  
 The **sourceLocation** attribute defines an in-bound DRDA RDBNAM (Relational Database Name) that the DRDA Service should use when mapping to an out-bound SQL Server database name. This **optional** property accepts a **string** value. The default value is an **empty string**, which denotes any value.  
  
> [!NOTE]
>  When connecting DB2 for z/OS to the DRDA Service, the sourceLocation value may be the database alias (DBALIAS) value from the DB2 for z/OS Connection Database (CDB) table SYSIBM.LOCATIONS.  
  
#### Source Collection  
 The **sourceCollection** attribute defines an in-bound DRDA COLID (Collection Identifier) that the DRDA Service should use when mapping to an out-bound SQL Server schema name. This **optional** attribute accepts a **string** value. The default value is an **empty string**, which denotes any value.  
  
#### Target Database  
 The **targetDatabase** attribute defines an out-bound SQL Server database name that the DRDA Service should use when mapping from an in-bound DRDA RDBNAM value. This **optional** attribute accepts a **string** value. The default value is an **empty string**, which denotes any value.  
  
#### Target Schema  
 The **targetSchema** attribute defines an out-bound SQL Server schema name that the DRDA Service should use when mapping from an in-bound DRDA COLID value. This **optional** attribute accepts a **string** value. The default value is an **empty string**, which denotes any value.  
  
 **Example:** The DRDA Service can map a DB2 location name (e.g. CONTOSO) to a SQL Server database name (e.g. ContosoRetailDW), and a DB2 collection name (e.g. PROD1) to a SQL Server database schema name (e.g.dbo).  
  
```  
<databaseAliases>  
  <databaseAlias sourceLocation="CONTOSO"  
                 sourceCollection="DSN8HC91"  
                 targetDatabase="ContosoRetailDW"  
                 targetSchema="DSN8910" />  
  <databaseAlias sourceLocation="NWIND"  
                 sourceCollection="DSN8HC91"  
                 targetDatabase="Northwind"  
                 targetSchema="DSN8910" />  
</databaseAliases>  
```  
  
 <em>**Example.</em>* DRDA Service can map DB2 catalog and schema names to SQL Server names.*  
  
```  
DrdaAs Information: 1 : [<timestamp>] Processing ACCRDB  
DrdaAs Information: 1 : [<timestamp>] Processing ACCRDB RDBNAME="ContosoRetailDW"  
...  
DrdaAs Information: 0 : [<timestamp>] Transformed:  
SELECT * FROM CONTOSO.DSN8HC91.FACTSALES FOR FETCH ONLY  
SELECT * FROM ContosoRetailDW.DSN8910.FACTSALES FOR FETCH ONLY  
```  
  
 *DRDA Service trace output of the DRDA ACCRDB connection and EXCSQLSTT command.*