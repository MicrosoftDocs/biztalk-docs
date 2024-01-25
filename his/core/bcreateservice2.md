---
description: "Learn more about: bCreateService"
title: "bCreateService2"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# bCreateService
The **bCreateService** function is used to create a service on a computer for a link service. This utility function is used to construct an integrated link service configuration dynamic-link library (DLL).  
  
## Syntax  
  
```  
  
          BOOL bCreateService(   
LPSTRszComputerName,  
LPSTRszServiceName,  
LPSTRszServicePath,  
LPSTRszServiceDependencies,  
DWORDdServiceType,  
DWORDdServiceLoadType,  
LPSTRszDomainName,  
LPSTRszUserid,  
LPSTRszPassword);  
```  
  
#### Parameters  
 *szComputerName*  
 This supplied parameter specifies the name of the computer to create the service on.  
  
 *szServiceName*  
 This supplied parameter specifies the name of the link service that is to be created.  This parameter is passed unchanged to the Microsoft Windows **CreateService** function.  
  
 *szServicePath*  
 This supplied parameter specifies the binary path to the link service that is to be created. This parameter is passed unchanged to the Windows **CreateService** function.  
  
 *szServiceDependencies*  
 This supplied parameter specifies the service dependencies of the link service that is to be created. This parameter is passed unchanged to the Windows **CreateService** function.  
  
 *dServiceType*  
 This supplied parameter specifies the type of service that is to be created. This parameter is passed unchanged to the Windows **CreateService** function.  
  
 *dServiceLoadType*  
 This supplied parameter specifies the load type of service that is to be created. This parameter is passed unchanged to the Windows **CreateService** function.  
  
 *szDomainName*  
 This supplied parameter specifies the domain name for the service to run in.  
  
 *szUserid*  
 This supplied parameter specifies the user identifier for the service to run in.  
  
 *szPassword*  
 This supplied parameter specifies the password for the domain account.  
  
## Return Value  
 TRUE  
 The function executed successfully and the service was created.  
  
 FALSE  
 One or more of the parameters passed to this function are invalid or the function failed.  
  
## Remarks  
 If the *szUserid* parameter is not supplied, then the *szDomainName* parameter is used to construct the Account parameter passed to the Windows **CreateService** function.
