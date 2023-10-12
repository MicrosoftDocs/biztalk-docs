---
description: "Learn more about: MSMQ Adapter Property Schema and Properties"
title: "MSMQ Adapter Property Schema and Properties"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# MSMQ Adapter Property Schema and Properties
The MSMQ adapter assigns values to context properties that you use in your applications. For a list of the send and receive properties in the MSMQ adapter, see [How to Configure an MSMQ Receive Location](../core/how-to-configure-an-msmq-receive-location.md) and [How to Configure an MSMQ Send Port](../core/how-to-configure-an-msmq-send-port.md).  
  
## Context Properties  
 The following table shows the context properties to which the MSMQ adapter assigns values.  
  
|**Property Name**|**Type**|**Description**|**Promoted**|  
|--------------|--------------|---------------------|------------------|  
|**Acknowledgement**|xs:int|Specifies the classification of acknowledgment that this message represents using the values in the **System.Messaging.Acknowledgment** enumeration.|No|  
|**AcknowledgeType**|xs:int|Specifies the type of acknowledgment message that the sending application requests.|No|  
|**AdministrationQueue**|xs:string|Specifies the name of the queue name that receives the acknowledgment message.|No|  
|**AppSpecific**|xs:int|Specifies application-specific information that you can use to organize different types of messages.|Yes|  
|**ArrivedTime**|xs:dateTime|Specifies the time that the message arrived in the destination queue.|No|  
|**Authenticated**|xs:boolean|Specifies whether the message was authenticated.|No|  
|**BodyType**|xs:int|Specifies the type of data that the message body contains.|No|  
|**CertificateThumbPrint**|xs:string|Specifies the thumbprint of the client certificate that you want to use for message authentication purposes.|Yes|  
|**CorrelationId**|xs:string|Specifies the message identifier used by acknowledgment, report, and response messages to reference the original message.|Yes|  
|**EncryptionAlgorithm**|xs:int|Specifies the encryption algorithm used to encrypt the body of a message.|No|  
|**Id**|xs:string|Specifies the message's identifier.|No|  
|**Label**|xs:string|Specifies an application-defined Unicode string that describes the message.|Yes|  
|**MaximumMessageSize**|xs:unsignedInt|Specifies the maximum message size in kilobytes for messages that you send to the specified queue.|No|  
|**MessageType**|xs:int|Specifies the message type. A Message Queuing message can be one of the following types:<br /><br /> -   Normal, which is either a typical message sent from an application to a queue, or a response message returned to the sending application.<br />-   Acknowledgement, which Message Queuing generates whenever the sending application requests one. For example, Message Queuing can generate positive or negative messages to indicate that the original message arrived or was read. Message Queuing returns the appropriate acknowledgment message to the administration queue specified by the sending application.<br />-   Report, which Message Queuing generates whenever a report queue is defined at the source Queue Manager. When tracing is enabled, Message Queuing sends a report message to the Message Queuing report queue each time the original message enters or leaves a Message Queuing server.|No|  
|**Priority**|xs:int|Specifies the message priority using the values defined in the **System.Messaging.MessagePriority** enumeration.|Yes|  
|**Recoverable**|xs:boolean|Specifies whether the message is guaranteed to be delivered in the event of a computer failure or network problem.|No|  
|**ResponseQueue**|xs:string|Specifies the queue that receives application-generated response messages.|No|  
|**SegmentationSupport**|xs:boolean|Specifies whether the segmentation of messages larger than 4 MB is supported.|No|  
|**SentTime**|xs:dateTime|Specifies the date and time on the sending computer that the message was sent by the source queue manager.|No|  
|**SourceMachine**|xs:string|Specifies the computer from which the message originated.|No|  
|**TimeOut**|xs:int|Specifies the time for the message to reach the destination queue before a time-out occurs.|No|  
|**TimeOutUnits**|string|Specifies the units for the **TimeOut** property. You can set the property to Days, Hours, Minutes, or Seconds.|No|  
|**Transactional**|xs:boolean|Specifies the behavior for transactional and non-transactional send ports and receive locations.|No|  
|**UseAuthentication**|xs:boolean|Specifies whether the message was (or must be) authenticated before being sent.|No|  
|**UseDeadLetterQueue**|xs:boolean|Specifies whether a copy of the message that could not be delivered should be sent to a dead-letter queue.|No|  
|**UseJournalQueue**|xs:boolean|Specifies whether a copy of the message should be kept in a machine journal on the originating computer.|No|  
|**Password**|xs:string||No|  
  
> [!NOTE]
>  The **Acknowledgement**, **AcknowledgeType**, **EncryptionAlgorithm**, and **MessageType** properties use the integer-equivalent values of the enumerations in the **System.Messaging** namespace. For more information about these values, see "System.Messaging Namespace" in .NET Framework Class Library Help.  
> 
> [!NOTE]
>  If you need to develop a BizTalk project that will make use of the MSMQ adapter context properties, the BizTalk project must contain a reference to the file **Microsoft.BizTalk.Adapter.MSMQ.MsmqAdapterProperties.dll** located in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] installation directory.  
  
## Message Labels  
 You can use the Message Queuing **Label** property in filters by adding a reference to **Microsoft.BizTalk.Adapter.MSMQ.MsmqAdapterProperties.dll** and selecting the property in the **Filter** dialog box. You can also use the property in other contexts because the MSMQ adapter automatically adds it to the message context.  
  
## See Also  
 [Configuring the MSMQ Adapter](../core/configuring-the-msmq-adapter.md)
