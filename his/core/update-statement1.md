---
title: "UPDATE Statement1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b9fcdf21-60e9-4be2-84a0-de21804e5e08
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs"
manager: "anneta"
---
# UPDATE Statement
The following describes the `UPDATE` statement for the Managed Provider for Host Files and provides a sample `UPDATE` statement.  
  
## Syntax  
 UPDATE Filename SET (\<Values>)  
  
 UPDATE Filename SET (\<Values>) WHERE \<Where Clause>  
  
 UPDATE Filename AS \<AssemblyName.SchemaName> SET (\<Values>)  
  
 UPDATE Filename AS \<AssemblyName.SchemaName> SET (\<Values>) WHERE \<Where Clause>  
  
 UPDATE Filename SET (\<Column Collection>) (\<Values>)  
  
 UPDATE Filename SET (\<Column Collection>) (\<Values>) WHERE \<Where Clause>  
  
## Example  
 The following is a sample `UPDATE` statement for the Managed Provider for Host Files.  
  
```  
UPDATE Filename SET (OUT1_INTEGER) (7) WHERE <Applicable where clause >  
```  
  
## See Also  
 [SQL Parsing in the Managed Data Provider for Host Files](../core/sql-parsing-in-the-managed-data-provider-for-host-files2.md)