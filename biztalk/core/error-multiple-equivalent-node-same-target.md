---
description: "Learn more about: Error - Multiple Equivalent Node Same Target"
title: "Error - Multiple Equivalent Node Same Target | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.map.error.multipleEquivNodeSameTarget"
ms.assetid: d8ca9f94-1d87-41bb-9479-6a01a5b6702d
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Error - Multiple Equivalent Node Same Target
**Error Code**  
  
 btm1025  
  
 **Explanation**  
  
 The indicated nodes in the source schema, which are conflicting child nodes of an **Equivalent** group node, are both linked to the indicated node in the destination schema. Only one of these nodes in the source schema can occur in a given instance message.  
  
 **User Action**  
  
 Ensure that only one of the child nodes of the **Equivalent** group node is connected to a given node in the destination schema.
