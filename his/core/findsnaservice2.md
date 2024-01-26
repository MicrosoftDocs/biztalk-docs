---
description: "Learn more about: FindSNAService"
title: "FindSNAService2"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# FindSNAService
The **FindSNAService** function is written as a parallel to [CreateSNAService](../core/createsnaservice1.md). It is written to provide an easy way to access the keys for a particular service.  
  
## Parameters  
 *Argument 0*  
 Name of the service to look for.  
  
## Return Values  
 *Return 0*  
 Status of the operation.  
  
 *Return 1*  
 Handle to the service key.  
  
 *Return 2*  
 Handle to the **Parameters** key under the service key.  
  
 *Return 3*  
 Handle to the **ExtraParameters** key under the **Parameters** key.
