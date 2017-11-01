---
title: "WinCSVStartup1 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: bd110cf8-eabe-4869-b250-436f1c1c6aef
caps.latest.revision: 3
author: MandiOhlinger
manager: anneta
---
# WinCSVStartup
The **WinCSVStartup** function allows an application to specify the version of Windows CSV required and to retrieve details of the specific Windows CSV implementation. This function must be called by an application to register itself with a Windows CSV implementation before issuing any further Windows CSV calls.  
  
## Syntax  
  
```  
  
int WINAPI WinCSVStartup(   
WORD wVersionRequired,  
LPWCSVDATA lpwcsvdata  
);  
```  
  
#### Parameters  
 *wVersionRequired*  
 Specifies the version of Windows CSV support required. The high-order byte specifies the minor version (revision) number; the low-order byte specifies the major version number. The current version of the Windows CSV API is 1.0.  
  
 *lpwcsvdata*  
 A pointer to the CSV data structure. The **CSVDATA** structure is defined as follows:  
  
```  
typedef struct tagWCSVDATA {  
    WORD wVersion;  
    char szDescription[WCSVDESCRIPTION_LEN+1];  
}  CSVDATA, FAR * LPWCSVCDATA;  
```  
  
 where **WCSVDESCRIPTION** is defined to be 127 and the structure members are as follows:  
  
 wVersion  
  
 The version of Windows CSV supported. The high-order byte specifies the minor version (revision) number; the low-order byte specifies the major version number.  
  
 szDescription  
  
 A description string identifying the vendor of the Windows CSV DLL.  
  
 This **CVSDATA** structure provides information about the underlying Windows CSV DLL implementation. The first *wVersion* field has the same structure as the *wVersionRequired* parameter, and the *szDescription* field contains a string identifying the vendor of the Windows CSV DLL. The description field is only meant to provide a display string for the application and should not be used to programmatically distinguish between Windows CSV implementations.  
  
## Return Values  
 The return value specifies whether the application was registered successfully and whether the Windows CSV implementation can support the specified version number. If the value is zero, it was registered successfully. Otherwise, the return value is one of the following:  
  
 WCSVSYSNOTREADY  
 Indicates that the underlying network system is not ready for network communication.  
  
 WCSVVERNOTSUPPORTED  
 The version of Windows CSV support requested is not provided by this particular Windows CSV implementation.  
  
 WCSVINVALID  
 The Windows CSV version specified by the application is not supported by this DLL.  
  
## Remarks  
 To support future Windows CSV implementations and applications that may have functionality differences from Windows CSV version 1.0, a negotiation takes place in **WinCSVStartup**. An application passes to **WinCSVStartup** the Windows CSV version that it can use. If this version is lower than the lowest version supported by the Windows CSV DLL, the DLL cannot support the application and **WinCSVStartup** fails. If the version is not lower, however, the call succeeds and returns the highest version of Windows CSV supported by the DLL. If this version is lower than the lowest version supported by the application, the application either fails its initialization or attempts to find another Windows CSV DLL on the system.  
  
 This negotiation allows both a Windows CSV DLL and a Windows CSV application to support a range of Windows CSV versions. An application can successfully use a DLL if there is any overlap in the versions. The following table illustrates how **WinCSVStartup** works in conjunction with different application and DLL versions.  
  
|Application versions|DLL versions|To WinCSVStartup|From WinCSVStartup|Result|  
|--------------------------|------------------|----------------------|------------------------|------------|  
|1.0|1.0|1.0|1.0|Use 1.0|  
|1.0, 2.0|1.0|2.0|1.0|Use 1.0|  
|1.0|1.0, 2.0|1.0|2.0|Use 1.0|  
|1.0|2.0, 3.0|1.0|WCSVINVALID|Fail|  
|2.0, 3.0|1.0|3.0|1.0|App Fails|  
|1.0, 2.0, 3.0|1.0, 2.0, 3.0|3.0|3.0|Use 3.0|  
  
 After making its last Windows CSV call, an application should call [WinCSVCleanup](../core/wincsvcleanup.md).  
  
 Each Windows CSV implementation must make a **WinCSVStartup** call before issuing any other Windows CSV calls. Consequently, this function can be used for initialization purposes.