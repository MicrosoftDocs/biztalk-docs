---
title: "Error - First Input to Value Extractor Functoid Not Valid | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.map.error.firstInputValueExtractorNotValid"
ms.assetid: 7703ca5f-21aa-441f-8c28-b02da72c25c1
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Error - First Input to Value Extractor Functoid Not Valid
**Error Code**  
  
 btm1002  
  
 **Explanation**  
  
 The first input parameter to the indicated **Value Extractor** functoid must be the output (an ADO recordset) from the **Database Lookup** functoid.  
  
 **User Action**  
  
 Ensure that the first input to all **Value Extractor** functoids is a link from a **Database Lookup** functoid to their left in a map grid page.