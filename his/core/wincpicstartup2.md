---
description: "Learn more about: WinCPICStartup"
title: "WinCPICStartup2"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# WinCPICStartup
The **WinCPICStartup** function allows an application to specify the version of Microsoft Windows Common Programming Interface for Communications (CPI-C) required and to retrieve details of the specific Windows CPI-C implementation. This function must be called by an application to register itself with a Windows CPI-C implementation before issuing any further Windows CPI-C calls.  
  
## Syntax  
  
```  
  
        INT WINAPI WinCPICStartup(   
WORDwVersionRequired,  
    LPWCPICDATAlpwcpicdata);  
```  
  
#### Parameters  
 *wVersionRequired*  
 Specifies the version of Windows CPI-C support required. The high-order byte specifies the minor version (revision) number. The low-order byte specifies the major version number.  
  
 *lpwcpicdata*  
 A pointer to the CPI-C data structure. The **CPICDATA** structure is defined as follows:  
  
```  
typedef struct {  
....WORD wVersion;  
    char szDescription[WCPICDESCRIPTION_LEN+1];  
}  CPICDATA, FAR * LPWCPICDATA;  
```  
  
 WCPIDESCRIPTION is defined to be 127 and the structure members are as follows:  
  
 wVersion  
  
 The version of Windows CPI-C supported. The high-order byte specifies the minor version (revision) number. The low-order byte specifies the major version number.  
  
 szDescription  
  
 The description string describing the CPI-C version supported.  
  
## Return Value  
 The return value specifies whether the application was registered successfully and whether the Windows CPI-C implementation can support the specified version number. If the value is zero, it was registered successfully. Otherwise, the return value is one of the following:  
  
 WCPICSYSNOTRERADY  
 The underlying network system is not ready for network communication.  
  
 WCPICVERNOTSUPPORTED  
 The version of Windows CPI-C support requested is not provided by this particular Windows CPI-C implementation.  
  
 WCPICINVALID  
 The Windows CPI-C version specified by the application is not supported by this dynamic-link library (DLL).  
  
## Remarks  
 To support future Windows CPI-C implementations and applications that may have functionality differences from Windows CPI-C version 1.0, a negotiation takes place in **WinCPICStartup**. An application passes to **WinCPICStartup** the Windows CPI-C version that it can use. If this version is lower than the lowest version supported by the Windows CPI-C DLL, the DLL cannot support the application and the **WinCPICStartup** call fails. If the version is not lower, however, the call succeeds and returns the highest version of Windows CPI-C supported by the DLL. If this version is lower than the lowest version supported by the application, the application either fails its initialization or attempts to find another Windows CPI-C DLL on the system.  
  
 This negotiation allows both a Windows CPI-C DLL and a Windows CPI-C application to support a range of Windows CPI-C versions. An application can successfully use a DLL if there is any overlap in the versions. The following table illustrates how **WinCPICStartup** works in conjunction with different application and DLL versions.  
  
|Application versions|DLL versions|To WinCPICStartup|From WinCPICStartup|Result|  
|--------------------------|------------------|-----------------------|-------------------------|------------|  
|1.0|1.0|1.0|1.0|Use 1.0|  
|1.0, 2.0|1.0|2.0|1.0|Use 1.0|  
|1.0|1.0, 2.0|1.0|2.0|Use 1.0|  
|1.0|2.0, 3.0|1.0|WCPICINVALID|Fail|  
|2.0, 3.0|1.0|3.0|1.0|App Fails|  
|1.0, 2.0, 3.0|1.0, 2.0, 3.0|3.0|3.0|Use 3.0|  
  
 Details of the actual Windows CPI-C implementation are described in the **WHLLDATA** structure defined as follows:  
  
```  
typedef struct tagWCPICDATA { WORD wVersion;  
            char szDescription[WHLLDESCRIPTION_LEN+1];  
            } WCPICDATA, FAR *LPWCPICDATA;  
```  
  
 Having made its last Windows CPI-C call, an application should call the [WinCPICCleanup](../core/wincpiccleanup2.md)routine.  
  
 Each Windows CPI-C implementation must make a **WinCPICStartup** call before issuing any other Windows CPI-C calls.
