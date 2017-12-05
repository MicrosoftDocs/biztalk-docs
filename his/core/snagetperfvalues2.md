---
title: "SNAGetPerfValues2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d342333f-6483-4a9f-8917-119c9661e364
caps.latest.revision: 3
---
# SNAGetPerfValues
The **SNAGetPerfValues** function is used to provide pointers to the *ServiceNameIndex* and *FirstCounterIndex* variables so that the Perfmon application knows where to get the descriptions of the performance counters from the registry. These variables are returned as members in the **ADAPTERPERFDATA** structure returned by the **SNAGetLinkPerfArea** function.  
  
## Syntax  
  
```  
  
            USHORT SNAGetPerfValues(  
            int *pServiceNameIndex,int *pFirstCounterIndex   
);  
```  
  
#### Parameters  
 *pServiceNameIndex*  
 A pointer to the **ServiceNameIndex** member of the **ADAPTERPERFDATA** structure.  
  
 *pFirstCounterIndex*  
 A pointer to the **FirstCounterIndex** member of the **ADAPTERPERFDATA** structure.  
  
## See Also  
 [ADAPTERPERFDATA](../core/adapterperfdata1.md)   
 [SNAGetLinkPerfArea](../core/snagetlinkperfarea1.md)