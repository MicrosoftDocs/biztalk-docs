---
title: "Error - Generic Native Parsing | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.map.error.genericNativeParsing"
ms.assetid: a28a4c0f-b69b-448b-b305-3b06b4f061e4
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Error - Generic Native Parsing
**Error Code**  
  
 btm1042  
  
 **Explanation**  
  
 The native input instance message file specified for the Test Map operation could not be parsed, and generated a generic fatal parsing error.  
  
 **User Action**  
  
 As appropriate, correct either the source schema associated with the map or the native input instance message in the specified file, or both. Consider working within BizTalk Editor to isolate the problem. The **Validate Schema** and **Generate Instance** commands, available when you right-click a schema in Solution Explorer, are useful for finding schema errors.