---
title: "Catch Exception Block | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.orch.exception.catch.block"
ms.assetid: c3545960-9ea0-409e-8a36-c5c6c49dd435
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Catch Exception Block
The **Catch Exception** block represents an exception handler, and is attached to the end of a **Scope** shape. You can attach as many **Catch Exception** blocks as you need. If an exception is thrown that matches the type specified, the exception handler will be called. If some other exception is thrown, it will be handled by the default exception handler.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Exception Object Name** property|Type a name for the exception.|  
|**Exception Object Type** property|From the drop-down list, select an exception type consisting of either a fault message or an object derived from the class **System.Exception**.|  
|**Report to Analyst** property|Select **True** if you want to make this shape viewable in the Visual Business Analyst Tool.|  
  
## See Also  
 [How to Add a Catch Exception Block](../core/how-to-add-a-catch-exception-block3.md)