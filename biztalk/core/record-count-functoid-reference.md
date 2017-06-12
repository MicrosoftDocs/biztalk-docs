---
title: "Record Count Functoid Reference | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Record Count functoids"
ms.assetid: a380ed75-7726-4a74-9bc1-936369b1d886
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Record Count Functoid Reference
Use the **Record Count** functoid ( ![](../core/media/advcount.gif "advcount")) to generate a count of the number of times a particular repeating structure occurs in an input instance message.  
  
## Input  
 **Parameter 1:** A link from a node in the source schema. For this functoid to do something interesting, the structure in an input instance message that corresponds to this node must be repeating. Otherwise, the output is always one (1).  
  
## Output  
 **Output 1:** A number that corresponds to the number of occurrences of the repeating structure in an input instance message that corresponds to the node specified by parameter 1.  
  
## Remarks  
 You can also use the **Record Count** functoid to count repeating field elements. It is not restricted to records.  
  
## See Also  
 [Advanced Functoids Reference](../core/advanced-functoids-reference.md)   
 [Advanced Functoids](../core/advanced-functoids.md)   
 [Record Count Functoid](../core/record-count-functoid.md)   
 [How to Add Record Count Functoids to a Map](../core/how-to-add-record-count-functoids-to-a-map.md)