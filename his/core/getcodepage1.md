---
description: "Learn more about: GetCodePage"
title: "GetCodePage1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d9302c79-8eaa-4300-91fb-78df7635c6c1
caps.latest.revision: 3
author: "christopherhouser"
ms.author: "hisdocs"
manager: "anneta"
---
# GetCodePage
The SNA National Language Support (SNANLS) **GetCodePage** function copies the code page information identified by a key to a structure passed as a parameter.  
  
## Syntax  
  
```  
  
BOOL WINAPI GetCodePage(   
        Int nKey  
struct CodePage *pPage  
);  
```  
  
#### Parameters  
 *nKey*  
 Supplied parameter. The numeric key to a code page. This value is an opaque index into an array containing the code pages supported by SNANLS. This value is normally the *CodePageKey* member of a CodePage structure returned from a previous call to **FindFirstCodePage** or **FindNextCodePage**.  
  
 *pPage*  
 Supplied and returned parameter. A pointer to struct CodePage where the code page information should be copied.  
  
 On a successful return, the memory location pointed to by this parameter will be filled with the information for the specific code page.  
  
 On failure, no changes will be made to the memory pointed to by this parameter.  
  
 The CodePage struct is defined in the SNANLS.H include file as follows:  
  
```  
struct CodePage {  
    BYTE    CodePageKey;  
    DWORD   CodePageID;  
    WCHAR   szFriendlyName[CP_SIZE];  
    short   eGroup;  
    BOOL    bAvailable;  
    BYTE    bccsid;  
    BOOL    bEuro;  
};  
```  
  
 The members of this CodePage structure are as follows:  
  
 CodePageKey  
  
 A numeric value that represents the index into the array of CodePage structures. This value should be used as an opaque value, since this value can be changed arbitrarily by Service Packs when additional code pages are supported.  
  
 CodePageID  
  
 The NLS code page number.  
  
 szFriendlyName  
  
 The SNANLS display name for this code page. The character string is null terminated.  
  
 eGroup  
  
 The group that this code page is represented by. .This value can be one of the following enumerations defined in the SNANLS.h include file for code groups:  
  
 ENUM_CP_EBCDIC  
  
 This code page is a member of the EBCDIC code page group.  
  
 ENUM_CP_ANSI  
  
 This code page is a member of the ANSI code page group.  
  
 ENUM_CP_ISO  
  
 This code page is a member of the ISO code page group.  
  
 ENUM_CP_OEMPC  
  
 This code page is a member of the OEM PC code page group.  
  
 ENUM_CP_ISO  
  
 This code page is a member of the ISO code page group.  
  
 ENUM_CP_ISO  
  
 This code page is a member of the ISO code page group.  
  
 ENUM_CP_OEM PC  
  
 This code page is a member of the OEM PC code page group.  
  
 ENUM_CP_OPEN  
  
 This code page is a member of the Open Systems code page group.  
  
 ENUM_CP_UCS  
  
 This code page is a member of the UCS code page group.  
  
 bAvailable  
  
 A Boolean used to indicate that this code page is installed on the computer. A value of **FALSE** for this member indicates that the computer will not be queried to determine if this code page is installed. A value of **TRUE** indicated the code page is installed.  
  
 bccsid  
  
 A flag used to indicate the type of code page. This flag can be one of the following:  
  
 ENUM_CP_DBCS (0x08)  
  
 The code page is for a double-byte character set.  
  
 ENUM_CP_MBCS (0x10)  
  
 The code page is for a mixed-byte character set.  
  
 ENUM_CP_SBCS (0x20)  
  
 The code page is for a single-byte character set.  
  
 bEuro  
  
 A Boolean value used to indicate if this code page supports the Euro symbol. If this value is **TRUE**, then the euro symbol is supported.  
  
## Return Value  
 The **GetCodePage** function returns a value of **TRUE** on success. On failure, the returned value is **FALSE**.  
  
## Remarks  
 This function is supported by SNANLS on Host Integration Server.
