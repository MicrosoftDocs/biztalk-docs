---
title: "Error - Could Generate Multiple Equivalent Children | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.map.error.couldGenMultipleEquivChildren"
ms.assetid: ef3ea6db-6759-4f38-804c-e32a1f24d758
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Error - Could Generate Multiple Equivalent Children
**Error Code**  
  
 btm1026  
  
 **Explanation**  
  
 Links to the destination schema inappropriately enable multiple nodes within an **Equivalent** group node to be generated.  
  
 **User Action**  
  
 Rework the links into the destination schema, potentially using logical functoids, so that only a single node within the **Equivalent** group node can be generated during mapping.