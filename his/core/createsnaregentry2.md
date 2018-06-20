---
title: "CreateSNARegEntry2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0e056dc3-ace4-4e7c-800d-7d58384a3281
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# CreateSNARegEntry
The **CreateSNARegEntry** function creates the necessary entries for an instance in the **SOFTWARE\Microsoft** registry tree. If the product is not already in the registry, it creates an entry for the product. It then creates an entry for the particular instance of the product and for the **NetRules** key under that entry. This function leaves open handles to all the important subkeys for further use.  
  
## Parameters  
 *Argument 0*  
 Name of the top-level registry node to use. This should be a full registry path. For most scenarios, this is the value held in the *ProductRegBase* variable (**SOFTWARE\Microsoft**).  
  
 *Argument 1*  
 Name of the product. This is the name of the key that will be created for this product.  
  
 *Argument 2*  
 Instance index. This is the index of this particular instance of this product.  
  
## Return Values  
 *Return 0*  
 Status of the operation:  
  
- STATUS_SUCCESSFUL: Operation succeeded.  
  
- STATUS_FAILED: Operation failed.  
  
  *Return 1*  
  Handle to the top-level registry node.  
  
  *Return 2*  
  Handle to the products registry key under the top-level node.  
  
  *Return 3*  
  Handle to the instance entry under the product key.  
  
  *Return 4*  
  Handle to the NetRules entry under the instance key.