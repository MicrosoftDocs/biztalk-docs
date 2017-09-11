---
title: "Error - Schema Root Reference Nonexistent | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.edit.error.rootRefNonExistent"
ms.assetid: 84eaa5fb-f0b5-4a41-b935-e6d3ed734aba
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Error - Schema Root Reference Nonexistent
**Error Code**  
  
 BEC2006  
  
 **Explanation**  
  
 The **Root Reference** property of the **Schema** node is referencing a nonexistent root node. The referenced root node may have been deleted or renamed after it was set as the **Root Reference** property value.  
  
 **User Action**  
  
 Set the **Root Reference** property of the **Schema** node again. The drop-down list for that property includes all currently valid choices for root nodes.