---
title: "About Session Management2 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b3ecdb4f-d384-42ac-9776-e7ad14d5f151
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# About Session Management
The Microsoft BizTalk Adapter for JD Edwards EnterpriseOne creates a connection session to send a call to the JD Edwards EnterpriseOne server. When the call terminates, the session is put in a pool to be re-used by a subsequent call. The adapter creates multiple connection sessions to handle concurrent calls to the JD Edwards EnterpriseOne server. The pool is periodically cleaned to remove sessions that are no longer necessary.  
  
 The Microsoft BizTalk Adapter JD Edwards EnterpriseOne provides two message context properties to control when calls must occur within the same session.  
  
|Name|Type|Default|  
|----------|----------|-------------|  
|JDE.SessionID|Int|0|  
|JDE.ReserveSession|boolean|false|  
  
 Session management is unnecessary if the business function requires a single call to the JD Edwards EnterpriseOne server. The adapter can pick any available session and the session remains available for any following calls. In this scenario, you can ignore the message context properties as the defaults are appropriate.  
  
 Some JD Edwards EnterpriseOne functionality requires multiple calls to the JD Edwards EnterpriseOne server; for example, the creation of a SalesOrder. The first call to BeginDoc creates an empty SalesOrder. Each subsequent call to EditLine adds one line item to the SalesOrder. Finally the call to EndDoc closes the SalesOrder.  
  
```  
BeginDoc  
   EditLine  
   EditLine  
   ...  
EndDoc  
```  
  
 To be successful, all the calls for a single SalesOrder must be sent on the same session. To do this, assign message context properties to instruct the adapter what to do with the session. For the SalesOrder example, these are the values that would be assigned to the message context properties to handle the JD Edwards EnterpriseOne session:  
  
|Function|SessionID|ReserveSession|  
|--------------|---------------|--------------------|  
|BeginDoc|0|true|  
|EditLine|Copied from BeginDoc reply|true|  
|EditLine|Copied from BeginDoc reply|true|  
|EndDoc|Copied from  BeginDoc reply|false|  
  
- For the first call, the adapter is free to choose any available session (because the SessionID is zero).  
  
- The adapter returns the SessionID that was used in the BeginDoc reply.  
  
- The ReserveSession property tells the adapter to reserve this session for following calls that explicitly requests this session. No other calls can accidentally re-use the session because it is reserved.  
  
- Subsequent calls request the session by setting the SessionID to the value returned in BeginDoc.  
  
- The ReserveSession property is set to true, at least until the last call in the series.  
  
- The last call sets ReserveSession to false to make the session available to any following call. However, the orchestration can elect to keep the session for more calls.  
  
  If the session is not used for a while, it will be garbage-collected by the pool, even if the session is still reserved by mistake.  
  
  Refer to BizTalk Server documentation for more details on message context properties.  
  
## See Also  
 [Using Message Context Properties](../core/using-message-context-properties1.md)