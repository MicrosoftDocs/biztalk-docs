---
description: "Learn more about: FindSNAProductServices"
title: "FindSNAProductServices1"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
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
