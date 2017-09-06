---
title: "Error - Generic Native Serialization | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.map.error.genericNativeSerialize"
ms.assetid: 3728727d-7d99-432d-844e-c956cc4635e4
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Error - Generic Native Serialization
**Error Code**  
  
 btm1049  
  
 **Explanation**  
  
 The XML output instance message produced by the transformation specified by the map could not be converted to the native format specified by the destination schema due to an unspecified error.  
  
 **User Action**  
  
 Open the destination schema in BizTalk Editor and use the **Validate Schema**, **Validate Instance**, and **Generate Instance** commands, available when you right-click a schema in Solution Explorer, to isolate the problem.