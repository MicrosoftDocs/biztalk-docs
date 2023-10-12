---
description: "Learn more about: SELECT Statement"
title: "SELECT Statement1"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# SELECT Statement
The following describes the `SELECT` statement parsing used in the Managed Provider for Host Files and provides sample `SELECT` statements.  
  
## Syntax  
 SELECT \<Column Collection> FROM Filename WHERE \<Where Clause>  
  
 SELECT \<Column Collection> FROM Filename AS \<AssemblyName.SchemaName> WHERE \<Where Clause>  
  
## Examples  
  
```  
SELECT * FROM FILE_NAME   
SELECT COL_NAME1, COL_NAME2… FROM FILE_NAME   
```  
  
## See Also  
 [SQL Parsing in the Managed Data Provider for Host Files](../core/sql-parsing-in-the-managed-data-provider-for-host-files2.md)
