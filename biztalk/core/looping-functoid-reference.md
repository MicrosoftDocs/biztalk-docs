---
title: "Looping Functoid Reference | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Looping functoids, properties"
  - "Looping functoids, about Looping functoids"
ms.assetid: 776041c2-1f1d-415d-ac86-89d40dedc103
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Looping Functoid Reference
Use the **Looping** functoid ( ![](../core/media/advlooping.gif "advlooping")) to combine multiple repeating structures in an input instance message into a single repeating structure in the output instance message.  
  
## Input  
 **Parameters 1 – 100:** A link from at least one repeating node in the source schema, and optionally, links from other repeating nodes in the source schema.  
  
## Output  
 **Output 1:** A link to a single repeating node in the destination schema.  
  
## Remarks  
 The input and output links for the **Looping** functoid define the repeating structures in an input instance message that are combined into a single repeating structure in an output instance message. However, additional links are required from nodes within the repeating nodes in the source schema to the appropriate nodes within the repeating node in the destination schema. Without these additional links, the repeating structures are combined, but without any of the data that they contain.  
  
 For example, if there are two input links and their corresponding structures repeat 5 and 10 times, respectively, in a particular input instance message, the corresponding structure in the output instance message repeats 15 times.  
  
 The **Looping** functoid can be useful in a number of ways, but it is somewhat more complicated to set up correctly than many other functoids.For more information about the **Looping** functoid, see the [Looping Functoid](../core/looping-functoid.md).  
  
 Under certain conditions, some functoids might not behave as expected when they are used in a map with a **Looping** functoid. If a functoid meets the following conditions, it does not produce the expected results when used with the **Looping** functoid:  
  
-   The functoid has more than one input link.  
  
-   Two or more of the functoid input links are linked to child fields of the input records to the **Looping** functoid, where the child fields are not siblings.  
  
-   The functoid has an output link that is linked to a child field of the output record of the **Looping** functoid.  
  
-   There is a logical filter in effect that makes the loop occur only when the logical condition evaluates to **True**.  
  
> [!NOTE]
>  The Looping functoid should not be used with the Value Mapping (Flattening) functoid. If both are used together, it results in a compiled map that assumed there is no source looping dependency for the target nodes that are below the **Looping** functoid.  
  
## See Also  
 [Advanced Functoids Reference](../core/advanced-functoids-reference.md)   
 [Advanced Functoids](../core/advanced-functoids.md)   
 [Looping Functoid](../core/looping-functoid.md)   
 [How to Add Looping Functoids to a Map](../core/how-to-add-looping-functoids-to-a-map.md)