---
description: "Learn more about: SNAGetLinkPerfArea"
title: "SNAGetLinkPerfArea2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0a0de082-65a9-43a3-a7fe-4b94d46065d9
caps.latest.revision: 3
author: "christopherhouser"
ms.author: "hisdocs"
manager: "anneta"
---
# SNAGetLinkPerfArea
The **SNAGetLinkPerfArea** function returns a pointer to the shared data area used by the Perfmon application to store the link statistics. The parameters are the returned values from **SNAInitLinkPerfmon**. The SNA link then maintains the **ADAPTERCOUNTER** members of the returned **ADAPTERPERFDATA** structure.  
  
## Syntax  
  
```  
  
            ADAPTERPERFDATA * SNAGetLinkPerfArea(   
HANDLEshrlockmutx,  
ADAPTERPERFDATA *shrptr   
);  
```  
  
#### Parameters  
 *shrlockmutx*  
 The handle of a mutex used to protect a block of shared memory that will contain the **ADAPTERPERFDATA** structure for this SNA link. The address of this handle is returned by the **SNAInitLinkPerfmon** function.  
  
 *shrptr*  
 A pointer to a block of shared memory returned by **SNAInitLinkPerfmon** that will contain the **ADAPTERPERFDATA** structure used by the Perfmon functions for this SNA link.  
  
## See Also  
 [ADAPTERPERFDATA](../core/adapterperfdata2.md)   
 [SNAInitLinkPerfmon](../core/snainitlinkperfmon1.md)
