---
title: "FindSNAService2 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 321ac6cd-2e25-4efa-b783-9c76c889dcd0
caps.latest.revision: 3
---
# FindSNAService
The **FindSNAService** function is written as a parallel to [CreateSNAService](../core/createsnaservice.md). It is written to provide an easy way to access the keys for a particular service.  
  
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