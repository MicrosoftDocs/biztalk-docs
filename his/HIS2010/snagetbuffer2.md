---
title: "SNAGetBuffer2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 28a0a2b3-3df4-4b82-84e5-c5988b7de4dd
caps.latest.revision: 3
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
  
 It is possible to add an element to an existing buffer by calling [SNAGetElement](../HIS2010/snagetelement2.md) to get the extra element. The new element should be added to the element chain of the buffer, and the number of elements count should be updated.  
  
 The application must release any buffers that are not transmitted.