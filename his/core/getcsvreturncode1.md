---
title: "GetCsvReturnCode1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c9943992-4fae-41c8-871f-da33094662ef
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# GetCsvReturnCode
The **GetCsvReturnCode** function converts the primary and secondary return codes in the verb control block to a printable string. This function provides a standard set of error strings for use by applications using common service verbs (CSVs).  
  
## Syntax  
  
```  
  
    int WINAPI GetCsvReturnCode(   
struct csv_hdr FAR * vpb,  
UINTbuffer_length,  
unsigned char FAR * buffer_addr);  
```  
  
#### Parameters  
 *vpb*  
 Supplied parameter. Specifies the address of the verb control block.  
  
 *buffer_length*  
 Supplied parameter. Specifies the length of the buffer pointed to by *buffer_addr*. The recommended length is 256.  
  
 *buffer_addr*  
 Supplied parameter. Specifies the address of the buffer that will hold the formatted, null-terminated string when the function completes.  
  
## Return Value  
 The **GetCsvReturnCode** function returns a positive value on success that indicates the length of the error string passed back in *buffer_addr*.  
  
 A return value of zero indicates an error. On Microsoft Windows a call to **GetLastError** provides the actual error return code as follows:  
  
 0x20000001  
 The parameters are invalid; the function could not read from the specified verb parameter block or could not write to the specified buffer.  
  
 0x20000002  
 The specified buffer is too small.  
  
 0x20000003  
 The CSV string library CSVST32.DLL could not be loaded.  
  
## Remarks  
 The descriptive error string returned in *buffer_addr* does not terminate with a newline character (**\n**).  
  
 The descriptive error strings are contained in CSVST32.DLL and can be customized for different languages.