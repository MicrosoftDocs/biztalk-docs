---
description: "Learn more about: bStopService"
title: "bStopService2"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# bStopService
The **bStopService** function is used to stop a service running on a computer for a link service. This utility function is used to construct an integrated link service configuration dynamic-link library (DLL).  
  
## Syntax  
  
```  
  
          BOOL bStopService(   
LPSTRszServiceName,  
LPSTRszComputerName);  
```  
  
#### Parameters  
 *szServiceName*  
 This supplied parameter specifies the name of the service that is to be stopped. This parameter is passed unchanged to the Microsoft Windows **OpenService**  function.  
  
 *szComputerName*  
 This supplied parameter specifies the name of the computer to stop the service on.  
  
## Return Value  
 TRUE  
 The function executed successfully and the service was stopped.  
  
 FALSE  
 One or more of the parameters passed to this function are invalid or the function failed.
