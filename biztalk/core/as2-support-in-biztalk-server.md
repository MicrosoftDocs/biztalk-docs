---
title: "AS2 Support in BizTalk Server | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f8ee230e-8f5f-4b51-99e2-0b38acaf5707
caps.latest.revision: 18
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# AS2 Support in BizTalk Server
This topic provides a brief general overview of AS2 processing and how BizTalk Server implements it.  
  
## Introduction to AS2  
 A common transport used for EDI is Value-Added Networks (VANs). These are private networks that provide value-added services, such as precise and legally binding audit trails. However, companies are migrating to exchanging EDI documents over the Internet. This lowers costs, increases flexibility and efficiency, and has advantages in terms of redundancy and scalability.  
  
 The most common way of implementing EDI over the Internet (EDIINT) is by AS2 (Applicability Statement 2). The AS2 specification defines MIME-based secure peer-to-peer business data interchange. Messages containing an envelope with MIME data are transmitted using HTTP over TCP/IP.  
  
 AS2 uses the HTTP POST operation to send EDI, XML, or other business data. AS2 is not restricted to sending EDI data. Request-URI identifies a process to be used to unpack and handle message data. A message disposition notification (MDN) is returned as an acknowledgment either in the HTTP response message body or by a new HTTP POST operation to a URL for the original sender.  
  
 For more information about EDI messaging, see [AS2 Messaging](../core/as2-messaging.md).  
  
## How AS2 Is Implemented in BizTalk Server  
 BizTalk Server includes native functionality providing support for AS2. It is not an add-in to the product, such as an adapter or an accelerator. It is built into the product, and provides the following functionality:  
  
- [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] uses AS2-defined methods to send, receive, and verify messages. [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] helps ensure the security of data transfer by encryption, signing, and compression. To do so, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] uses encryption keys, digital signatures, and certificates.  
  
- [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] enables you to save incoming and outgoing AS2 messages in non-repudiation storage. This includes saving encoded or decoded AS2 messages and saving MDNs.  
  
- [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] provides the ability to preserve attachment file names as part of the AS2 message.  
  
- [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] enables you to check for duplicate incoming messages.  
  
- You can return MDNs either synchronously over the same connection as the message being acknowledged, or asynchronously over a different connection.  
  
- You can resend an AS2 message if an MDN is not received within a specified time period.  
  
- [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] provides AS2-specific status reporting. These reports provide comprehensive status of an AS2 transmission, including acknowledgments correlated to the interchange.  
  
- AS2 requires that the HTTP adapter is used on both the receive-side and the send-side.  
  
- [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] enables you to override the default signing certificate for AS2 messages by defining a certificate per agreement. For instructions on how to specify a different certificate for a party, see [Configuring AS2 Properties](../core/configuring-as2-properties.md).  
  
## AS2 Components in BizTalk Server  
 BizTalk Server components used for AS2 transport include the following:  
  
- The BizTalk EDI Application that contains artifacts (including pipelines and schemas) that are needed to process AS2 documents.  
  
  > [!NOTE]
  >  When you configure the AS2 feature in BizTalk Server, the configuration program creates this application. Whenever you create an application that will process AS2 messages, you must add a reference to the BizTalk EDI Application from your application. For more information, see [How to Add a Reference to the BizTalk Server EDI Application](http://msdn.microsoft.com/library/7af066fb-372f-4709-b566-c8d6b4a9d782).  
  
- The AS2EdiReceive pipeline that performs AS2 processing, and then EDI processing, of an EDI message received over AS2. For more information, see [AS2 Receive Components](../core/as2-receive-components.md).  
  
- The AS2Receive pipeline that performs AS2 processing of a non-EDI message received over AS2. For more information, see [AS2 Receive Components](../core/as2-receive-components.md).  
  
- The AS2EdiSend pipeline that performs EDI processing, and then AS2 processing, of an EDI message being sent over AS2. For more information, see [AS2 Send Components](../core/as2-send-components.md).  
  
- The AS2Send pipeline that performs AS2 processing of a non-EDI message being sent over AS2. For more information, see [AS2 Send Components](../core/as2-send-components.md).  
  
- The Trading Partner Management (TPM) user interface that enables you to set processing properties for trading partners engaging in AS2 document transport. For more information, see [The Role of Agreements in AS2 Processing](../core/the-role-of-agreements-in-as2-processing.md) and the **EDI and AS2 UI** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].
  
- Status reporting user interface that provides comprehensive status of AS2 interchanges and correlated acknowledgments. For more information, see [EDI and AS2 Status Reporting](../core/edi-and-as2-status-reporting.md).  
  
- A migration tool (Party Migration Tool) enables you to migrate party data containing AS2 properties from BizTalk Server 2006 R2 or BizTalk Server 2009 to BizTalk Server. For more information, see [Migrating EDI Artifacts from a Previous Version of BizTalk Server](http://msdn.microsoft.com/library/b956a97e-03d0-47ea-a2ce-c07a339c0f2c).  
  
## See Also  
 [AS2 Solution Architecture](../core/as2-solution-architecture.md)   
 [EDI and AS2 Status Reporting](../core/edi-and-as2-status-reporting.md)   
 [Developing and Configuring BizTalk Server AS2 Solutions](../core/developing-and-configuring-biztalk-server-as2-solutions.md)