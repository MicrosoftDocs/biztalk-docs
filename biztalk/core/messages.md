---
title: "Messages | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "messages, headers"
  - "messages, acknowledgements"
  - "messages, persisting"
  - "messages"
  - "examples, message headers"
  - "properties"
  - "message headers"
  - "EMS messages"
ms.assetid: 65bb3431-7186-4d4c-b004-932cdf070e73
caps.latest.revision: 11
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Messages
An Enterprise Message Service (EMS) message, like a JMS message, contains three separate parts: header, properties, and body. The header is the only required part of an EMS message. This topic describes how messages are treated in Microsoft BizTalk Adapter for TIBCO Enterprise Message Service.  
  
> [!NOTE]
>  To set or retrieve a header field (for example, set the Message Priority or Correlation ID) or a message property from the orchestration, you must add a reference to the **Microsoft.BizTalk.Adapters.TIBCOEMSProperties.dll** in your project using Solution Explorer.  
  
## Message Header  
 The message header contains a series of predefined fields that contain values. BizTalk Adapter for TIBCO Enterprise Message Service knows what it can and cannot set in the header. If you try to set a read-only value, the adapter redirects or sets your value in the Properties{} section.  
  
### Header Example  
 In the following example, notice that **Properties= { Destination={String:Queue[Q2]} }**. `Properties` is a property that contains a string, and the contents of the string is **Q2**. This has nothing to do with the Destination section; it contains strings of values that you set that could not go anywhere else, so the adapter has held them here in this section.  
  
 The `ReplyTo` property can be set in the orchestration to tell an eventual consumer where to send a response. EMS sets the `Destination` property when the message is received from TIBCOEMS. This second property is read-only in the orchestration receiving the message from TIBCOEMS and cannot be edited in the orchestration.  
  
 For example, an orchestration cannot dispatch messages and set the destination dynamically inside an orchestration. The value of Destination is set by the port to which the message is being transmitted.  
  
 If you want to dispatch messages to different queues, you must create send ports for each queue. The orchestration can then decide which port to assign the message.  
  
 In the following message example, the Destination= `{Queue[Q1]}` is read-only. This value is set by TIBCOEMS when the server receives the message. The value for Destination, Q1, comes from the Transport Properties.  
  
#### Example  
  
```  
TextMessage={   
    Header={ MessageID={ID:EMS-SERVER.824437A58B11C75F4:1}   
    Destination={Queue[Q1]}   
  
        ' This is READONLY. It gets set by the server when the  
        ' message is received by the server (EMS). It is set in the  
        ' Transport Properties when you specify that you want to  
        ' listen for messages on Q1.  
    ReplyTo={}   
    DeliveryMode={Persistent}   
    Redelivered={False}   
    CorrelationID={}   
    MsgType={}   
    Timestamp={12/1/2005 11:59:01 PM}   
    Expiration={0}   
    Priority={1} }   
    Properties={ Destination={String:Queue[Q2]} }   
  
        ' This is a property that contains a string, and the   
        ' contents of the string is Q2. This has nothing to do with  
        ' the Destination section above – it is just another   
        ' property that is set.   
        ' This is in the schema. The adapter knows what it can and   
        ' cannot set in an EMS header. The values that the adapter   
        ' cannot set are put in the Properties section.   
    text={<?xml version="1.0" encoding="utf-16"?>  
    <ns0:Employees xmlns:ns0="http://BizTalk_Server_Project1.Employee">  
        <Emp Id="Id_0">  
            Name>Name_0</Name>  
        </Emp>  
    </ns0:Employees>  
    }  
```  
  
 The header contains a series of predefined fields that contain values, which the adapter promotes to the BizTalk Server message context for use in the orchestration. The promoted properties are identical in definition to the standard header properties as defined by the JMS specification and the TIBCO Enterprise Message Service extensions. All properties except for two are available to the orchestration as received from EMS: `Destination` and `ReplyTo` describe a destination that cannot be correctly mapped for use in an orchestration as a single property.  
  
 BizTalk Adapter for TIBCO EMS maps the TIBCOEMS property to a string type and uses the Destination string representation. This looks like `StaticQueue[queuename]` or `StatisTopic[topicname]`. The orchestration can set the value for `ReplyTo`, and the adapter replaces it with a valid destination object in the header.  
  
 The adapter provides a schema and reference assembly describing all TIBCO EMS header properties that can be used by orchestrations. These properties can be used to either filter incoming messages or to add to the outgoing message. The rules governing the orchestration filter differs from those for the message selector for the EMS server. For example, orchestrations can filter on the `TibcoEMS.ReplyTo` or the `TibcoEMS.Destination` property, but there is no support in the JMS specification to allow message selector on this same property.  
  
 When these properties are defined by the orchestration, they are included in the header properties of the JMS message. Alternatively, when the EMS message is received, these header properties are copied to the BizTalk Server message context.  
  
 When a property matches the port configuration, the value of the property on the message takes precedence on the port’s configuration. For example, if the priority is set to 4 in the port, but you set the priority of the message to 9 in the logic of the orchestration, the message is received by TIBCO EMS as having a priority of 9.  
  
### Property Descriptions  
 The following table describes how each property is used by BizTalk Adapter for TIBCO Enterprise Message Service.  
  
|Name|Type|Description|  
|----------|----------|-----------------|  
|TibcoEMS.MessageID|string|Sending calls assign a unique ID to each message and record it in the header.<br /><br /> All message ID values start with the three-character prefix ID (which is reserved for this purpose).<br /><br /> Read-only. Changing the value does not affect the message.|  
|TibcoEMS.Timestamp|long|Sending calls record a UTC timestamp in the header. This indicates the approximate time that the server accepted the message.<br /><br /> The value is in milliseconds since January 1, 1970<br /><br /> Read-only. Changing the value does not affect the message.|  
|TibcoEMS.Redelivered|boolean|The server sets the header to indicate whether a message might duplicate a previously delivered message:<br /><br /> -   false—The server has not previously tried to deliver this message to the consumer.<br />-   true—It is likely, but not guaranteed, that the server has previously tried to deliver this message to the consumer, but the consumer did not return timely acknowledgement.<br /><br /> Read-only. Changing the value does not affect the message.|  
|TibcoEMS.Destination|string|Sending calls record the destination (queue or topic) of the message in this header. The format is adapted from a destination to a string. The format is previously described.<br /><br /> Read-only. Changing the value does not affect the message.|  
|TibcoEMS.DeliveryMode|string|Has two possible values: PERSISTENT and NON-PERSISTENT. Default value is PERSISTENT mode.<br /><br /> The adapter waits for an acknowledgement from the EMS server before acknowledging the message sent to BizTalk Server. This header property and port configuration item controls the time EMS takes to send this acknowledgement to the adapter and control the reliability of message transmission.<br /><br /> Using PERSISTENT delivery mode—the EMS server waits until the message is successfully persisted in the EMS server. This action guarantees that the message has arrived in the queue. When you use PERSISTENT mode delivery, consider the following:<br /><br /> The larger the messages, the longer it takes for BizTalk Server to consider the message as sent.<br /><br /> Using NON-PERSISTENT mode—the EMS server returns the acknowledgement before persisting the message. If a failure were to occur with the EMS server, the message might be lost when it is considered successfully sent by BizTalk Server.|  
|TibcoEMS.Expiration|long|Length of time that the message will live before expiration. If set to 0, message does not expire.<br /><br /> The time-to-live is specified in milliseconds.|  
|TibcoEMS.Priority|int|Uses a numeric ranking, between 0 and 9, to define message priority as normal or expedited. Larger numbers represent higher priority.|  
|TibcoEMS.CorrolationID|string|Can be used to link messages, such as linking a response message to a request message.<br /><br /> Usually this is the same value as the `EMS.JMSMessageID`. This is usually used together with the `EMS.JMSReplyTo` property.|  
|TibcoEMS.ReplyTo|string|A destination to which a message reply should be sent. Format is identical to the `EMS.JMSDestination` and also the port's configuration.|  
|TibcoEMS.Type|string|Does not describe the message type (text, byte, string …).<br /><br /> Some JMS providers use a message repository to store message type definitions. Client programs can store a value in this field to reference a definition in the repository. EMS supports this header but does not use it.<br /><br /> The JMS specification does not define a standard message definition repository, nor does it define a naming policy for message type definitions.<br /><br /> Some providers require message type definitions for each application message. To guarantee compatibility with such providers, client programs can set this header, even if the client application does not use it.<br /><br /> To guarantee portability, clients can set this header with symbolic values (instead of literals), and configure them to match the provider's repository.|  
  
## Properties  
 The integrator can define a set of properties to promote to the BizTalk Server message context, after which the properties are added to the properties part of the JMS message. The integrator takes care when defining the type of the property while it is creating the schema. If this property value is used in a message selector, certain operations are valid depending on the type of the property. For example, if a message selector **myMessageProperty > 5** is used, the property must be defined as an integer value, and the adapter puts the value in the message as an integer value. For the properties to be promoted, the property names must start with EMSX. They must also not have the same name as the predefined properties.  
  
 BizTalk Adapter for TIBCO Enterprise Message Service provides a schema and assembly, which declare the EMS- and JMS-specific properties that can appear in this section. These can be augmented to include any omissions. All EMSX properties referenced in the message context are put in the message property section of the EMS message. For more information, see the TIBCO EMS Users Guide.  
  
## Body  
 EMS supports all messages enumerated in the JMS specification: text, byte, stream, map, and object. The BizTalk Adapter for TIBCO EMS supports only the text message type.  
  
 JMS does not require that messages of type text contain XML-formatted bodies. The adapter does not process the body of the message; it is provided to [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] as received.  Therefore, messages submitted to BizTalk by the adapter may not always parse as XML data.  
  
## Persistent Messages  
 Messages can be persisted on the EMS server to guarantee exactly one-time delivery to a subscriber; however, this can have a significant impact on the adapter's performance. When you send messages, EMS stores the message in local storage before acknowledging reception of the message to the adapter. You can set this property on a per-message basis in the orchestration or for all messages processed by the port.  
  
 From the receiving aspect, the adapter can miss messages when it is not subscribed to the topic. Messages posted to topics when there are no subscriptions are not persisted by EMS. The adapter needs a mechanism to receive message postings even when not currently subscribed; however, like the use of persistent messages, this has a significant impact on the EMS performance, and it is not always required.  
  
> [!NOTE]
>  There is a mechanism for receive from the point of view of EMS, but it is not implemented, nor is it really desired. This is only an issue with topic; queues are not affected. A topic is generally used for time-specific data -- stock quotes, for example. If the price of a stock is missed, you know that it will be posted again later.  
  
 For these reasons the port configuration lets you enable or disable message persistence on the EMS server.  
  
## Message Acknowledgement  
 BizTalk Adapter for TIBCO Enterprise Message Service always acknowledges reception of a message when that message was correctly dispatched to BizTalk Server. This means that unacknowledged messages are resent from EMS to the adapter. The adapter cannot control the number of times the message is resent by EMS because this is a configuration of the destination itself; however, the adapter can control if the message is sent to the MessageBox or not. The EMS server controls the maximum number of times a failed message is sent to a queue.  
  
 For messages that are redelivered, the EMS server sets the `JMSRedelivered` property to True and increments the `JMSXDeliveryCount`. Both property values are available to the orchestration. You cannot move a message to the EMS un-delivered queue without delivering it there. Doing this would change the message properties.  
  
 When a message reaches its configured maximum redelivery count, the EMS server determines whether the message should be deleted or put on the $sys.undelivered queue. The EMS server makes the decision based on the `JMS_TIBCO_PRESERVE_UNDELIVERED` property; if True, the message goes to the undelivered queue, or it is deleted. This property can be set in the orchestration before sending the message. After delivery, the message property cannot be changed. Messages sent to EMS are acknowledged to BizTalk Server when they are successful. If there is a failure sending theme to EMS, they are suspended and marked as retryable.  
  
## See Also  
 [Getting Started](../core/getting-started-with-biztalk-adapter-for-tibco-enterprise-message-service.md)