---
title: "FindNextAvailableIndex1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e1aad8a5-2844-4644-bc39-777c0721211d
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# FindNextAvailableIndex
The **FindNextAvailableIndex** function is used to determine the index a new instance should receive. For example, if the current indexes in use are { 01, 02, 04 }, this function would return 03 as its return value.  
  
## Parameters  
 *Argument 0*  
 A list of the indexes currently in use. This list can be obtained by using the [FindSNAProductServices](../core/findsnaproductservices1.md) function.  
  
## Return Values  
 *Return 0*  
 Status of the operation:  
  
- STATUS_SUCCESSFUL: Operation succeeded.  
  
- STATUS_FAILED: Operation failed.  
  
  *Return 1*  
  First available index for the list.