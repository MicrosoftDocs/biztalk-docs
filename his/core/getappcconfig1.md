---
title: "GetAppcConfig1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d7b92ade-7ffb-4380-9720-bd1ee47b11aa
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# GetAppcConfig
The **GetAppcConfig** function provides an asynchronous entry point for retrieving the remote systems to which a particular local LU can connect.  
  
## Syntax  
  
```  
  
HANDLE WINAPI GetAppcConfig(   
HANDLE hWnd,  
LPSTR pLocalLu,  
LPSTR pMode,  
LPINT pNumRemLu,  
INT iMaxRemLu,  
PSTR pRemLu,  
LPINT pAsyncRetCode  
);  
```  
  
#### Parameters  
 *hWnd*  
 Supplied parameter. Contains the handle of the window that is to receive an asynchronous completion message when the call has completed. If non-null, the completion message will be posted to this window handle. In this case, *pAsyncRetCode* (the last parameter) must be null. Asynchronous message completion is the recommended approach for Windows applications to use this function.  
  
 *pLocalLu*  
 Supplied parameter. Specifies the address of a buffer containing the local LU name for which information is returned. This local LU name must be specified as follows:  
  
- Nonpadded  
  
- Null-terminated  
  
- ASCII string  
  
- Maximum length of eight bytes (excluding the terminator)  
  
  To request that the user's default local LU be used, the buffer should contain eight spaces followed by a null.  
  
  *pMode*  
  Supplied parameter. Specifies the address of a buffer containing the mode name for which information is returned. In Microsoft Host Integration Server, this parameter is not used, but for compatibility with earlier versions of SNA Server a mode name must be specified as follows:  
  
- Nonpadded  
  
- Null-terminated  
  
- ASCII string  
  
- Maximum length of eight bytes (excluding the terminator)  
  
  *pNumRemLu*  
  Supplied parameter. Specifies the address of an integer variable that when the function completes will contain the number of remote LUs that would have been returned, had the buffer specified by *pRemLu* been large enough to accommodate all of the remote LUs.  
  
  *iMaxRemLu*  
  Supplied parameter. Specifies the number of remote LU names that can be held by the buffer indicated by *pRemLu*.  
  
  *pRemLu*  
  Supplied parameter. Specifies the address of the buffer that will hold the remote LU names after the function completes. The information will be returned as an array of strings. Each remote LU name will be stored in the buffer as follows:  
  
- Nonpadded  
  
- Null-terminated  
  
- ASCII string  
  
- Maximum length of eight bytes (excluding the terminator)  
  
  The strings start every nine bytes in the buffer, and thus (*pRemLu* + (*i*–1)\*9) gives the start of the *i*th string. In the case where the buffer is too small to hold all the names, only *iMaxRemLu* strings will be returned.  
  
  *pAsyncRetCode*  
  Supplied parameter. Specifies the address of an integer variable used to store the return code from this function, if the supplied address is non-null. The return codes will be the same as those returned by an asynchronous completion message. While the call is completing, the value of this variable will be APPC_CFG_PENDING. When this asynchronous call is completed, the value of this variable will contain some return code other than APPC_CFG_PENDING.  
  
  This variable is used by polling for completion when asynchronous message completion to a window handle is not used.  
  
  Note that if *pAsyncRetCode* is used, *hWnd* must be null.  
  
## Return Value  
 The meaning of the immediate return value depends on whether or not the asynchronous request was accepted. To test for acceptance, evaluate the expression:  
  
 (\<*Returned Handle*> & APPC_CFG_SUCCESS)  
  
 If the expression is FALSE, the request was rejected. The return value is then one of the synchronous return codes in the following list. If the expression is TRUE, the request was accepted, and one of the following cases will apply.  
  
-   If *hWnd* was non-null, a completion message will arrive in the following form:  
  
    |Message parameter|Description|  
    |-----------------------|-----------------|  
    |*hWnd*|The handle of the target window. This value is the same as the value passed in *hWnd* on the initial call.|  
    |*uMsg*|Matches the number returned by a call to **RegisterWindowMessage**, with WinAppcCfg used as the identifying string. This string is available by the **#define WIN_APPC_CFG_COMPLETION_MSG**.|  
    |*wParam*|Matches the *HANDLE* returned from the initial call. It is used as a correlator.|  
    |*lParam*|Contains one of the asynchronous return codes in the following list.|  
  
-   If *pAsyncRetCode* was non-null, then the specified integer variable will be set to APPC_CFG_PENDING. After this function completes asynchronously, its value will change to one of the asynchronous return codes listed below.  
  
## Synchronous Return Codes  
 APPC_CFG_ERROR_NO_APPC_INIT  
 The Windows APPC library needs to be initialized by a call to [WinAPPCStartup](../core/winappcstartup1.md) before calling **GetAppcConfig** and this has not been done.  
  
 APPC_CFG_ERROR_INVALID_HWND  
 The handle passed in *hWnd* was non-null, yet not a valid window handle.  
  
 APPC_CFG_ERROR_BAD_POINTER  
 The *hWnd* parameter was null, indicating that completion was signaled by setting the integer variable pointed to by *pAsyncRetCode*, but *pAsyncRetCode* was not a valid pointer.  
  
 APPC_CFG_ERROR_UNCLEAR_COMPLETION_MODE  
 Both *hWnd* and *pAsyncCompletion* were non-null, so **GetAppcConfig** was unable to decide how completion should be signaled.  
  
 APPC_CFG_ERROR_TOO_MANY_REQUESTS  
 Too many **GetAppcConfig** calls are already being processed (currently, this indicates 16 requests are outstanding). Try the call again after a delay. For the Microsoft Windows version 3.*x* system, you must yield during this period.  
  
 APPC_CFG_ERROR_GENERAL_FAILURE  
 An unexpected error occurred, probably of a system nature.  
  
## Asynchronous Return Codes  
 APPC_CFG_SUCCESS_NO_DEFAULT_REMOTE  
 The configuration information has been retrieved, and either no default remote LU was defined or it was not accessible by the specified local LU.  
  
 APPC_CFG_SUCCESS_DEFAULT_REMOTE  
 The configuration information has been retrieved, and there is a default remote LU that is accessible by the specified local LU.  
  
 APPC_CFG_ERROR_NO_DEFAULT_LOCAL_LU  
 An attempt was made to retrieve remote LUs partnered with the default local LU, but no default local LU was configured.  
  
 APPC_CFG_ERROR_BAD_LOCAL_LU  
 The local LU specified is either not configured, or is not valid for the calling verb.  
  
 APPC_CFG_ERROR_GENERAL_FAILURE  
 An unexpected error occurred, probably of a system nature.  
  
## Remarks  
 [WinAPPCStartup](../core/winappcstartup1.md) must be called before using **GetAppcConfig**.  
  
 Whether an error code represents success or failure can be determined by evaluating either (*RetCode&* APPC_CFG_SUCCESS) to test for success or (*RetCode&* APPC_CFG_FAILURE) to test for failure.  
  
 The following code fragment shows how a console application can test completion:  
  
```  
while (*pAsyncRetCode == APPC_CFG_PENDING)  
{  
    sleep(250);  
}  
```