---
title: "Index Functoid Reference | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Index functoids, about Index functoids"
  - "Index functoids, properties"
ms.assetid: 06cf4c6b-c5d9-4524-ab7b-3a5c47360095
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Index Functoid Reference
Use the **Index** functoid ( ![](../core/media/advindex.gif "advindex")) to retrieve and output a specific value or set of values from a (potentially nested) repeating structure in an input instance message.  
  
## Input  
 **Parameter 1:** A link from the **Record** or **Field Element** node within a (potentially nested) repeating structure from which a particular subset of the values is sought.  
  
 **Parameter 2:** A positive number indicating the index of the value sought, as indicated by parameter 1, within the most deeply nested repeating structure in which it occurs.  
  
 **Parameters 3 – 100:** Optionally, a positive number indicating the index of the value sought, as indicated by parameter 1, within the **next** most deeply nested repeating structure in which it occurs.  
  
 Parameters 1 and 2 are required. Subsequent parameters are optional, and their number is limited only by the depth of the repeating structures in which the value sought is nested.  
  
## Output  
 **Output 1:** The value or set of values from the input instance message that are associated with the specified **Record** or **Field Element** node at the specified index (or indices) within the repeating structures in which they occur.  
  
## Remarks  
 Within typical XML instance messages, structures repeat, and structures within those structures repeat, and so on. Mappings are often required to be very specific about retrieving a specific value from within potentially nested repeating structures. For example, consider a set of nested repeating structures, A, B, and C, where each of them repeats three times. If A, B, and C are records, and record C has a field called F1, there are 27 possible F1 values from which to choose. If you link F1 to an **Index** functoid and specify the constant value one (1) as parameter 2, the functoid outputs the value of F1 from the first occurrence of C within every occurrence of B within every occurrence of A, for a total of 9 values.  
  
 Adding more parameters to the functoid causes the functoid to output fewer values by limiting the occurrences of B and A from which values are retrieved. Continuing the example above, if you add the constant value two (2) as parameter 3, the functoid outputs the value of F1 from the first occurrence of C within each second occurrence of B within every occurrence of A, for a total of 3 values. Adding a fourth parameter that is set to a constant value of one (1), two (2), or three (3) reduces the output to a single value.  
  
## See Also  
 [Advanced Functoids Reference](../core/advanced-functoids-reference.md)   
 [Advanced Functoids](../core/advanced-functoids.md)   
 [Index Functoid](../core/index-functoid.md)   
 [How to Add Index Functoids to a Map](../core/how-to-add-index-functoids-to-a-map.md)