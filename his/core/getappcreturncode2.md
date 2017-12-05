---
title: "GetAppcReturnCode2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 497cb779-0407-4a7d-a5fd-ad7c6b660e0b
caps.latest.revision: 4
---
# GetAppcReturnCode
The **GetAppcReturnCode** function converts the primary and secondary return codes in the verb control block to a printable string. This function provides a standard set of error strings for use by APPC applications such as 5250 emulators.  
  
## Syntax  
  
```  
  
    int WINAPI GetAppcReturnCode(   
struct appc_hdr FAR * vpb,  
UINTbuffer_length,  
unsigned char FAR * buffer_addr);  
```  
  
#### Parameters  
 *vpb*  
 Supplied parameter. Specifies the address of the verb control block.  
  
 *buffer_length*  
 Supplied parameter. Specifies the length of the buffer pointed to by *buffer_addr*. The recommended length is 256.  
  
 *buffer_addr*  
 Supplied parameter. Specifies the address of the buffer that will hold the formatted, null-terminated string.  
  
## Return Value  
 The **GetAppcReturnCode** function returns a positive value on success that indicates the length of the error string passed back in *buffer_addr*.  
  
 A return value of zero indicates an error. On Microsoft Windows a call to **GetLastError** provides the actual error return code as follows:  
  
 0x20000001  
 The parameters are invalid; the function could not read from the specified verb control block or could not write to the specified buffer.  
  
 0x20000002  
 The specified buffer is too small.  
  
 0x20000003  
 The APPC string library APPCST32.DLL could not be loaded.  
  
## Remarks  
 The descriptive error string returned in *buffer_addr* does not terminate with a new line character (**\n**).  
  
 The descriptive error strings are contained in APPCST32.DLL and can be customized for different languages.