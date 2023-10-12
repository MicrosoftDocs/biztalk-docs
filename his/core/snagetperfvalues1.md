---
description: "Learn more about: SNAGetPerfValues"
title: "SNAGetPerfValues1"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
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
 [ADAPTERPERFDATA](../core/adapterperfdata2.md)   
 [SNAGetLinkPerfArea](../core/snagetlinkperfarea2.md)
