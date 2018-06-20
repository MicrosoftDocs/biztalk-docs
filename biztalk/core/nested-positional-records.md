---
title: "Nested Positional Records | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3e205e9d-f740-4177-b45a-5e1baadae99a
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Nested Positional Records
Nested positional records are allowed if the **Max Occurs** property of child records is set to a positive integer. Field autocalculation should be able to handle the new depth. However, there is a modification to the way this behaves. Specifically, because of the possibility for null delimiters, autocalculation of field positions will function only if one of the following conditions is met:  
  
- The selected node has a parent that is infix delimited.  
  
- The selected node has a specified starting position.  
  
  Note that there is a distinction between nested positional records and positional records whose parent is a delimited container where the delimiter is null. For structures to be truly nested positionally, there must not be any ambiguity in determining their length. For example, a delimited loop node can contain a repeating positional record that occurs 0 to N times. However, for that loop node itself to be positional, and possibly also contain fields as peers to the repeating positional record, the occurrence of the repeating positional record must be deterministic (a positive integer).  
  
## See Also  
 [Positional Record Considerations](../core/positional-record-considerations.md)