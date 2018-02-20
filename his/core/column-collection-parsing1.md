---
title: "Column Collection Parsing1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: bd309c5d-4827-42d5-a043-d03618a326ea
caps.latest.revision: 4
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Column Collection Parsing
The following describes the column collection parsing for the Managed Provider for Host Files and provides a sample parsed column collection.  
  
1.  Check for `* OR`  
  
2.  Check for column identifiers separated by commas.  
  
3.  After every column name, check whether the `AS` keyword is provided.  
  
     If `AS` is provided, the next token should be the CLR data type, such as  `Int32` or `String`).  
  
## Example  
 The following is a sample parsed column collection for the Managed Provider for Host Files.  
  
```  
*  
Col1, Col2, …  
Col1 AS String, Col2 as Int32, …  
Col1 AS String, Col2, Col3, …  
```  
  
## See Also  
 [SQL Parsing in the Managed Data Provider for Host Files](../core/sql-parsing-in-the-managed-data-provider-for-host-files2.md)