---
description: "Learn more about: PASSSTRUCT structure"
title: "PASSSTRUCT structure1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b5ea97f8-7558-4625-92f6-87906c5d9aba
caps.latest.revision: 3
author: "christopherhouser"
ms.author: "hisdocs"
manager: "anneta"
---
# PASSSTRUCT structure
The PASSSTRUCT structure is defined as follows:  
  
## Syntax  
  
```  
  
typedef struct tagPassParm {  
    WORD    parm_length;  
    WORD    exit_code;  
    WORD    in_length;  
    LPBYTE  in_addr;  
    WORD    out_length;  
    LPBYTE  out_addr;  
    WORD    trns_id;  
    WORD    in_page;  
    WORD    out_page;  
    WORD    option;  
} PASSSTRUCT;  
```  
  
## Members  
 **parm_length**  
 Supplied parameter. The length of the structure passed, normally set to 24. If the **option** member is not needed or used, then this parameter can be set to 22.  
  
 **exit_code**  
 Supplied and returned parameter. On entry this member must be set to zero. On return, this member indicates the exit status. Legal values for returned **exit_code** values are as follows:  
  
 0  
  
 Normal exit code indicating function completed successfully.  
  
 1  
  
 The requested conversion is not supported.  
  
 12  
  
 The **exit_code** field was not properly initialized to zero.  
  
 128  
  
 The last character in the source input string was a DBCS lead byte.  
  
 256  
  
 The conversion could not be successfully completed since the length of the resulting converted destination string exceeds 65535 bytes.  
  
 257  
  
 An error occurred when trying to load one and initialize one of the TrnsDTx.dll files.  
  
 **in_length**  
 Supplied parameter. Specifies the length of the input source string in bytes.  
  
 **in_addr**  
 Supplied parameter. A pointer to the buffer containing the source string to be converted.  
  
 **out_length**  
 Supplied and returned parameter. Specifies the maximum length available for the output translated string in bytes. On return, this member is set to the length of the converted output string on success or the output buffer length needed if the buffer was too small.  
  
 **out_addr**  
 Supplied parameter. A pointer to the buffer that will contain the output destination string after conversion.  
  
 **trns_id**  
 Supplied parameter. The conversion identifier, which is always zero.  
  
 **in_page**  
 Supplied parameter. Specifies the code page of the incoming source string.  
  
 **out_page**  
 Supplied parameter. Specifies the code page of the output translated string.  
  
 **option**  
 Supplied and returned parameter if **parm_length** was set to 24. As a supplied parameter, this specifies a set of options that may be applied to the translation process. Possible values for these options are as follows:  
  
 Bits 15-9  
  
 Reserved.  
  
 Bit 8  
  
 Add shift out (SO)/shift in (SI) bytes to the converted output strings.  
  
 Bits 3-7  
  
 Reserved.  
  
 Bit 2  
  
 If this bit is set, then convert the input string using the IBM-specified 1-byte code table. This option is only valid when converting from code page 932 to one of the following code pages: 037, 290, 930, or 931.  
  
 If this bit is zero, then convert the input source string using the conversion table that is created using the SYSCTBL utility.  
  
 In case of double-byte characters, always use the conversion table created by the SYSCTBL utility.  
  
 The SYSCTBL.EXE file is a utility program included with Host Integration Server that provides a tool that can be used to create custom conversion tables for use with the **TrnsDT** function.  
  
 Bit 1  
  
 If this bit is set, then it indicates that the input source string starts with a 2-byte character. Generally, the host data always includes SO/SI control characters in pairs, but when converting part of mixed data strings, it is necessary to start the conversion from a double-byte character without the SO control character. In this case, the data itself does not have adequate information to determine if it is double-byte or not, so bit 1 must be set.  
  
 Bit 0  
  
 If this bit is set, then it indicates that the input source string contains SO/SI control characters. Bit 8 and bit 0 should be set as follows:  
  
 Conversion from PC to host                    Bit 8=1, bit 0 =0  Conversion from host to PC                    Bit 8=0, bit 0=1  
  
 On return, **option** is set to 4 if the last character was a double-byte character.
