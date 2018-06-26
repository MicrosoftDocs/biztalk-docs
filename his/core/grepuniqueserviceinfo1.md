---
title: "GrepUniqueServiceInfo1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9b77de57-6973-446c-ab4f-82ababe1e0c5
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# GrepUniqueServiceInfo
The **GrepUniqueServiceInfo** function is used to determine information about a particular instance when only one of the four elements (index, name, title, or description) is available. Because there is no way to determine the position of an element in a list, it is hard to figure out the respective name, title, or description of an instance given only the index. This function searches the list and returns the rest of the information about the instance.  
  
## Parameters  
 *Argument 0*  
 Type of information to search:  
  
- INDEX: Search the list of indexes.  
  
- NAME: Search the list of service names.  
  
- TITLE: Search the list of titles.  
  
- DESC: Search the list of descriptions.  
  
  *Argument 1*  
  Keyword to search for in the list.  
  
  *Argument 2*  
  List of indexes for the instances of this product.  
  
  *Argument 3*  
  List of service names for the instances of this product.  
  
  *Argument 4*  
  List of titles for the instances of this product.  
  
  *Argument 5*  
  List of descriptions for the instances of this product.  
  
## Return Values  
 *Return 0*  
 Status of the operation.  
  
 *Return 1*  
 Index for this instance of the product.  
  
 *Return 2*  
 Service name for this instance of the product.  
  
 *Return 3*  
 Title for this instance of the product.  
  
 *Return 4*  
 Description for this instance of the product.