---
title: "GetFmiReturnCode1 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6383b568-6918-4e60-8379-873239056f44
caps.latest.revision: 3
author: MandiOhlinger
manager: anneta
---
# GetFmiReturnCode
The **GetFmiReturnCode** function converts link status and error codes to a printable string. This function provides a standard set of error strings for use by Function Management Interface (FMI) applications.  
  
## Syntax  
  
```  
  
int WINAPI GetFmiReturnCode (  
    UINT errcode1,  
    UINT errcode2,  
    UINT buffer_length,  
    unsigned char FAR *buffer_addr  
);  
```  
  
#### Parameters  
 *errcode1*  
 Supplied parameter; see Remarks.  
  
 *errcode2*  
 Supplied parameter; see Remarks.  
  
 *buffer_length*  
 Supplied parameter; specifies the length of the buffer pointed to by *buffer_addr*. The recommended length is 256 characters.  
  
 *buffer_addr*  
 Supplied/returned parameter; specifies the address of the buffer that will hold the formatted, null-terminated string.  
  
## Return Values  
 0x20000001  
 The parameters are invalid; the function could not read the specified error codes or could not write to the specified buffer.  
  
 0x20000002  
 The specified buffer is too small.  
  
## Remarks  
 The *errcode1* and *errcode2* parameters are set according to the way that **GetFmiReturnCode** is used, as shown in the following table.  
  
|Codes to be translated|Value for *errcode1*|Value for *errcode2*|  
|----------------------------|--------------------------|--------------------------|  
|The *errcode1* and *errcode2* values specified in [Error and Sense Codes](../Topic/Error%20and%20Sense%20Codes1.md) includes messages for**Open(SSCP) Response**, **Open(PLU) Confirm**, **Status-Acknowledge(Nack-2)**, **Status-Control(...) Nack2**, **Status-Error**, and **Appl-Data** messages with the system detected error indicator (SDI) set|Unchanged from message|Unchanged from message|  
|The status and qualifier codes returned from a [Status-Session](../core/status-session.md) message|*status*\*256 + *qualifier*|0xFFFF|  
|The return code from **WinLUAGetLastInitStatus**|The return code|0xFFFF|