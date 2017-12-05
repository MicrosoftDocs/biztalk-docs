---
title: "WinRUIGetLastInitStatus1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: cc88c27a-c241-48cf-9296-d23d85015af9
caps.latest.revision: 3
---
# WinRUIGetLastInitStatus
The **WinRUIGetLastInitStatus** function enables an application to determine the status of an [RUI_INIT](../core/rui-init2.md), so that the application can evaluate whether the **RUI_INIT** should be timed out. This extension can be used to initiate status reporting, terminate status reporting, or find the current status. For details, see the Remarks section.  
  
## Syntax  
  
```  
  
          int WINAPI WinRUIGetLastInitStatus(   
DWORD dwSid,             
 HANDLE hStatusHandle,    
DWORD dwNotifyType,      
BOOL bClearPrevious    );  
```  
  
#### Parameters  
 *dwSid*  
 Specifies the RUI session identifier of the session for which status will be determined. If *dwSid* is zero, *hStatusHandle* is used to report status on all sessions. Note that the **lua_sid** parameter in the [RUI_INIT](../core/rui-init2.md) verb control block (VCB) is valid as soon as the call to [RUI](../core/rui1.md) or [WinRUI](../core/winrui2.md) for the **RUI_INIT** returns.  
  
 *hStatusHandle*  
 Specifies a handle used for signaling the application that the status for the session (specified by *dwSid*) has changed. Can be a window handle, an event handle, or NULL; *dwNotifyType* must be set accordingly:  
  
 If *hStatusHandle* is a window handle, status is sent to the application through a window message. The message is obtained from **RegisterWindowMessage** using the string "WinRUI". The parameter *wParam* contains the session status. (For more information, see Return Codes.) Depending on the value of *dwNotifyType*, *lParam* contains either the RUI session identifier of the session, or the value of **lua_correlator** from the [RUI_INIT](../core/rui-init2.md) verb.  
  
 If *hStatusHandle* is an event handle, when the status for the session specified by *dwSid* changes, the event is put into the signaled state. The application must then make a further call to **WinRUIGetLastInitStatus** to find out the new status. Note that the event should not be the same as one used for signaling completion of any RUI verb.  
  
 If *hStatusHandle* is NULL, the status of the session specified by *dwSid* is returned in the return code. In this case, *dwSid* must not be zero unless *bClearPrevious* is TRUE. If *hStatusHandle* is NULL, *dwNotifyType* is ignored.  
  
 *dwNotifyType*  
 Specifies the type of indication required. This determines the contents of the *lParam* of the window message, and how **WinRUIGetLastInitStatus** interprets *hStatusHandle*. Allowed values are:  
  
 WLUA_NTFY_EVENT  
  
 The *hStatusHandle* parameter contains an event handle.  
  
 WLUA_NTFY_MSG_CORRELATOR  
  
 The *hStatusHandle* parameter contains a window handle, and the *lParam* of the returned window message should contain the value of the **lua_correlator** field on the [RUI_INIT](../core/rui-init2.md).  
  
 WLUA_NTFY_MSG_SID  
  
 The *hStatusHandle* parameter contains a window handle, and the *lParam* of the returned window message should contain the LUA session identifier.  
  
 *bClearPrevious*  
 If TRUE, status messages are no longer sent for the session identified by *dwSid*. If *dwSid* is zero, status messages are no longer sent for any session. If *bClearPrevious* is TRUE, *hStatusHandle* and *dwNotifyType* are ignored.  
  
## Return Value  
 WLUASYSNOTREADY  
 SNABASE is not running.  
  
 WLUANTFYINVALID  
 The *dwNotifyType* parameter is invalid.  
  
 WLUAINVALIDHANDLE  
 The *hStatusHandle* parameter does not contain a valid handle.  
  
 WLUASTARTUPNOTCALLED  
 [WinRUIStartup](../core/winruistartup2.md) has not been called.  
  
 WLUALINKINACTIVE  
 The link to the host is not yet active.  
  
 WLUALINKACTIVATING  
 The link to the host is being activated.  
  
 WLUAPUINACTIVE  
 The link to the host is active, but no ACTPU has yet been received.  
  
 WLUAPUACTIVE  
 An ACTPU has been received.  
  
 WLUAPUREACTIVATED  
 The physical unit (PU) has been reactivated.  
  
 WLUALUINACTIVE  
 The link to the host is active, and an ACTPU has been received, but no ACTLU has been received.  
  
 WLUALUACTIVE  
 The LU is active.  
  
 WLUALUREACTIVATED  
 The LU has been reactivated.  
  
 WLUAUNKNOWN  
 The session is in an unknown status. (This is an internal error.)  
  
 WLUAGETLU  
 The session is waiting for an [Open(SSCP)](../core/open-sscp-1.md) response from the node.  
  
 WLUASIDINVALID  
 The security ID (SID) specified does not match any known by the RUI.  
  
 WLUASIDZERO  
 The *hStatusHandle* parameter is NULL and *bClearPrevious* is FALSE, but *dwSid* is zero.  
  
 WLUAGLOBALHANDLER  
 The *dwSid* parameter is zero, and messages from all sessions will be notified. (This is a normal return code, not an error.)  
  
## Remarks  
 This extension is intended to be used with either a window handle or an event handle to enable asynchronous notification of status changes. It can also be used alone to find the current status of a session.  
  
## With a window handle  
 There are two ways to use this extension with a window handle:  
  
```  
WinRUIGetLastInitStatus(Sid,Handle,WLUA_NTFY_MSG_CORRELATOR,FALSE);  
```  
  
 —or—  
  
```  
WinRUIGetLastInitStatus(Sid,Handle,WLUA_NTFY_MSG_SID,FALSE);  
```  
  
 With this implementation, changes in status are reported by a window message sent to the window handle specified. If WLUA_NTFY_MSG_CORRELATOR is specified, the *lParam* field in the window message contains the **lua_correlator** field for the session. If WLUA_NTFY_MSG_SID is specified, the *lParam* field in the window message contains the LUA session identifier for the session.  
  
 When the extension has been used with a window handle, use the following to cancel status reporting:  
  
```  
WinRUIGetLastInitStatus(Sid,NULL,0,TRUE);  
```  
  
 For this implementation, note that if *Sid* is nonzero, status is only reported for that session. If *Sid* is zero, status is reported for all sessions.  
  
## With an event handle  
 To use this extension with an event handle, implement it as follows:  
  
```  
WinRUIGetLastInitStatus(Sid,Handle,WLUA_NOTIFY_EVENT,FALSE);  
```  
  
 The event whose handle is given will be signaled when a change in state occurs. Because no information is returned when an event is signaled, a further call must be issued to find out the status.  
  
```  
Status = WinRUIGetLastInitStatus(Sid,NULL,0,0,FALSE);  
```  
  
 Note that in this case, a *Sid* must be specified.  
  
 When the extension has been used with an event handle, use the following to cancel the reporting of status:  
  
```  
WinRUIGetLastInitStatus(Sid,NULL,0,TRUE);  
```  
  
## Query current status  
 To use this extension to query the current status of a session, it is not necessary to use an event or window handle. Instead, use the following:  
  
```  
Status = WinRUIGetLastInitStatus(Sid,NULL,0,0,FALSE);  
```  
  
## See Also  
 [RUI](../core/rui1.md)   
 [RUI_INIT](../core/rui-init2.md)   
 [WinRUI](../core/winrui2.md)   
 [WinRUIStartup](../core/winruistartup2.md)