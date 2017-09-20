---
title: "Error - Native Serialization | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.map.error.nativeSerialize"
ms.assetid: 48f8d460-83a0-44ce-af9b-086fcad36cb8
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Error - Native Serialization
**Error Code**  
  
 btm1048  
  
 **Explanation**  
  
 The indicated serialization error was encountered when attempting to convert the XML output instance message produced by the map into the native format specified by the destination schema.  
  
 **User Action**  
  
 Based on the indicated serialization error, make the appropriate corrections to either the transformations specified in the map, or to the destination schema, or to both. It may be helpful to open the destination schema in BizTalk Editor and use the **Validate Schema**, **Validate Instance**, and **Generate Instance** commands available when you right-click a schema in Solution Explorer.