---
title: "Find Method | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Find method"
ms.assetid: 676827a6-82af-4922-bf9e-aca5bd23624b
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Find Method
Used to return a list of keys that satisfy the supplied partial search keys. Note that for a component interface that has only one instance, that is, there is no key, the `Find()` function is not generated. See also [Get Method](../core/get-method.md).  
  
## Syntax  
  
```  
Find (partialKey, keyList)  
```  
  
## Parameters  
  
|Parameter|Description|  
|---------------|-----------------|  
|`partialKey`|A structure where the individual keys are optional.|  
|`keyList`|A list of keys that matches the `partialKey`. It is an output parameter.<br /><br /> The keys correspond to the set of Find Keys as defined for the particular component interface.|  
  
## Remarks  
 When you specify the partial keys, it is possible to use the same wildcard search available from the PeopleSoft internal `Find()` function. For example, the partial ACCOUNT key of "11" returns all ACCOUNT keys that start with "11", whereas "%40" returns all ACCOUNT keys that contain "40" anywhere within the key. A partial key "_4_4" returns all ACCOUNT keys with the character "4" in the 2nd and 4th positions.  
  
 Note: With the current implementation of the PeopleSoft Server, if more than 300 items match the search criteria, the call fails. This is a restriction of the PeopleSoft server. The Microsoft BizTalk Adapter for PeopleSoft Enterprise `Find()` method is provided if the PeopleSoft `Find` function in the component interface is enabled and Get keys are available.  
  
## See Also  
 [Appendix A: Component Interface Methods](../core/appendix-a-component-interface-methods.md)