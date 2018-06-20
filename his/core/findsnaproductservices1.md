---
title: "FindSNAProductServices1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f78572a5-a5b6-4920-bf91-170ba54c8b73
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# FindSNAProductServices
The **FindSNAProductServices** function enumerates all instances of a product. It returns lists of information for the instances that can be used in the script. This function can also be used to determine whether or not a product exists in the registry by analyzing the return status.  
  
## Parameters  
 *Argument 0*  
 Name of top-level registry node to use.  
  
 *Argument 1*  
 Name of the product.  
  
## Return Values  
 *Return 0*  
 Status of the operation:  
  
- STATUS_SUCCESSFUL: Operation succeeded.  
  
- STATUS_NOSUCHPRODUCT: The product does not exist in the registry.  
  
- STATUS_FAILED: Operation failed.  
  
  *Return 1*  
  List of indexes for the instances of this product.  
  
  *Return 2*  
  List of service names for the instances of this product.  
  
  *Return 3*  
  List of titles for the instances of this product.  
  
  *Return 4*  
  List of descriptions for the instances of this product.