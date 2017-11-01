---
title: "PrtFilterJobEnd1 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ec8853af-95fb-44ac-8245-6bd67a71f225
caps.latest.revision: 3
author: MandiOhlinger
manager: anneta
---
# PrtFilterJobEnd
The **PrtFilterJobEnd** function is called to inform the print data filter DLL that a print job is about to end. This allows the DLL to provide custom processing and send special data to the print server at the end of a print job.  
  
## Syntax  
  
```  
  
            void * WINAPI PrtFilterJobEnd(   
  void *UniqueID,   
  char **pBufPtr,   
  DWORD *pBufLen    
);  
```  
  
#### Parameters  
 *UniqueID*  
 Supplied parameter. The *UniqueID* value returned by the **PrtFilterJobStart** function to identify a print job.  
  
 *pBufPtr*  
 Returned parameter. Specifies a pointer to a buffer pointer holding additional data to be printed by the print server.  
  
 *pBufLen*  
 Returned parameter. Pointer to the length of the data provided by the print data filter DLL in the buffer.  
  
## Remarks  
 No data is passed in the buffer, but the user DLL can return print data which will be sent to the printer before the print job is ended.  
  
## See Also  
 [PrtFilterJobStart](../core/prtfilterjobstart.md)