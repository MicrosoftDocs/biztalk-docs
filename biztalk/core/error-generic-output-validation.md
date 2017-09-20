---
title: "Error - Generic Output Validation | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.map.error.genericOutputValidation"
ms.assetid: 27fb2233-3add-42f8-a96b-872e2e38f797
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Error - Generic Output Validation
**Error Code**  
  
 btm1047  
  
 **Explanation**  
  
 The output instance message file created by the Test Map operation could not be validated against the destination schema for an unspecified reason.  
  
 **User Action**  
  
 Open the destination schema in BizTalk Editor and use the **Validate Schema**, **Validate Instance**, and **Generate Instance** commands, available when you right-click a schema in Solution Explorer, to isolate the problem.