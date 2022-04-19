---
description: "Learn more about: RemovePerfmonCounters"
title: "RemovePerfmonCounters1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e55441bb-5a65-429e-8e41-6cbd5a4cf791
caps.latest.revision: 3
author: "christopherhouser"
ms.author: "hisdocs"
manager: "anneta"
---
# RemovePerfmonCounters
The **RemovePerfmonCounters** function is used to remove counters from a link service. This utility function is used to construct an integrated link service configuration DLL.  
  
## Syntax  
  
```  
  
          void RemovePerfmonCounters(   
LPSTRpszComputerName,  
LPSTRpszService);  
```  
  
#### Parameters  
 *pszComputerName*  
 This supplied parameter specifies the name of the computer that is to have Perfmon counters removed.  
  
 *pszService*  
 This supplied parameter specifies the name of the link service that is to have Perfmon counters removed.  
  
## Return Value  
 None.  
  
## Remarks  
 SNA RPC Service must be running or an error message will indicate a failure.
