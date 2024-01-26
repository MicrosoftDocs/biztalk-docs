---
description: "Learn more about: SNAGetBuffer"
title: "SNAGetBuffer1"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# SNAGetBuffer
The **SNAGetBuffer** function is called by an application to get a buffer with a requested number of elements.  
  
```  
PTRBFHDR SNAGetBuffer(  
INTEGER numelts  
);  
```  
  
## Parameters  
 *numelts*  
 Number of elements required.  
  
## Return Values  
 A pointer to the buffer obtained. NULL if a buffer could not be obtained.  
  
## Remarks  
 Each element has a size of 268, the constant SNANBEDA in the header file SNA_DLC.H.  
  
 The returned buffer consists of a header and the required number of elements. The header points to the first element, which points to the next element and so on to make an element chain.  
  
 It is possible to add an element to an existing buffer by calling [SNAGetElement](../core/snagetelement1.md) to get the extra element. The new element should be added to the element chain of the buffer, and the number of elements count should be updated.  
  
 The application must release any buffers that are not transmitted.
