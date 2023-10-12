---
description: "Learn more about: Error - Table Looping Functoid Without Link to Destination Schema"
title: "Error - Table Looping Functoid Without Link to Destination Schema"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.map.error.tableLoopingNoLinkToDestSchema"
---
# Error - Table Looping Functoid Without Link to Destination Schema
**Error Code**  
  
 btm1077  
  
 **Explanation**  
  
 Unlike most functoids, the **Table Looping** functoid has multiple outputs. All but one of these outputs must be connected as the first input parameter to separate instances of the **Table Extractor** functoid. The remaining output must be connected to a **Record** node (with appropriate recurrence settings) in the destination schema. This error occurs when this latter output link from a **Table Looping** functoid is missing.  
  
 **User Action**  
  
 Drag the indicated **Table Looping** record to the appropriate **Record** node in the destination schema to create the missing link.
