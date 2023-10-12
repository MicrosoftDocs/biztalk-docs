---
description: "Learn more about: PrtFilterAlloc"
title: "PrtFilterAlloc2"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# PrtFilterAlloc
The **PrtFilterAlloc** function is called to obtain a data buffer from the user filter DLL in which to pass it the print data.  
  
## Syntax  
  
```  
  
            void * WINAPI PrtFilterAlloc(   
  DWORD BufLen    
);  
```  
  
#### Parameters  
 *BufLen*  
 Supplied parameter. Indicates the length of buffer required.  
  
## Return Value  
 The **PrtFilterAlloc** function allocates a memory block of *BufLen* size and returns a pointer to the buffer. This function should return a NULL pointer on failure.  
  
## See Also  
 [PrtFilterFree](../core/prtfilterfree1.md)
