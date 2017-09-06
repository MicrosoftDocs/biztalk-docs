---
title: "Warning - Envelope Schema Needs Root Record Node | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.edit.error.envelopeSchemaNeedsRoot"
ms.assetid: 3fbc1571-1270-4c5e-adcf-00633bf46efe
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Warning - Envelope Schema Needs Root Record Node
**Error Code**  
  
 BEC1010  
  
 **Explanation**  
  
 Envelope schemas are required to have at least one root **Record** node as a child of its **Schema** node.  
  
 **User Action**  
  
 Right-click the **Schema** node, click **Insert Child Record** on the shortcut menu, and then type a descriptive name for the inserted **Record** node. In general, envelope schemas will also have additional nodes inserted within the root **Record** node.