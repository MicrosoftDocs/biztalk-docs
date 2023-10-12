---
description: "Learn more about: FindSNARegEntry"
title: "FindSNARegEntry1"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# FindSNARegEntry
The **FindSNARegEntry** function is written as a parallel to [CreateSNARegEntry](../core/createsnaregentry2.md). When called, it attempts to open all of the necessary registry keys and return open handles to them.  
  
## Parameters  
 *Argument 0*  
 Name of the top-level registry node to use.  
  
 *Argument 1*  
 Name of the product.  
  
 *Argument 2*  
 Instance index.  
  
## Return Values  
 *Return 0*  
 Status of the operation.  
  
 *Return 1*  
 Handle to the top-level registry node.  
  
 *Return 2*  
 Handle to the products registry key under the top-level node.  
  
 *Return 3*  
 Handle to the instance entry under the product key.  
  
 *Return 4*  
 Handle to the NetRules entry under the instance key.
