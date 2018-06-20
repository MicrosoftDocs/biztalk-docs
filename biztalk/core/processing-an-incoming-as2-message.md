---
title: "Processing an Incoming AS2 Message | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 998ff334-71e2-4686-b2b7-44940a0ebed1
caps.latest.revision: 32
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Processing an Incoming AS2 Message
The AS2 receive pipelines process an incoming message over AS2. The AS2EdiReceive receive pipeline processes an EDI-encoded message, using the EDI Disassembler. The AS2Receive receive pipeline processes a non-EDI-encoded message, using the AS2 Disassembler. The two pipelines process the payload of the AS2 message and generate an MDN differently; however, both receive pipelines use the AS2 Decoder to process the AS2 message.  
  
 When the AS2EdiReceivePipeline processes an AS2 message with an EDI payload, it completes the AS2 processing of the received message before performing the EDI processing. When the pipeline generates an EDI acknowledgment for the EDI payload of an AS2 message, it must return the EDI acknowledgment asynchronously, because the connection is closed by the AS2 response.  
  
## The Receive Port  
 An HTTP receive port is used to receive an AS2 message with an EDI or non-EDI payload. If an MDN must be returned synchronously, then the receive port must be a request-response port.  
  
 An MDN can be returned synchronously or asynchronously. This is determined by the Disposition-notification-to header of the AS2 message, unless the **Use agreement settings for validation and MDN instead of message header** property is selected in the one-way AS2 agreement tab of the **Agreement Properties** dialog box. If the property is selected, the way the MDN is returned is determined by the **Request asynchronous MDN** property in the **Sender MDN Settings** page of the one-way AS2 agreement tab of the **Agreement Properties** dialog box. For more information, see [AS2 Messages](../core/as2-messages.md) and [MDN Messages](../core/mdn-messages.md).  
  
 If the MDN will be returned synchronously, the MDN is returned over the send port of the two-way receive location. This MDN serves as the HTTP response, for example, a 200OK indicating successful reception of the message.  
  
 If the MDN will be returned asynchronously, the MDN must be returned over a separate send port. If a dynamic send port is used, the MDN will be sent to the address contained in Disposition-notification-to header.  
  
> [!NOTE]
>  The two-way receive port used to receive AS2 messages should not be used to receive MDN messages. MDN messages should be received on a static one-way receive port. Using a request/response receive port for an MDN returned asynchronously would prevent a 200OK message from being returned in response to the incoming MDN, thereby causing unnecessary retries of the MDN transmission.  
  
## How the AS2 Receive Pipelines Work  
 The steps that the AS2 receive pipelines performs in processing an incoming AS2 message are as follows:  
  
- Determines the sending party by matching the AS2-From value in the AS2 header of the message with the value for AS2-From list in the **Identifiers** page of the one-way AS2 agreement tab of the **Agreement Properties** dialog box. If that fails, attempts to determine the sending party by matching the AS2-From context property that is set for the incoming message with the name of a party. If a match is found, and the **Use agreement settings for validation and MDN instead of message header** property is selected in the one-way AS2 agreement tab of the **Agreement Properties** dialog box, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will use the AS2 properties associated with the agreement for the party for processing the AS2 message. If the property is not selected, the receive pipeline will use the AS2 header tags in the incoming message. If the agreement is not found, the pipeline aborts processing, suspends the message, and raises an exception.  
  
  > [!NOTE]
  >  The **Use agreement settings for validation and MDN instead of message header** property allows you to validate that an incoming message has signing, encryption, and compression properties (if those properties are specified in the agreement in the **Validation** tab of the one-way agreement), and if not, to suspend the message and post an error. These changes must be negotiated with the agreement for the sending party. For more information see [Configuring AS2 Properties](../core/configuring-as2-properties.md).  
  
- If the agreement for the sending party is determined, but an error arises when the receive pipeline attempts to process the AS2 message, the pipeline will set the context property MessageDestination on the AS2 message to SuspendQueue. The receive pipeline will then suspend the message in the MessageBox. The receive pipeline will also set the `EdiIntAS.IsAS2FailedMessage` context property to True. If an MDN is enabled by setting **Request MDN** in the **Sender MDN Settings** page of the one-way AS2 agreement tab of the **Agreement Properties** dialog box, the pipeline will then return the appropriate MDN to the sender. The pipeline will always attempt to return an MDN if it is requested.  
  
- Determines if the message is a duplicate, if the **Check for duplicate messages within** option is selected in the **Validation** page of the one-way AS2 agreement tab of the **Agreement Properties** dialog box. Duplicate message detection is accomplished by matching the AS2-From, AS2-To, and Message-ID values on the inbound message to values on messages previously received. If all three values match, the receive pipeline will set the value of the `EdiIntAs.IsAS2MessageDuplicate` context property to true. If the **Suspend duplicate messages** option is also selected on the **Validation** page, the message will be suspended and an error logged.  
  
- Retrieves the file name, if any, of each attachment and promotes this to the context properties.  
  
- Makes a copy of the message (in wire format), and stores the copy in the non-repudiation receipt database, if enabled in the one-way AS2 agreement properties.  
  
- Performs MIME processing, including verifying the signature and decrypting the message (based upon the header tags).  
  
- Decompresses the received message, if it was compressed.  
  
- Generates an HTTP response, appended to the MDN in synchronous request-response mode, or sent as a standalone response in asynchronous mode.  
  
- Generates an MDN response, if requested. The pipeline will generate an MDN based upon agreement properties, if the **Use agreement settings for validation and MDN instead of message header** property is set, or from context properties, if that property is not set. If the configuration settings and the headers in the incoming message are inconsistent, the pipeline will generate a negative MDN.  
  
- The EDI Disassembler in the AS2EdiReceive receive pipeline generates an EDI acknowledgment, if the message was EDI-encoded and an acknowledgment was enabled. The pipeline will route the EDI acknowledgment to the MessageBox, from which a dynamic send port will pick it up and send it out asynchronously. EDI acknowledgments are always sent out asynchronously over AS2 transport, because either an MDN or an HTTP response is sent out synchronously.  
  
- Makes a copy of the MDN, and stores it in the non-repudiation receipt database, if enabled in the one-way AS2 agreement properties.  
  
- Makes a copy of the decoded message, and stores the copy in the non-repudiation receipt database, if enabled in the one-way AS2 agreement properties.  
  
  If an AS2 error occurs, no further processing will occur on the received message. However, the receive pipeline will still generate an MDN response.  
  
## See Also  
 [How BizTalk Server Receives AS2 Messages](../core/how-biztalk-server-receives-as2-messages.md)   
 [AS2 Messages](../core/as2-messages.md)   
 [MDN Messages](../core/mdn-messages.md)