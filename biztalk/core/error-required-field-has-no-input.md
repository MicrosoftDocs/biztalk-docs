---
title: "Error - Required Field Has No Input | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.map.error.reqdFieldHasNoInput"
ms.assetid: 2454baf8-aa28-4b7b-93cd-aab9afc63823
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Error - Required Field Has No Input
**Error Code**  
  
 btm1028  
  
 **Explanation**  
  
 The indicated node in the destination schema is specified as required, yet has no incoming link, constant value, or default value, and thus will not be included in output instance messages provided by this map.  
  
 **User Action**  
  
 As appropriate, either change the indicated node in the destination schema to optional, or provide an incoming link, constant value, or default value for it.