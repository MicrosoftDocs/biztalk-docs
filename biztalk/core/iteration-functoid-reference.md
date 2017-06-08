---
title: "Iteration Functoid Reference | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Iteration functoids, about Iteration functoids"
  - "Iteration functoids, properties"
ms.assetid: 3ccd959f-93e9-46bc-93a3-af366d845db1
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Iteration Functoid Reference
Use the **Iteration** functoid ( ![](../core/media/adviteration.gif "adviteration")) to output the number of passes through a repeating structure in an input instance message as that structure is being processed.  
  
## Input  
 **Parameter 1:** A link from a repeating structure in the source schema.  
  
## Output  
 **Output 1:** A monotonically increasing number, starting at one (1), for each iteration through the specified repeating structure.  
  
## Remarks  
 For example, if the **Iteration** functoid is connected to a **Record** node in the source schema and connected to a **Field Element** node named "book" in the destination schema, and in a particular instance message the corresponding input element occurs three times, the following output is produced:  
  
```  
<book>1</book>  
<book>2</book>  
<book>3</book>  
  
```  
  
## See Also  
 [Advanced Functoids Reference](../core/advanced-functoids-reference.md)   
 [Advanced Functoids](../core/advanced-functoids.md)   
 [Iteration Functoid](../core/iteration-functoid.md)   
 [How to Add Iteration Functoids to a Map](../core/how-to-add-iteration-functoids-to-a-map.md)