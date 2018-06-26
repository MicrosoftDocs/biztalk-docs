---
title: "EDI Support in BizTalk Server1 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7cddab7a-99ef-4dbb-bb74-9e3d03df3996
caps.latest.revision: 37
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# EDI Support in BizTalk Server
This topic provides a brief general overview of EDI and how BizTalk Server supports EDI.  
  
## Introduction to EDI  
 Electronic Data Interchange (EDI) is the single most commonly used means by which business trading partners exchange data electronically. EDI is largely messaging-oriented. Documents are implemented as flat files that can include batched transaction sets. Batched interchanges can contain multiple groups, each of which can contain multiple transaction sets or messages.  
  
 EDI consists of specific data interchange methods agreed upon by standards bodies. The primary EDI standards are X12 (standardized by ANSI and used primarily in North America) and EDIFACT (standardized by the United Nations and used primarily outside the U.S.). Other standards are derived from these, for example, HIPAA from X12 and KEDIFACT in Korea from EDIFACT. The standards are closely parallel in message structure and acknowledgment schemes, but have distinct differences.  
  
 The EDI standards prescribe the following:  
  
- The formats, character sets, and data elements used in the exchange of documents  
  
- The envelopes used in EDI transaction  
  
- The acknowledgments required to verify delivery  
  
- How to provide guaranteed, exactly-once delivery, and automatic detection and reporting of corrupted or incorrect data.  
  
  While the EDI standards establish the rules for the structure of the document, trading partners must agree on the specific information to be transmitted and how it should be used. The design of an EDI system connecting two trading partners is determined by what the standards require, and what the trading partners agree upon. For more information about EDI messaging, see [EDI Messaging](../core/edi-messaging.md).  
  
> [!NOTE]
>  EDI messages are distinguished from their transport. The EDI standards do not prescribe message transport, and EDI messages can be sent by a variety of different means.  
  
## How EDI Is Implemented in BizTalk Server  
 BizTalk Server includes native functionality that provides support for EDI. EDI is built into the product; it is not an add-in, such as an adapter or an accelerator .  
  
 **Interchange Processing**  
  
 The EDI feature performs the following receive-side and send-side processing in pipelines that enforces the rules dictated by the EDI standards.  
  
- Processes incoming EDI messages, including validating interchanges and generating acknowledgments.  
  
- Generates and sends outgoing EDI messages, including validating interchanges and processing received ACKs depending upon the configuration.  
  
  **Batch Processing**  
  
  Batch processing is handled by the receive pipeline and orchestration:  
  
- If a received batched interchange is to be split, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] splits it into its constituent transaction sets, generating an XML file for each transaction set and promoting properties required for send-side batch generation.  
  
- If a received batched interchange is to be preserved, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] processes the batch such that it retains the transaction sets and groups that it contained when the batch was received.  
  
- If a received batched interchange is to be configured, batches receive EDI transaction sets and groups into an outgoing interchange.  
  
- If multiple parties subscribe to a batched interchange, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] sends a copy of the batch to each party.  
  
  **Trading Partner Agreements**  
  
  Trading partners mutually define the Trading Partner Agreement which is a set of properties defined in the BizTalk Server Administration Console. These party properties, send and receive port/location properties, determine receive-side and send-side EDI processing. For more information about trading partner agreements, see [Trading Partner Agreement](../core/trading-partner-agreement.md).  
  
  **Interchange Status**  
  
  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] provides EDI-specific status reporting. These status reports provide a comprehensive status of an EDI document exchange transaction, including acknowledgments correlated to the interchange.  
  
## EDI Components in BizTalk Server  
 Microsoft BizTalk Server components used for EDI processing include the following:  
  
- The BizTalk EDI Application contains artifacts (including pipelines, orchestrations, and schemas) that are needed to process EDI documents.  
  
  > [!NOTE]
  >  When you configure the EDI feature in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], the configuration program creates this application. Whenever you create an application that will process EDI interchanges, you must add a reference to the BizTalk EDI Application from your application. For more information, see [How to Add a Reference to the BizTalk Server EDI Application](http://msdn.microsoft.com/library/7af066fb-372f-4709-b566-c8d6b4a9d782).  
  
- The BizTalk EDI Receive Pipeline (EdiReceive pipeline) parses EDI-encoded documents, splits EDI batches, converts the EDI-encoded documents into XML encoding, performs EDI and XSD validation, and performs HIPAA X12 sub-document splitting. For more information, see [EDI Receive Components](../core/edi-receive-components.md).  
  
- The BizTalk EDI Send Pipeline (EdiSend pipeline) converts XML documents into X12 or EDIFACT encoding, serializes EDI-encoded documents, and performs EDI and XSD validation. For more information, see [EDI Send Components](../core/edi-send-components.md).  
  
- The Trading Partner Management (TPM) user interface enables you to set processing properties for trading partners engaging in EDI document exchange and AS2 document transport. For more information, see [The Role of Agreements in EDI Processing](../core/the-role-of-agreements-in-edi-processing.md) and **EDI and AS2 UI** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].
  
- The batching orchestration batches EDI interchanges and sets context properties for sending of the batched interchange. The routing orchestration handles the instances in which messages match multiple batches, creating as many copies of the message as required. For more information, see [Processing Incoming Batches](../core/processing-incoming-batches.md) and [Batching Outgoing EDI Messages](../core/batching-outgoing-edi-messages.md).  
  
- The status reporting user interface provides comprehensive status of EDI interchanges and correlated acknowledgments. For more information, see [EDI and AS2 Status Reporting](../core/edi-and-as2-status-reporting.md).  
  
- Design time tools in Visual Studio enable you to generate an instance, validate an instance, validate a schema, test a map, and validating a map. For more information, see [Using Design-Time XML Tools](../core/using-design-time-xml-tools.md).  
  
- A schema repository includes X12, EDIFACT, HIPAA X12N 4010A XSD, EANCOM, and control schemas. For more information, see [EDI Document Schema Support](../core/edi-document-schema-support.md).  
  
- A migration tool (Party Migration Tool) enables you to migrate EDI party data from BizTalk Server 2006 R2 or BizTalk Server 2009 to BizTalk Server. For more information, see [Migrating EDI Artifacts from a Previous Version of BizTalk Server](http://msdn.microsoft.com/library/b956a97e-03d0-47ea-a2ce-c07a339c0f2c).  
  
## See Also  
 [EDI Processing in BizTalk Server](../core/edi-processing-in-biztalk-server.md)   
 [HIPAA Support in BizTalk Server](../core/hipaa-support-in-biztalk-server.md)   
 [EDI Support Issues](../core/edi-support-issues.md)   
 [EDI Solution Architecture](../core/edi-solution-architecture.md)   
 [EDI and AS2 Status Reporting](../core/edi-and-as2-status-reporting.md)   
 [Developing and Configuring BizTalk Server EDI Solutions](../core/developing-and-configuring-biztalk-server-edi-solutions.md)