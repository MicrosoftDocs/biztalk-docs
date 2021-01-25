---
description: "Learn more about: Parameterized Queries"
title: "Parameterized Queries1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b6701870-d7b8-4369-b191-da0ddc7f7dda
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs"
manager: "anneta"
---
# Parameterized Queries
The host file provider supports parameterized queries. In this case, instead of using the values directly in the SQL statement, a placeholder can be used.  
  
## Syntax  
 WHERE KEY (KEY_COLUMN) BETWEEN (@p1) AND (@p2)  
  
## See Also  
 [SQL Parsing in the Managed Data Provider for Host Files](../core/sql-parsing-in-the-managed-data-provider-for-host-files2.md)
