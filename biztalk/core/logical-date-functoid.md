---
title: "Logical Date Functoid | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Logical Date functoids, properties"
  - "Logical Date functoids, about Logical Date functoids"
ms.assetid: 9cff7543-f240-4ff4-aba1-64f963b4eb42
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Logical Date Functoid
Use the **Logical Date** functoid ( ![](../core/media/logicalisdate.gif "logicalisdate")) to determine whether the input parameter is a date.  
  
## Input  
 **Parameter 1:** A string that may or may not be interpretable as an ISO-8601 formatted date.  
  
## Output  
 **Output 1:** The Boolean value **True** if the input parameter is determined to be a date; the Boolean value **False** otherwise.  
  
## Remarks  
 BizTalk Mapper, and XML in general, require date and time values to be specified in ISO-8601 format. However, this functoid will return the Boolean value **True** for any date format that is acceptable to the .NET **Convert.ToDateTime** method using invariant culture.  
  
## See Also  
 [Logical Functoids Reference](../core/logical-functoids-reference.md)   
 [Logical Functoids](../core/logical-functoids.md)   
 [How to Add Basic Functoids to a Map](../core/how-to-add-basic-functoids-to-a-map.md)