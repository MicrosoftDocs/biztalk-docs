---
title: "IcomLUO.Connect Method1 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c5026753-5147-40ae-9eb8-46a1f025c0dd
caps.latest.revision: 5
author: MandiOhlinger
manager: anneta
---
# IcomLUO.Connect Method
Connects a comLU0 client to an existing session.  
  
## Syntax  
  
```  
  
Void Connect(  
   object sessionHandle  
)  
```  
  
#### Parameters  
  
|Parameter|Description|  
|---------------|-----------------|  
|`sessionHandle`|Pointer to an IUnknown that contains the session handle of the session to connect to.|  
  
## Return Value  
  
|Value|Description|  
|-----------|-----------------|  
|S_OK|The method has completed successfully.|  
|CLU0_S_SSCP_ACTIVE|The comLU0 session is connected to an SSCP initiated session whose LU-LU session is not yet active.<br /><br /> You should send the appropriate messages to the SSCP to solicit activation of the session.|  
|CLU0_S_OFFLINE|The comLU0 session is connected to an SNA session that is currently offline. You should call IcomLU0.Online to activate the session.|  
|CLU0_E_SESSION_FAILED|The underlying SNA session failed.<br /><br /> You must disconnect and release the server session.|  
|CLU0_E_ALREADY_CONNECTED|Another comLU0 client is connected to this session.|  
|CLU0_E_SYSERROR|Connect failed due to an internal systems error.|  
|E_NOINTERFACE|The session handle is not a valid IUnknown interface pointer.|  
  
## Exceptions  
  
## Remarks  
 Once you connect successfully to a session, you are responsible for calling IcomLU0.Receive to provide processing time for outbound data.  
  
 You are guaranteed exclusive access to the session until you call IcomLU0.Disconnect.