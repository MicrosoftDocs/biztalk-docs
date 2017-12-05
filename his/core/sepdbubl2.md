---
title: "sepdbubl2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 13ed51dc-524b-4260-993d-3e9f5cd145fe
caps.latest.revision: 3
---
# sepdbubl
The application calls the **sepdbubl** function to get a buffer with a requested number of elements.  
  
## Syntax  
  
```  
  
PTRBFHDR sepdbubl(  
USHORT noelts  
);  
```  
  
#### Parameters  
 *noelts*  
 Number of elements required.  
  
## Return Value  
 A pointer to the buffer obtained. NULL if a buffer could not be obtained.  
  
## Remarks  
 Each element has a size of 268—the constant SNANBEDA in the header file FMI.H.  
  
 The returned buffer consists of a header and the required number of elements. The header points to the first element, which points to the next element, and so on to make an element chain.  
  
 It is possible to add an element to an existing buffer by calling [sbpibegt](../core/sbpibegt1.md) to get the extra element. The new element should be added to the element chain of the buffer, and the "number of elements" count should be updated.  
  
 The application must release any buffers that are not transmitted.