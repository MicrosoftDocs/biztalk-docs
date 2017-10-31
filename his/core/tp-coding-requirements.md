---
title: "TP Coding Requirements1 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 87e49823-d66c-41f2-b51b-d530adf89029
caps.latest.revision: 3
---
# TP Coding Requirements
To work with CICS, TPs must be coded to specify a SYSID parameter on the **ALLOCATE** request that matches the defined SYSIDNT parameter configured in the DFHTCT tables. This request must be in the following format:  
  
```  
EXEC CICS ALLOCATE SYSID('DC11')  
  
```  
  
 The SYSID field must match the SYSIDNT field specified for a CICS program by the DFHTCT definition in the TCT (Terminal Control Table). The TCT then uses the NETNAME parameter to refer to a specific LU in the VTAM table of the NAUs (Network Addressable Units). This parameter is used by the TP to communicate with the remote system.  
  
## See Also  
 [VTAM Definitions](../core/vtam-definitions.md)