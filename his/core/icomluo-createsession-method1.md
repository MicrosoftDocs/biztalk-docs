---
title: "IcomLUO.CreateSession Method1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d7c54b28-840b-464a-b0d4-6516995c2b02
caps.latest.revision: 4
---
# IcomLUO.CreateSession Method
Creates a new LU0 session.  
  
## Syntax  
  
```  
  
void CreateSession(  
   string connectionSTR,  
   short initType,  
   ref System.Array data,  
   int timeout,  
   out object sessionHandle  
)  
```  
  
#### Parameters  
  
|Parameter|Description|  
|---------------|-----------------|  
|`connectionSTR`|NULL-terminated string that indicates the connection properties of the new session. The string is presented in a "PROPERTY=VALUE", space-delineated format. Connection property names and values are case insensitive. For more information about connection properties, see IcomLUO Session Properties.|  
|`initType`|Contains the session initialization type. For more information, see the Comments section.|  
|`data`|Pointer an array of type unsigned char that contains the INITSELF or SSCP logon message. Used only if `initType` contains INIT_INITSELF or INIT_LOGON.|  
|`timeout`|The period of time in milliseconds to wait for the BIND and SDT commands to arrive. If the timeout expires before the SDT arrives the SNA server LU will be released and an error returned.<br /><br /> Entering `0xfffffff` into `timeout` indicates an infinite wait time.|  
|`sessionHandle`|When this method successfully returns, contains a pointer to the IUnknown interface to the comLU0 session object representing the underlying LU0 session. As along as a reference is kept to this interface, the session object will remain intact.<br /><br /> This interface may be passed to the IcomLU0.Connect method to connect to the comLU0 object with the session.<br /><br /> If no LU property is specified, comLU0 will select the best available LU assigned to the user account under which it is running.|  
  
## Return Value  
 The following table describes the return codes for CreateSession.  
  
|Value|Description|  
|-----------|-----------------|  
|S_OK|The LU0 session was successfully created. The LU session is active and ready to receive input.|  
|CLU0_S_SSCP_ACTIVE|The LU0 session was successfully created. The SSCP session is active and ready to receive input.<br /><br /> This return code is valid only when `initType` is set to `INIT_SSCP`.|  
|CLU0_E_NEG_RESPONSE|The host or SNA server sent a negative response to the INITSELF.<br /><br /> Optionally, the host or SNA server may have sent an unformatted logon command. This is true only if `initType` is set to `INIT_INITSELF` or `INIT_LOGON`.|  
|CLU0_E_BADPARM|`connectionStr` contained an invalid property setting.|  
|CLU0_E_NOFREELU|The LU specified in `luname` is an SNA server LU pool. The pool does not currently have any free LUs.|  
|CLU0_E_LUINUSE|The LU specified in `luname` is an SNA server LU. This LU is currently being used by another application.|  
|CLU0_E_LUNOTFOUND|The LU or pool name does not exist.|  
|CLU0_E_TIMEDOUT|The session was not started within the specified timeout.|  
|CLU0_E_SESSION_FAILED|The session failed to activate and is not connected to any TSS LU0 session.<br /><br /> The application should attempt to create a new session using the same or different connection properties, or else connect to a different TSS session handle.|  
|CLU0_E_ACCESSDENIED|The user account for the client does not have permission to use the requested LU or pool.|  
|CLU0_E_ALREADY_CONNECTED|The comLU0 client is already connected to another session.|  
|CLU0_E_SYSERROR|Failed due to an internal error.|  
  
## Remarks  
 The following table contains the possible values for `initType`.  
  
|Name|Value|Description|  
|----------|-----------|-----------------|  
|INIT_BIND|0|Wait for an unsolicited BIND and SDT from the PLU.|  
|INIT_SSCP|1|Wait for a BIND and SDT to arrive but allow access to the SSCP session for the application to send SSCP data and commands.|  
|INIT_INITSELF|2|Wait for a BIND and SDT to arrive after sending the INITSELF command specified in `data`.|  
|INIT_LOGON|3|Wait for a BIND and SDT to arrive after sending the UNFORMATTED SSCP logon message specified in `data`.|  
  
## See Also  
 [IcomLU0 Methods](../core/icomlu0-methods2.md)   
 [Session Integrator for LU0](../core/session-integrator-for-lu01.md)