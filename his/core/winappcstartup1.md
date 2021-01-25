---
description: "Learn more about: WinAPPCStartup"
title: "WinAPPCStartup1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b7d0702d-fa4a-4a35-a4de-2edfabf8582b
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs"
manager: "anneta"
---
# WinAPPCStartup
The **WinAPPCStartup** function allows an application to specify the version of Windows APPC required and to retrieve details of the specific Windows APPC implementation. An application must call this function to register itself with a Windows APPC implementation before issuing any further Windows APPC calls.  
  
## Syntax  
  
```  
  
            int WINAPI WinAPPCStartup(   
        WORDwVersionRequired,  
        LPWAPPCDATAlpAPPCData  
);  
  
typedef struct {  
    WORD wVersion;  
    char szDescription[WAPPCDESCRIPTION_LEN+1];  
} WAPPCDATA, FAR * LPWAPPCDATA;  
  
where WAPPCDESCRIPTION_LEN is defined as 127  
```  
  
#### Parameters  
 *wVersionRequired*  
 Specifies the version of Windows APPC support required. The high-order byte specifies the minor version (revision) number; the low-order byte specifies the major version number. The current version of the Windows APPC API is 1.0.  
  
 *lpAPPCData*  
 Pointer to a returned structure containing a Windows APPC version number and a description of the Windows APPC implementation.  
  
## Return Value  
 The return value specifies whether the application was registered successfully and whether the Windows APPC implementation can support the specified version number. If the value is zero, it was registered successfully and the specified version can be supported. Otherwise, the return value is one of the following:  
  
 WAPPCSYSNOTREADY  
 The underlying network system is not ready for network communication.  
  
 WAPPCVERNOTSUPPORTED  
 The version of Windows APPC support requested is not provided by this particular Windows APPC implementation.  
  
 WAPPCINVALID  
 The Windows APPC version specified by the application is not supported by this DLL.  
  
## Remarks  
 To support future Windows APPC implementations and applications that may have functionality differences from Windows APPC version 1.0, a negotiation takes place in **WinAPPCStartup**. An application passes to **WinAPPCStartup** the Windows APPC version that it can use. If this version is lower than the lowest version supported by the Windows APPC DLL, the DLL cannot support the application and **WinAPPCStartup** fails. If the version is not lower, however, the call succeeds and returns the highest version of Windows APPC supported by the DLL. If this version is lower than the lowest version supported by the application, the application either fails its initialization or attempts to find another Windows APPC DLL on the system.  
  
 This negotiation allows both a Windows APPC DLL and a Windows APPC application to support a range of Windows APPC versions. An application can successfully use a DLL if there is any overlap in the versions. The following table illustrates how **WinAPPCStartup** works in conjunction with different application and DLL versions.  
  
|Application versions|DLL versions|To WinAPPCStartup|From WinAPPCStartup|Result|  
|--------------------------|------------------|-----------------------|-------------------------|------------|  
|1.0|1.0|1.0|1.0|Use 1.0|  
|1.0, 2.0|1.0|2.0|1.0|Use 1.0|  
|1.0|1.0, 2.0|1.0|2.0|Use 1.0|  
|1.0|2.0, 3.0|1.0|WAPPCINVALID|Fail|  
|2.0, 3.0|1.0|3.0|1.0|App Fails|  
|1.0, 2.0, 3.0|1.0, 2.0, 3.0|3.0|3.0|Use 3.0|  
  
 Details of the actual Windows APPC implementation are described in the **WAPPCDATA** structure defined as follows that is returned by **WinAPPCStartup**:  
  
```  
typedef struct tagWAPPCDDATA { WORD wVersion;  
char szDescription[WAPPCDESCRIPTION_LEN+1];  
} WAPPCDATA, FAR *LPWAPPCDATA;  
```  
  
 The structure members are as follows:  
  
 **wVersion**  
 The highest APPC version number supported by the Windows APPC DLL.  
  
 **szDescription**  
 A descriptive string describing the WinAPPC implementation.  
  
 After it makes its last Windows APPC call, an application should call the [WinAPPCCleanup](../core/winappccleanup1.md) routine.  
  
 Each Windows APPC implementation must make a **WinAPPCStartup** call before issuing any other Windows APPC calls.
