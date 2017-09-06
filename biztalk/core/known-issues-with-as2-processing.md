---
title: "Known Issues with AS2 Processing | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 941111d8-b394-4648-a675-e4a8f118a84b
caps.latest.revision: 40
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Known Issues with AS2 Processing
This section contains topics that describe known issues with [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] AS2 solutions.  
  
## AS2 Processing Not Supported on 64-Bit Computers  
 The [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] AS2 solution is not supported on 64-bit computers. AS2 processing only works on 32-bit computers or when running under the WOW64 emulator on 64-bit computers.  
  
## The AS2 Receive Pipelines Require the Account that the BizTalk Isolated Host Instance Process is Running Under to Be Part of the BizTalk Application Users Group  
 If you are using the AS2EdiReceive or AS2Receive pipeline, you must add the user account that the BizTalk Isolated Host Instance process is running under to the BizTalk Application Users group. The AS2EdiReceive and AS2Receive pipelines execute in the BizTalk Isolated Host Instance process.  
  
## An Empty Receipt-Delivery-Option Header Will Cause an MDN to Be Sent Synchronously  
 If the AS2Receive pipeline receives a message with an empty receipt-delivery-option header, and an asynchronous MDN is requested, the pipeline will ignore the asynchronous MDN request. It will send back a synchronous MDN instead, and post an error in the event log and in AS2 status reporting (if it is enabled). This occurs if the "Override inbound message properties" property is not selected. If that property were selected, it would override the Receipt-Delivery-Option header in the message with the value of the Receipt-Delivery-Option property in the Party as AS2 Message Sender page of the AS2 Properties dialog box.  
  
 In this instance, because the receipt-delivery-option header is empty, the AS2Receive pipeline does not have an address to send the MDN response to over an asynchronous connection. However, the pipeline still has an open synchronous connection, so it will send the MDN back over that connection. If it is a one-way receive port, BizTalk Server will close the connection after sending the HTTP 200OK message.  
  
## Use of Unfolded and Folded HTTP Line Headers  
 For maximum interoperability, you should use unfolded HTTP line headers for AS2 messages. Information Services (IIS) 7.0 supports only unfolded HTTP headers. IIS 6.0 supports folded and unfolded headers. However, not all systems can support headers with more than 80 characters per line, so for such systems folded lines should be used.  
  
 The default for AS2 in [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] is unfolded HTTP line headers.  
  
## Party Resolution Can Be Affected by a Localized Name  
 When BizTalk Server performs party resolution on an outbound AS2 message, the party resolution can be affected by a localized value in the message headers. If the AS2-To party property in the Party as AS2 Message Receiver page of the AS2 Properties dialog box is set by default to an English party name, and the value in the AS2-To header of the AS2 message is set to a non-English name, then the match will not be found.  
  
## AS2 Message Size Limitation  
 Encrypted AS2 messages should be smaller than 96 megabytes in order to be processed. This limitation is imposed by the AS2 Decoder, which is the part of the AS2Receive and AS2EdiReceive pipelines.  
  
 One way to work around this size limitation is to use compression, because an AS2 message is compressed before it is encrypted.  
  
## BizTalk EDI Application Must Not Be Modified  
 Artifacts in the BizTalk EDI Application must not be modified or deleted. If this application is modified, there is no way for you to revert to the original application by unconfiguring and reconfiguring the EDI and AS2 features.  
  
## Partner May Reject Multipart Messages  
 **Symptom**  
  
 When sending multipart messages using the AS2 send pipeline, your partner may reject the message due to a missing Content-Type MIME header.  
  
 **Possible Cause**  
  
 Content-Type is an optional header that can be present for each body part in a multipart message. Some partners require that this header is present for each body part, and set to a specific content-type.  
  
> [!NOTE]
>  The body of the message will have the Content-Type property set by the AS2 send pipeline, however any attachments will not have the Content-Type property set.  
  
 **Resolution**  
  
 If your partner requires the Content-Type header value for each body part, you must create a custom pipeline component that sets this property and use the component in the send pipeline.  
  
## When Receiving Multipart Messages, the First Part is Considered the Body  
 **Symptom**  
  
 When receiving a multipart AS2 message, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] may incorrectly identify one of the attachments as the message body.  
  
 **Possible Cause**  
  
 The MIME header of a multipart/related message may contain an optional ‘start’ parameter that indicates which of the parts should be treated as the body of the message by specifying the Content-ID of the part. If the start parameter is not present, the first part should be considered the body of the message. [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] does not honor the start parameter if it is present, and will always treat the first part as the body of the message.  
  
 **Resolution**  
  
 If your partner is unable to send the body as the first part of the multipart/related message, you must create a pipeline component that correctly identifies the body of the message.  
  
## See Also  
 [Troubleshooting EDI and AS2 Solutions](../core/troubleshooting-edi-and-as2-solutions.md)   
 [AS2 Solution Architecture](../core/as2-solution-architecture.md)   
 [Developing and Configuring BizTalk Server AS2 Solutions](../core/developing-and-configuring-biztalk-server-as2-solutions.md)