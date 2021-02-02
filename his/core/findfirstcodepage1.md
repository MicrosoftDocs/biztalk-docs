---
description: "Learn more about: FindFirstCodePage"
title: "FindFirstCodePage1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 998c9c58-e510-4925-a989-1fb82bfc7071
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs"
manager: "anneta"
---
# FindFirstCodePage
The SNA National Language Support (SNANLS) **FindFirstCodePage** function finds the first instance of a code page satisfying the condition specified, copies the code page information to a structure passed as a parameter, and opens and returns a handle used in subsequent calls to the **FindNextCodePage** function.  
  
## Syntax  
  
```  
  
const HANDLE WINAPI FindFirstCodePage(   
        DWORDdwEnumOption,  
        struct CodePage *pPage  
);  
```  
  
#### Parameters  
 *dwEnumOption*  
 Supplied parameter. The set of conditions that a code page should satisfy. These conditions can be any combination of the following values defined in the SNANLS.h include file:  
  
 ENUM_CP_AVAILABLE (0x01)  
  
 The code page is installed and available for use.  
  
 ENUM_CP_HOST (0x02)  
  
 The code page is a host code page (EBCDIC, for example).  
  
 ENUM_CP_EURO (0x04)  
  
 The code page contains support for the euro character.  
  
 ENUM_CP_DBCS (0x08)  
  
 The code page is for a double-byte character set.  
  
 ENUM_CP_MBCS (0x10)  
  
 The code page is for a mixed-byte character set.  
  
 ENUM_CP_SBCS (0x20)  
  
 The code page is for a single-byte character set.  
  
 Note that some of these combinations represent cases that will not match any installed code pages used by SNANLS.  
  
 *pPage*  
 Supplied and returned parameter. A pointer to a struct CodePage where the code page information should be copied.  
  
 On a successful return, the memory location pointed to by this parameter will be filled with the information for the first code page satisfying the conditions in *dwEnumOption*. On failure, no changes will be made to the memory pointed to by this parameter.  
  
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
  
 The SNANLS display name for this code page.  
  
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
  
 A Boolean value used to indicate if this code page supports the euro symbol. If this value is **TRUE**, then the euro symbol is supported.  
  
## Return Value  
 The **FindFirstCodePage** function returns a handle used in calls to the **FindNextCodePage** or **FindCloseCodePage** on success. On failure, INVALID_HANDLE_VALUE is returned for the value of this handle.  
  
## Remarks  
 The handle returned by this function should not be tampered with by the user.  
  
 This function is supported by SNANLS on Host Integration Server.
