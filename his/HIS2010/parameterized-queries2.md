---
title: "Parameterized Queries2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9e3116de-688f-4868-bb9f-4d7ab54c8aae
caps.latest.revision: 3
---
# Parameterized Queries
The host file provider supports parameterized queries. In this case, instead of using the values directly in the SQL statement, a placeholder can be used.  
  
## Syntax  
 WHERE KEY (KEY_COLUMN) BETWEEN (@p1) AND (@p2)  
  
## See Also  
 [SQL Parsing in the Managed Data Provider for Host Files](../HIS2010/sql-parsing-in-the-managed-data-provider-for-host-files1.md)