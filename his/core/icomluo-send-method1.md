---
description: "Learn more about: IcomLUO.Send Method"
title: "IcomLUO.Send Method1"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# IcomLUO.Send Method
Sends a complete inbound chain of data on an LU0 session.  
  
## Syntax  
  
```  
  
void Send(  
   int hint,  
   ref System.Array data,  
    out short seqno)  
  
```  
  
#### Parameters  
  
|Parameter|Description|  
|---------------|-----------------|  
|`hint`|A hint from the application regarding how the data is to be processed. For more information, see the remarks section.|  
|`data`|The data to send.|  
|`seqno`|When this method returns, contains the SNA sequence number of the chain.<br /><br /> You can use the value returned by `seqno` to correlate any response the host may send later.|  
  
## Return Value  
  
|Value|Description|  
|-----------|-----------------|  
|S_OK|The data was sent successfully. If relevant, positive response was also received.|  
|CLU0_S_MULTI_CHIIN|The session does not support multi-RU chains, but the data was larger than the RU size. comLU0 sent the data as a sequence of single RU chains.|  
|CLU0_S_DEFINITE_RSP_MODE|comLU0 sent the data using DEFINITE_RESPONSE mode when EXCEPTION_RESPONSE or NO_RESPONSE was requested.|  
|CLU0_S_EXCEPTION_RSP_MODE|comLU0 send the data using EXCEPTION_RESPONSE mode when DEFINITE_RESPONSE or NO_RESPONSE was requested.|  
|CLU0_S_NO_RSP_MODE|comLU0 sent the data using NO_RESPONSE mode when DEFINITE_RESPONSE or EXCEPTION_RESPONSE was requested.|  
|CLU0_E_NEG_RESPONSE|The host or SNA server sent a negative response to the DEFINITE_RESPONSE.|  
|CLU0_E_NO_RSP_REQUESTED|No response was received from the host to a RQD request.<br /><br /> You should call IcomLU0.Receive to determine the reason that he response was not received. For example, a CLEAR may have been received, or the session experienced an outage.|  
|CLU0_E_BRACKED_NOT_ALLOWED|The session was between brackets but comLU0 was not allowed to start a new bracket. This occurred due to comLU0 receiving an SBI from the host.|  
|CLU0_E_SESSION_FAILED|The underlying SNA session failed, possibly do to a link outage or other transient failure.<br /><br /> You must disconnect and release the server session. Optionally, you may call IcomLU0.Offline to reset the session, and then call IcomLU0.Online to reactive the session.|  
|CLU0_E_RECEIVE_IN_PROGRESS|The application has not completed receiving the last chain sent by the host. This is likely indicated by Receive returning the DATA_INCOMPLETE message.<br /><br /> You should re-issue IcomLU0.Receive call to collect the remaining data and then call Send again.|  
|CLU0_E_SERVER_FAILURE|The TSS session is no longer valid.<br /><br /> You should release the session handle.|  
|CLU0_E_WAITING|Another thread has issued a Receive call for this method, which has not yet returned.|  
|CLU0_E_SESSIONFAILURE|The LU0 session failed.|  
|CLU0_E_NOTCONNECTED|The comLU0 client is not connected to a session through a call to Icom3270.Connect.|  
|CLU0_E_SYSERROR|The send failed due to a system error.|  
  
## Exceptions  
  
## Remarks  
 The SNA TH and RH are provided by comLU0 and must not be present in the data presented by the application.  
  
 The following table describes the possible values for `hint`.  
  
|Value|Description|  
|-----------|-----------------|  
|END_BRACKET|comLU0 should end the current bracket.|  
|PREPARE_TO_RECEIVE|The application is about to enter the receive state.|  
|NO_RESPONSE|The application does not need a response from the host.|  
|EXCEPTION_RESPONSE1/2|The application requires that the host send a negative response only.|  
|DEFINITIE_RESPONSE1/2|The application requires that the host send a response to the data.|  
|NORMAL_DATA|The application is sending the on the normal data flow.|  
|EXPEDITED_DATA|The application is sending the data on the expedited data flow.|  
|APPL_DATA|The data is application (FMD) data.|  
|FM_DATA|The data is Function Management (FMH) data|  
|LU_DATA|The application is sending the data on the LU session.|  
|SCP_DATA|The application is sending the data on the SSCP session.|  
  
## See Also  
 [IcomLU0 Methods](../core/icomlu0-methods1.md)   
 [Session Integrator for LU0](./session-integrator-for-lu02.md)
