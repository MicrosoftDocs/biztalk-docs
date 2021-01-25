---
description: "Learn more about: IcomLUO.SendResponse Method"
title: "IcomLUO.SendResponse Method1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4550f2ba-c5c6-4457-af6f-bdeedebf0a82
caps.latest.revision: 4
author: "gplarsen"
ms.author: "hisdocs"
manager: "anneta"
---
# IcomLUO.SendResponse Method
Sends a response or courtesy acknowledgement to the host.  
  
## Syntax  
  
```  
  
void SendResponse(  
   int senseCode,  
   int hint,  
   short seqno  
)  
```  
  
#### Parameters  
  
|Parameter|Description|  
|---------------|-----------------|  
|`senseCode`|The sense code to send to the host, in Intel byte order.<br /><br /> 0x00000000 indicates a positive response or a courtesy acknowledgement to exception response data.|  
|`hint`|A hint to indicate the message flow on which the response is to be sent.<br /><br /> Hint should be a bitwise combination of LU_DATA or SSCP_DATA and NORMAL_DATA or EXPEDITED_DATA.|  
|`seqno`|The sequence number of the request to respond to.<br /><br /> The value used in `seqno` is returned by IcomLU0.Receive.|  
  
## Return Value  
  
|Value|Description|  
|-----------|-----------------|  
|S_OK|The method sent the message successfully.|  
|CLU0_E_SESSION_FAILED|The underlying SNA session failed, possibly due to a link outage or other transient failure.<br /><br /> You must disconnect and release the server session. Optionally, you may issue a call to IcomLU0.Offline to reset the session, and then reactivate the session with a call to IcomLU0.Online.|  
|CLU0_E_RECEIVE_IN_PROGRESS|The application has not completed receiving the last chain sent by the host. This may be indicated by Receive returning DATA_INCOMPLETE.<br /><br /> The you should re-issue the IcomLU0.Receive call to collect the remaining data and then retry the call to SendResponse.|  
|CLU0_E_SERVER_FAILURE|The TSS session is no longer valid.<br /><br /> You should release the session handle.|  
|CLU0_E_WAITING|Another thread has issued a Receive call for this comLU0 method which has not yet returned.|  
|CLU0_E_NOTCONNECTED|The comLU0 client is not connected to a session object through a call to Connect.|  
|CLU0_E_SYSERROR|This method failed due to an internal error.|  
  
## Exceptions  
  
## Remarks  
  
## See Also  
 [IcomLU0 Methods](../core/icomlu0-methods1.md)   
 [Session Integrator for LU0](./session-integrator-for-lu02.md)
