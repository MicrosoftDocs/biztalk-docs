---
description: "Learn more about: PrtFilterJobEnd"
title: "PrtFilterJobEnd1"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
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
 [PrtFilterJobStart](../core/prtfilterjobstart1.md)
