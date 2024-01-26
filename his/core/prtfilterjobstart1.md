---
description: "Learn more about: PrtFilterJobStart"
title: "PrtFilterJobStart1"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# PrtFilterJobStart
The **PrtFilterJobStart** function is called to inform the print data filter DLL that a new job has just been started. This allows the DLL to provide custom processing and send special data to the print server at the beginning of a job.  
  
## Syntax  
  
```  
  
          void * WINAPI PrtFilterJobStart(   
char *SessionName,    
DWORD LUType,         
char **pBufPtr,       
DWORD *pBufLen      );  
```  
  
#### Parameters  
 *SessionName*  
 Supplied parameter. The name of the print session which has just started a print job. The *SessionName* is the same as that configured in using the SNA Print Service Admin tool.  
  
 *LUType*  
 Supplied parameter. Specifies the printer type. Valid values are LU 1, LU 3, or LU 6.2 printers, represented by an *LUType* value of 1, 3, or 6.  
  
 *pBufPtr*  
 Returned parameter. Specifies a pointer to a buffer pointer holding additional data to be printed by the print server.  
  
 *pBufLen*  
 Returned parameter. Pointer to the length of the data provided by the print data filter DLL in the buffer.  
  
## Return Value  
 The **PrtFilterJobStart** function returns a unique identifier (cast to a pointer to a void) if it wants the opportunity to filter the data for this print job.  
  
 If the user DLL returns a NULL pointer, it is indicating that it is not interested in filtering this job. No further calls to the user DLL will be made for this print job.  
  
## Remarks  
 No data is passed in the data buffer to the print data filter DLL in this call, but the DLL can return data in *pBufPtr* (for example, a banner page). The data returned from this call should be printable ASCII and/or printer control sequences.
