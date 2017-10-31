---
title: "IcomLUO.Receive Method2 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 411053e8-207b-43b0-a9d4-cc8a0abee8fc
caps.latest.revision: 4
---
# IcomLUO.Receive Method
Receives outbound data on a LU0 session.  
  
## Syntax  
  
```  
  
void Receive(  
   int timeout,  
   ref int datasize,  
   out int indication,  
   out short seqno,  
   ref System.Array data  
)  
```  
  
#### Parameters  
  
|Value|Description|  
|-----------|-----------------|  
|`timeout`|The period of time in milliseconds that the thread can wait for data to arrive.<br /><br /> By setting `dataSize`, you can indicate if the application is willing to accept partial data after a timeout.<br /><br /> Entering 0xffffffff into `howLong` indicates an infinite length of time.|  
|`datasize`|The maximum amount of data that the application is willing to accept.<br /><br /> If `dataSize` bytes of data are received before the timeout is compete, Receive will return the partial chain.<br /><br /> When this method returns, contains the number of bytes present in the data buffer.|  
|`indication`|One or more flags in a bitwise OR containing additional information about the outbound datastream. For more information, see the Remarks section.|  
|`seqno`|When this method returns, contains the SNA sequence number of the chain.<br /><br /> If NEG_RESPONSE is set in `indication`, `seqno` may instead contain the sequence number of the chain to which the host sent a response.<br /><br /> The value returned in `seqno` may be used in IcomLU0.SendResponse to transmit a SNA response.|  
|`data`|An array containing the data to receive.|  
  
## Return Value  
  
|Value|Description|  
|-----------|-----------------|  
|S_OK|A complete, or else the remainder of a partial, chain of data was received into the data buffer.|  
|CLU0_S_PARTIAL_CHAIN|A partial chain of data was received into the data buffer.|  
|CLU0_S_TIMEOUT|No data was received within the timeout specified.<br /><br /> You should issue another Receive.|  
|CLU0_E_SESSIONFAILURE|The LU0 session failed.|  
|CLU0_E_SERVER_FAILURE|The TSS session is no longer valid.<br /><br /> The application should release the session handle.|  
|CLU0_E_WAITING|Another thread has issued a Receive call for this method, and has not yet returned.|  
|CLU0_E_SESSION_FAILED|The underlying SNA session failed, possibly due to a link outage or other transient failure.<br /><br /> You must either disconnect and release the server session. Alternately, you may call IcomLU0.Offline to reset the session, and then call IcomLU0.Online to reactive the session.|  
|CLU0_E_NOTCONNECTED|The comLU0 client is not connected to a session through a call to Icom3270.Connect.|  
|CLU0_E_BADPARAM|One of the parameters contained an invalid value.|  
|CLU0_E_SYSERROR|The method failed due to an internal error.|  
  
## Exceptions  
  
## Remarks  
 Normally, Receive blocks until a complete chain of SNA data is available. However, the application can control the block through `howLong`, `maxData`, and `incompleteData`.  
  
 Receive returns only application-level data. Specifically, Receive will not return the SNA TH and RH headers.  
  
 The following table describes the possible values for `indication`.  
  
|Value|Description|  
|-----------|-----------------|  
|SESSION_STARTED|One of the following:<br /><br /> -   The SSCP-initiated session has been activated.<br />-   A session that was reset by a CLEAR has been restarted by an SDT.<br />-   A session that previously received an UNBIUND has been reactivated by a BIND and SDT.|  
|BEGIN_BRACKET|The host started a new bracket.|  
|END_BRACKET|The host terminated the current bracket.|  
|SEND|The host has given permission to send.|  
|DATA_COMPLETE|The data represents a complete data chain or the end of a data chain.|  
|DATA_INCOMPLETE|The data represents an incomplete data chain.|  
|CANCEL|The last chain from the host was canceled.|  
|NO_RESPONSE|The application should not send a response to the data.|  
|EXCEPTION_RESPONSE1/2|The application may send a negative response to reject the data, or a courtesy acknowledgement.|  
|DEFINITE_RESPONSE1/2|The application must send a response to the data.|  
|POS_RESPONSE|The host sent a positive response.|  
|NEG_RESPONSE|The host sent a negative response.|  
|EXR_REQUEST|The SNA server converted the host request into an exception request.|  
|CHASE|The host requests that all outstanding responses be sent.|  
|NORMAL_DATA|The data was received on the normal data flow.|  
|EXPEDITED_DATA|The data was received on the expedited data flow.|  
|APPL_DATA|The data is application (FMD) data.|  
|FM_DATA|The data is Function Management (FMH) data.|  
|LU_DATA|The data was received on the LU session.|  
|SSCP_DATA|The data was received on the SSCP session.|  
|CLEAR|The host has cleared the session.|  
|QUIESCE|The host has quiesced the session.|  
|SHUTDOWN|The host is shutting down the session.|  
|RELEASE|The host canceled the quiesce or shutdown state.|  
|UNBIND|The host unbound the LU-LU session.|  
  
## See Also  
 [IcomLU0 Methods](../core/icomlu0-methods.md)   
 [Session Integrator for LU0](../Topic/Session%20Integrator%20for%20LU01.md)