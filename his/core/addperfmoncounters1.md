---
description: "Learn more about: AddPerfmonCounters"
title: "AddPerfmonCounters1"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
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
