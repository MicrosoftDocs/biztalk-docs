---
title: "Error - Generic Generate XML Instance | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.map.error.genericGenerateXmlInstance"
ms.assetid: f2b42589-fd44-45d6-86e6-c2502820beee
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Error - Generic Generate XML Instance
**Error Code**  
  
 btm1038  
  
 **Explanation**  
  
 BizTalk Mapper was not able to generate an XML instance message file for the source schema of the map. This suggests that there is a problem with the source schema associated with the map.  
  
 **User Action**  
  
 Use BizTalk Editor to open the source schema associated with the map and begin investigating whether there are problems with the source schema. Also, the **Validate Schema** and **Generate Instance** commands, available when you right-click a schema in Solution Explorer, are useful for finding schema errors.