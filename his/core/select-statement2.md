---
title: "SELECT Statement2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 13c4cb0c-f62b-4b60-9887-32fea1c92bcc
caps.latest.revision: 3
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
 [SQL Parsing in the Managed Data Provider for Host Files](../core/sql-parsing-in-the-managed-data-provider-for-host-files1.md)