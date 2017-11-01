---
title: "AddPerfmonCounters1 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8c8adb4e-34d7-4a7e-a942-b256679a9cfc
caps.latest.revision: 3
---
# AddPerfmonCounters
The **AddPerfmonCounters** function is used to add Perfmon counters to a link service. This utility function is used to construct an integrated link service configuration dynamic-link library (DLL).  
  
## Syntax  
  
```  
  
          void AddPerfmonCounters(   
LPSTRpszComputerName,  
LPSTRpszService);  
```  
  
#### Parameters  
 *pszComputerName*  
 This supplied parameter specifies the name of the computer that is to have Perfmon counters added.  
  
 *pszService*  
 This supplied parameter specifies the name of the link service that is to have Perfmon counters added.  
  
## Return Value  
 None.  
  
## Remarks  
 SNA RPC Service must be running or an error message will indicate a failure.