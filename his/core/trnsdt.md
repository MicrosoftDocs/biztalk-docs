---
title: "TrnsDT1 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ba45e49c-c45b-4856-b81e-1019af172ce4
caps.latest.revision: 4
author: MandiOhlinger
manager: anneta
---
# TrnsDT
The **TrnsDT** function is called to translate a string from one code page to another.  
  
## Syntax  
  
```  
  
WORD WINAPI TrnsDt(  
PASSSTRUCT far* PassParm);  
```  
  
#### Parameters  
 *PassParm*  
 Supplied parameter. A pointer to a **PASSSTRUCT** structure containing members that must be supplied as well as members that are returned by the function.  
  
## Return Value  
 The **TrnsDT** function returns zero on success. On failure, possible values returned by this function are as follows:  
  
 ERR_FILE_NOT_FOUND  
  
 This error is returned if the TrnsDT table files (\*.tbl) could not be found. Normally **TrnsDT** uses the conversion tables located in the Host Integration Server\System directory on Windows Server 2003 R2 SP2, Windows Vista SP2, Windows 7, Windows Server 2008 SP2, and Windows Server 2012. If **TrnsDT** cannot find these tables, it searches for them in the current directory.  
  
 ERR_INVALID_PARAMETER  
  
 This error is returned if a bad value was passed for one or more of the members of the *PassParm* structure. Invalid parameters can include not zeroing the **exit_code** member, passing an **in_length** for the input source string of zero or less or greater than 65535 bytes, passing an **out_length** for the output string buffer of zero or less, passing **in_page** or **out_page** members containing undefined codepage values.  
  
 ERR_BUFFER_OVERFLOW  
  
 This error is returned if the output buffer is too small for the converted output string. In such cases, the **out_length** member returns with the necessary value in bytes for the output buffer. This error is also returned if the length of the output buffer needed to convert the source string would exceed 65535 bytes.  
  
 ERR_MEMORY_ALLOCATE  
  
 This error is returned if memory could not be allocated for use by the TrnsDT DLL.