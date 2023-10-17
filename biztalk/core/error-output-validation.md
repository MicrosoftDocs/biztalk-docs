---
description: "Learn more about: Error - Output Validation"
title: "Error - Output Validation | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.map.error.outputValidation"
ms.assetid: 18a251a9-6bd4-4fd1-a774-2ea1b7870891
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Error - Output Validation
**Error Code**  
  
 btm1046  
  
 **Explanation**  
  
 The output instance message file created by the Test Map operation could not be validated against the destination schema for the indicated reason.  
  
 **User Action**  
  
 Based on the indicated reason, make the appropriate corrections to either the transformations specified in the map, or to the destination schema, or to both. It may be helpful to open the destination schema in BizTalk Editor and use the **Validate Schema**, **Validate Instance**, and **Generate Instance** commands available when you right-click a schema in Solution Explorer.
