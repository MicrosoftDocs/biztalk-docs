---
title: "SNAReleaseElement2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 11b406f5-e5a3-46d2-912d-51ecee57f6ff
caps.latest.revision: 3
---
# SNAReleaseElement
The **SNAReleaseElement** function is called by an application to release a buffer element from an existing buffer.  
  
```  
VOID SNAReleaseElement(  
PTRBFELT *eltptr   
);  
```  
  
## Parameters  
 *eltptr*  
 Pointer to a pointer to the element to be released.  
  
## Remarks  
 This function should only be used to release surplus elements from a buffer. [SNAReleaseBuffer](../HIS2010/snareleasebuffer2.md) should be called to release the entire buffer.  
  
 The released element should first be removed from the element chain and the count of the number of elements updated.  
  
 This function is typically used when a received buffer is being reused to transmit a message that is shorter than the incoming message.