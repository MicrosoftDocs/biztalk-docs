---
title: "FindSNAService1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 678c574c-033e-49b6-8cc6-66358b2c6b2a
caps.latest.revision: 3
---
# FindSNAService
The **FindSNAService** function is written as a parallel to [CreateSNAService](../HIS2010/createsnaservice2.md). It is written to provide an easy way to access the keys for a particular service.  
  
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