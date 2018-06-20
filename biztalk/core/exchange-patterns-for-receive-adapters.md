---
title: "Exchange Patterns for Receive Adapters | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e505559e-66be-4c32-a2a8-a242cba10000
caps.latest.revision: 21
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Exchange Patterns for Receive Adapters
Receive adapters receive data from the "wire" and submit it as a message into [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. This submittal process can be a one-way or a two-way message exchange pattern.  
  
## One-Way Submit  
 For a receive adapter to submit a message into the BizTalk Messaging Engine, it first needs to create a new BizTalk message. The code sample in the IBaseMessage topic shows how this is done. The stream that the adapter sets as the message body should typically be a forward-only stream, meaning that it should not cache the data that it has previously read into memory.  
  
 Before the adapter submits the message into the engine, it must write the **InboundTransportLocation** message context property in the system namespace onto the BizTalk message. This is illustrated in the following code fragment:  
  
 `Assembly References:`  
  
 `Microsoft.XLANGs.BaseTypes.dll`  
  
 `Microsoft.BizTalk.Pipeline.dll`  
  
 `Microsoft.BizTalk.GlobalPropertySchemas.dll`  
  
```  
using Microsoft.BizTalk.Message.Interop;  
using Microsoft.XLANGs.BaseTypes;  
  
private static readonly PropertyBase InboundTransportLocationProp =   
new BTS.InboundTransportLocation();  
  
private void StampMsgCtxProps(  
IBaseMessage msg, string uri, string adapterType)  
{  
msg.Context.Write(  
 InboundTransportLocationProp.Name.Name,   
 InboundTransportLocationProperty.Name.Namespace,   
  uri);  
}  
```  
  
 In addition, the adapter may define its own property schemas and write message context properties pertaining to the endpoint over which it received the message. For example, an HTTP adapter might write the HTTP headers to the message context, and an SMTP receiver might write the subject of the mail to the message context. This information may be useful to downstream components such as pipeline components, orchestration schedules, or a send adapter.  
  
 After the messages are prepared, they can be submitted into the Messaging Engine. To see how a one-way receive adapter might submit a message into the engine, see the code sample [SubmitDirect (BizTalk Server Sample)](../core/submitdirect-biztalk-server-sample.md).  
  
## Request-Response  
 Two-way receive adapters are typically used on one-way or two-way receive ports. The adapter determines whether the receive location it is servicing is a one-way or two-way port by inspecting the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] configuration property bag. This process is explained in the **IBTTransportConfig.AddReceiveEndpoint Method (COM)** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].  
  
 The following object interaction diagram illustrates the process of performing a request-response message exchange. The adapter requests a new batch from the transport proxy and passes in its reference to the **IBTTransmitter** interface through the **SubmitRequestMessage** method. The Messaging Engine delivers the response message on this interface by using the **TransmitMessage** method.  
  
 Because the engine is processing messages asynchronously, it is possible for the following to happen:  
  
- The **BatchComplete** callback might occur before **Done** has returned.  
  
- The call to TransmitMessage might be made before BatchComplete and even before Done.  
  
  While both of these scenarios are rare, the adapter should protect itself against this.  
  
  It is recommended that the response message is transmitted using an asynchronous non-blocking call.  
  
  The BaseAdapter project has a utility class, **StandardRequestResponseHandler**, that encapsulates the request-response semantics explained in this topic.  
  
## Request-Response Message Time-Outs  
 When an adapter submits a request-request message, it needs to specify the time-out of the request message on the **IBTTransportBatch.SubmitRequestMessage Method (COM)** API [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]. A response message will be delivered to the adapter only within this time-out period. After the time-out expires, a negative acknowledgment (NACK) will be delivered to the adapter instead of the response message. If the adapter does not specify a time-out value, the engine uses the default value of 20 minutes.  
  
 The default time-out for request-response messages may be controlled by using the following registry key for in-process receive adapters:  
  
 **DWORD**  
  
 **HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\BTSSvc{Host Guid}\MessagingReqRespTTL**  
  
 The registry key is in a different location for isolated receive adapters:  
  
 **DWORD**  
  
 **HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\BTSSvc.3.0\MessagingReqRespTTL**  
  
 NACKs (Negative ACKnowledgements) are SOAP faults and there are two ways to handle them. Typically the adapter returns the NACK to the client and the client handles the NACK. Alternatively the transmit pipeline handling the response message may be configured to change the contents of the response message, by using either a map or a custom pipeline component.