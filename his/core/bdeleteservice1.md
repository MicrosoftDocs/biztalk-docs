---
description: "Learn more about: bDeleteService"
title: "bDeleteService1"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# bDeleteService
The **bDeleteService** function is used to delete a service on a computer for a link service. This utility function is used to construct an integrated link service configuration dynamic-link library (DLL).  
  
## Syntax  
  
```  
  
          BOOL bDeleteService(   
LPSTRszComputerName,  
LPSTRszServiceName);  
```  
  
#### Parameters  
 *szComputerName*  
 This supplied parameter specifies the name of the computer to delete the service on.  
  
 *szServiceName*  
 This supplied parameter specifies the name of the service that is to be deleted. This parameter is passed unchanged to the Microsoft Windows **OpenService**  function.  
  
## Return Value  
 TRUE  
 The function executed successfully and the service was deleted.  
  
 FALSE  
 One or more of the parameters passed to this function are invalid or the function failed.
