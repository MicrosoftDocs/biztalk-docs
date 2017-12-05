---
title: "PrtFilterFree2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b2c56628-ca4a-422f-8d11-b4377f25b043
caps.latest.revision: 3
---
# PrtFilterFree
The **PrtFilterFree** function is called to indicate that a data buffer obtained previously from the DLL is no longer needed and the DLL can free the memory allocated for this resource. This function is called for data buffers returned from calls to **PrtFilterAlloc** as well as buffers that were allocated by the DLL to pass data in the **PrtFilterStartJob**, **PrtFilterJobData**, and **PrtFilterEndJob** functions.  
  
## Syntax  
  
```  
  
            void WINAPI PrtFilterFree(   
  void *pBuf    
);  
```  
  
#### Parameters  
 *pBuf*  
 Supplied parameter. Points to the data buffer that can be freed.  
  
## See Also  
 [PrtFilterAlloc](../HIS2010/prtfilteralloc1.md)