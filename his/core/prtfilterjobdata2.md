---
description: "Learn more about: PrtFilterJobData"
title: "PrtFilterJobData2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7e47a6be-666b-44df-a4af-8dda022fe7e2
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs"
manager: "anneta"
---
# PrtFilterJobData
The **PrtFilterJobData** function is called to give the user DLL the opportunity to manipulate the printer data before it is printed. This allows the DLL to provide custom processing for print data sent to the print server.  
  
## Syntax  
  
```  
  
          void WINAPI PrtFilterJobData(   
void *UniqueID,   
char **pBufPtr,   
DWORD *pBufLen  );  
```  
  
#### Parameters  
 *UniqueID*  
 Supplied parameter. The *UniqueID* value returned by the **PrtFilterJobStart** function to identify a print job.  
  
 *pBufPtr*  
 The print server passes the print data received from the host to the user DLL for processing in this incoming buffer. The user DLL returns to the print server a pointer to an outgoing buffer of data to be printed. This outgoing buffer pointer can be different from the received buffer pointer because the print data filter DLL can modify the data. Note that in this case **PrtFilterFree** will only be called by the Host Print Service for the outgoing buffer pointer. If necessary, the print data filter DLL must call its own free function on the incoming buffer pointer that was supplied to the **PrtFilterJobData** function. This incoming buffer was allocated by a Host Print Service by a previous call to **PrtFilterAlloc.**  
  
 *pBufLen*  
 Indicates the length of the data passed in the buffer to the print server and the length of the buffer returned to the print server by the user-provided DLL.  
  
## Remarks  
 The data in the buffer is printable ASCII and/or printer control sequences if these are being sent in the print jobs. The buffer returned by the user DLL does not have to be the same as the buffer passed in. The returned buffer will always be freed by calling **PrtFilterFree** after the data has been spooled. The unique identifier parameter *UniqueID* is the identifier returned from a previous call to the **PrtFilterJobStart** function.  
  
## See Also  
 [PrtFilterFree](../core/prtfilterfree1.md)   
 [PrtFilterJobStart](../core/prtfilterjobstart1.md)
