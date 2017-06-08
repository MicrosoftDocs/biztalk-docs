---
title: "Value Extractor Functoid | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Value Extractor functoids"
ms.assetid: 45a9a968-b100-4812-884a-f18879afc9c7
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Value Extractor Functoid
Use the **Value Extractor** functoid ( ![](../core/media/dbvalueextract.gif "dbvalueextract")) to extract the value from a specified column in a Microsoft ActiveX Data Objects (ADO) recordset, which is returned by the **Database Lookup** functoid.  
  
## Input  
 **Parameter 1:** An ADO recordset, which is the output of the **Database Lookup** functoid. This recordset never contains more than one database row.  
  
 **Parameter 2:** The name of a column from which to extract a value for output.  
  
## Output  
 **Output 1:** A value from the specified column in the single-row ADO recordset that was retrieved by using the **Database Lookup** functoid.  
  
## Remarks  
 To avoid errors that are only detected at run time, make sure that the first parameter to the **Value Extractor** functoid is the output of a **Database Lookup** functoid and not the output of any other functoid in the **Database**category or custom functoid that returns an ADO recordset.  
  
## See Also  
 [Database Functoids Reference](../core/database-functoids-reference.md)   
 [Database Functoids](../core/database-functoids.md)   
 [How to Add Basic Functoids to a Map](../core/how-to-add-basic-functoids-to-a-map.md)   
 [Database Lookup Functoid](../core/database-lookup-functoid.md)   
 [Error Return Functoid](../core/error-return-functoid.md)