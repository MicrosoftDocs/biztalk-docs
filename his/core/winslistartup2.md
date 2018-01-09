---
title: "WinSLIStartup2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a02e82a1-482b-4157-b721-379017e9802d
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# WinSLIStartup
The **WinSLIStartup** function allows an application using the Session Level Interface (SLI) verbs to specify the version of Microsoft Windows logical unit application (LUA) required and to retrieve details of the specific Windows LUA implementation. This function must be called by an application to register itself with a Windows LUA implementation before issuing any further Windows LUA calls.  
  
## Syntax  
  
```  
  
int WINAPI WinSLIStartup(   
WORD wVersionRequired,   
LUADATA FAR *lpLuaData  
);  
```  
  
#### Parameters  
 *wVersionRequired*  
 Specifies the version of Windows LUA support required. The high-order byte specifies the minor version (revision) number. The low-order byte specifies the major version number.  
  
 *lpLuaData*  
 Pointer to the **LUADATA** structure containing the returned version number information.  
  
## Return Value  
 The return code specifies whether the application was registered successfully and whether the Windows LUA implementation can support the specified version number. If the value is zero, it was registered successfully and the specified version can be supported. Otherwise, the return code is one of the following:  
  
 WLUASYSNOTREADY  
 The underlying network system is not ready for network communication.  
  
 WLUAVERNOTSUPPORTED  
 The version of Windows LUA support requested is not provided by this particular Windows LUA implementation.  
  
 WLUAINVALID  
 The Windows LUA version specified by the application is not supported by this dynamic-link library (DLL).  
  
 WLUAFAILURE  
 A failure occurred while the Windows LUA DLL was initializing. This usually occurs because an operating system call failed.  
  
 WLUAINITREJECT  
 **WinSLIStartup** was called multiple times.  
  
## Remarks  
 To support future Windows LUA implementations and applications that may have functionality differences, a negotiation takes place in **WinSLIStartup**. An application passes to **WinSLIStartup** the Windows LUA version that it can use. If this version is lower than the lowest version supported by the Windows LUA DLL, the DLL cannot support the application and **WinSLIStartup** fails. If the version is not lower, however, the call succeeds and returns the highest version of Windows LUA supported by the DLL. If this version is lower than the lowest version supported by the application, the application either fails its initialization or attempts to find another Windows LUA DLL on the system.  
  
 This negotiation allows both a Windows LUA DLL and a Windows LUA application to support a range of Windows LUA versions. An application can successfully use a DLL if there is any overlap in the versions. The following table illustrates how **WinSLIStartup** works in conjunction with different application and DLL versions.  
  
|App versions|LUA DLL versions|To<br /><br /> WinSLIStartup|From<br /><br /> WinSLIStartup|Result|  
|------------------|----------------------|--------------------------|----------------------------|------------|  
|1.0|1.0|1.0|1.0|Use 1.0|  
|1.0, 2.0|1.0|2.0|1.0|Use 1.0|  
|1.0|1.0, 2.0|1.0|2.0|Use 1.0|  
|1.0|2.0, 3.0|1.0|WLUAINVALID|Fail|  
|2.0, 3.0|1.0|3.0|1.0|App fails|  
|1.0, 2.0, 3.0|1.0, 2.0, 3.0|3.0|3.0|Use 3.0|  
  
> [!NOTE]
>  The application that uses SLI verbs must call **WinSLIStartup** prior to issuing any other LUA commands. However, **WinSLIStartup** needs to be called only once per application. If it is called multiple times, the subsequent calls will be rejected.  
  
 Details of the actual LUA implementation are described in the **WLUADATA** structure, defined as follows:  
  
```  
typedef struct { WORD wVersion;  
            char szDescription[WLUADESCRIPTION_LEN+1];  
            } LUADATA;  
```  
  
 Having made its last Windows LUA call, an application should call the **WinSLICleanup** routine.  
  
 Each LUA application that uses SLI verbs must make a **WinSLIStartup** call before issuing any other LUA calls.  
  
## See Also  
 [WinSLICleanup](../core/winslicleanup2.md)