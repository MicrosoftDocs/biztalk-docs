---
description: "Learn more about: Error - First Input to Value Extractor Functoid Not Valid"
title: "Error - First Input to Value Extractor Functoid Not Valid"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.map.error.firstInputValueExtractorNotValid"
---
# Error - First Input to Value Extractor Functoid Not Valid
**Error Code**  
  
 btm1002  
  
 **Explanation**  
  
 The first input parameter to the indicated **Value Extractor** functoid must be the output (an ADO recordset) from the **Database Lookup** functoid.  
  
 **User Action**  
  
 Ensure that the first input to all **Value Extractor** functoids is a link from a **Database Lookup** functoid to their left in a map grid page.
