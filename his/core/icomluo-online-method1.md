---
title: "IcomLUO.Online Method1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e9bba741-8348-43c8-a7fc-283ede8bfc4d
caps.latest.revision: 4
---
# IcomLUO.Online Method
Sets the LU0 session back in an on-line state after a call to Offline.  
  
## Syntax  
  
```  
  
void Online(  
   short initType,  
   ref System.Array data,  
   int timeout)  
  
```  
  
#### Parameters  
  
|Parameter|Description|  
|---------------|-----------------|  
|`initType`|Describes the session initiation type. For more information, see the Remarks section.|  
|`data`|Contains the INITSELF or SSCP logon message, if necessary.|  
|`timeout`|The period of time in milliseconds to wait for the BIND and SDT to arrive. If the timeout expires before the SDT arrives, the SNA server LU will be released and an error returned.<br /><br /> 0xffffffff indicates an infinite timeout.|  
  
## Return Value  
  
|Value|Description|  
|-----------|-----------------|  
|S_OK|The LU0 session was successfully reactivated and the LU session is active and ready to receive input.|  
|CLU0_S_SSCP_ACTIVE|The LU0 session was successfully reactivated and the SSCP session is active and ready to receive input.<br /><br /> Valid only when `initType` is set to INIT_SSCP.|  
|CLU0_E_NEG_RESPONSE|The host or SNA server sent a negative response to the INITSELF or unformatted logon command.<br /><br /> Valid only if `initType` is set to INIT_INITSELF or INIT_LOGON|  
|CLU0_E_BADPARAM|`connectionStr` contained an invalid property setting.|  
|CLU0_E_NOFREELU|`luname` specified an SNA server LU pool, and no LUs are free in that pool.|  
|CLU0_E_LUINUSE|`luname` specified an SNA server LU, and the LU is currently in use by another application.|  
|CLU0_E_LUNOTFOUND|The LU or pool name does not exist.|  
|CLU0_E_TIMEDOUT|The session was not started within the timeout specified.|  
|CLU0_E_SESSION_FAILED|The underlying SNA session failed, possibly due to a link outage or other transient failure.<br /><br /> You must disconnect and release the server session. Optionally, you may issue a call to Icom3270.Offline to reset the server, and then reactivate the session using a call to Icom3270.Online.|  
|CLU0_E_SERVER_FAILURE|The TSS session is no longer valid.<br /><br /> You should release the session handle.|  
|CLU_E_WAITING|Another thread has issued a Receive call for this method, which has not yet returned.|  
|CLU_E_SYSERROR|This method failed due to an internal error.|  
  
## Exceptions  
  
## Remarks  
 Online will attempt to acquire the same SNA server LU, and therefore the same SNA server, used when the session was last on-line.  
  
 The following table describes the possible values for `initType`.  
  
|Name|Value|Description|  
|----------|-----------|-----------------|  
|INIT_BIND|0|Wait for unsolicited BIND and SDT from the PLU.|  
|INIT_SSCP|1|Wait for a BIND and SDT to arrive but allow access to the SSCP session for the application to send SSCP data and commands.|  
|INIT_INITSELF|2|Wait for a BIND and SDT to arrive after sending the INITSELF command specified in `data`.|  
|INIT_LOGON|3|Wait for a BIND and SDT to arrive after sending the UNFORMATTED SSCP logon message specified in `data`.|  
  
## See Also  
 [IcomLU0 Methods](../core/icomlu0-methods2.md)   
 [Session Integrator for LU0](../core/session-integrator-for-lu01.md)