---
title: "Limitations1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f5053e24-bd06-411c-8a5a-afbf5475b7c9
caps.latest.revision: 3
---
# Limitations
The following describes the limitations on SQL statements for the Managed Provider for Host Files.  
  
## SQL Limitations  
  
-   If the table contains a complex type (for example, Unions), then the `INSERT` and `UPDATE` commands should set the values for all the complex types.  
  
-   Data definition language (DDL) commands like `ALTER` and `CREATE` are not supported.  
  
-   Any form of data control language (DCL) is not supported.  
  
-   The expression: {COLUMN NAME} AS {EXPRESSION} is not supported.  
  
## See Also  
 [SQL Parsing in the Managed Data Provider for Host Files](../HIS2010/sql-parsing-in-the-managed-data-provider-for-host-files1.md)