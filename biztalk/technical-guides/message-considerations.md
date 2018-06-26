---
title: "Message Considerations | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5ca466fa-426c-46f6-a400-747ff51ff8f4
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Message Considerations
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] provides an extensive set of capabilities for sending, receiving, transforming, and processing messages. Some of these capabilities include:  
  
- Ability to send and receive messages using multiple industry standard transports such as HTTP, SMTP, FTP/FTPS  and WCF. Transport level support for sending and receiving messages is accomplished using [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] adapters. Integration of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] message processing with various “line of business” (LOB) applications is accomplished using one of many available [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] accelerators or adapters, such as the BizTalk Accelerator for HIPAA, BizTalk Accelerator for SWIFT, or the BizTalk SAP adapter. These accelerators and adapters conform to industry standards which in turn accommodates straightforward integration of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] with systems that conform to particular industry standard.  
  
- Ability to process multiple message formats, such as plain text, XML, binary, and others. This functionality is crucial to providing integration of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] with a broad spectrum of trading partners.  
  
- Support for message transformation or document mapping. Mapping accommodates the transformation of data between different schemas. For example, mapping could be used to transform the contents of a received customer purchase order into a receipt with shipping notification to be sent back to the customer.  
  
- BizTalk Server orchestrations provide functionality for creating business processes that span time, organizations, applications, and people. [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] provides the Orchestration Designer graphical interface to develop business processes that include support for transactions (both traditional “atomic” MSDTC type and long running), exception handling, debugging, tracking, and extensibility for calling external code.  
  
  > [!NOTE]
  >  See [Optimizing Orchestration Performance](../technical-guides/optimizing-orchestration-performance.md) for guidance about best practices to follow when using orchestrations in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. See the topic [Creating Orchestrations Using Orchestration Designer](http://go.microsoft.com/fwlink/?LinkId=158997) (<http://go.microsoft.com/fwlink/?LinkId=158997>) in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] documentation for in-depth information about using Orchestration Designer.  
  
  The remainder of this topic describes performance considerations related to the size, complexity, and distribution profile of messages that are processed in a BizTalk Server environment.  
  
## Message size considerations  
 While BizTalk Server imposes no restriction on message size, practical limits and dependencies might require you to minimize the size of your messages because large messages require more processing resources. As message size increases, overall throughput (messages processed per second) decreases. When designing your scenario and planning for capacity, consider the average message size, message type, and number of messages BizTalk Server processes. Do not use unnecessarily long attribute and tag names; if possible, keep the length under 50 characters. For example, do not use a 200-character tag name for a message size of only 1 byte.  
  
 If the in-memory size of a received message exceeds the number of bytes specified for the Large message fragment size (configurable on the Group Properties page for the BizTalk Group in the BizTalk Server Administration console), the message is split into fragments of the specified size. Additionally, the fragments are written into the Messagebox under the context of a Microsoft Distributed Transaction Coordinator (MSDTC) transaction as follows:  
  
1. If the incoming message is being published in the context of an existing MSDTC transaction, this transaction is used when writing the message fragments to the BizTalk MessageBox database. For example, if the incoming message is being published by a transactional adapter configured to require transactions, the existing transaction would be used when writing the message fragments to the MessageBox database.  
  
2. If the incoming message is not being published in the context of an existing MSDTC transaction, a new MSDTC transaction is created to write the message fragments to the MessageBox database. In this scenario, the following considerations apply:  
  
   -   Increase the value for **Large message fragment size** to reduce the frequency with which large messages are fragmented and reduce the incidence of creating the associated MSDTC transactions. This should be done because excessive use of MSDTC transactions is expensive from a performance standpoint. Note that increasing this value may also increase the amount of available memory that is used.  
  
   -   If it takes longer than the maximum allowable MSDTC transaction timeout of 60 minutes to write a message to the MessageBox, the transaction times out, an error occurs, and the attempt to write the message fails and is rolled back. The **Large message fragment size** value should be increased enough to avoid this problem when processing very large messages. Depending on available memory, this value should be increased up to a maximum value of 1000000 bytes.  
  
   -   Each message fragment in a message creates one or more SQL Server database locks against the MessageBox database. When the number of locks exceeds several hundred thousand, it is possible that SQL Server will generate “out of lock” errors. If this problem occurs, increase the value for **Large message fragment size** to reduce the number of fragments (which decreases the number of SQL Server database locks made against the MessageBox database) or consider housing your MessageBox database on a 64-bit version of SQL Server. The number of available locks is significantly higher on the 64-bit version of SQL Server than on a 32-bit version of SQL Server. The following formula can be used to estimate the maximum number of messages per interchange when the MessageBox database is housed on a 32-bit version of SQL Server:  
  
       ```  
       200,000 / (Number of CPUs * BatchSize * MessagingThreadPoolSize)  
       ```  
  
   For more information about how BizTalk Server processes large messages, including guidelines for processing large messages, see [How BizTalk Server Processes Large Messages](http://go.microsoft.com/fwlink/?LinkID=154680) (http://go.microsoft.com/fwlink/?LinkID=154680).  
  
## Message type considerations  
 Messages are received into BizTalk Server in one of two primary formats: XML files or flat files. Message type should always be factored into the message distribution profile because of the varying resource requirements of XML and flat file messages.  
  
-   **XML files** In order for BizTalk Server to perform any processing on a message other than pass-through routing, the message must be in the XML file format.  
  
-   **Flat files** Flat files must be parsed into an XML format before BizTalk Server can perform any processing other than pass-through routing. Parsing a flat file into an XML file can greatly increase the size of the file. Flat files do not contain XML tags with descriptive information about their data. XML files, on the other hand, wrap all of their data in descriptive XML tags. In some scenarios, parsing can increase the size of a flat file by a factor of 10 or more, depending on how much descriptive data is contained in the XML tags for the file.  
  
-   **Flat file documents wrapped in a single CDATA section node in an XML document** This type of document is a combination of both XML and flat file, and is often memory-intensive, since BizTalk Server must load the entire wrapped flat file document into memory before processing it.  
  
## Overload considerations  
 Most BizTalk Server applications do not receive messages at a specific, constant rate. Typically, message processing is subject to peaks and valleys. , For example, an online banking application may process a higher volume of messages first thing in the morning, then during the middle of the day, and at the end of the day. BizTalk Server solutions should be tested to ensure that they will be able to handle these overload scenarios. To determine how well a BizTalk Server solution can handle overload scenarios, the maximum sustainable throughput (MST) of the BizTalk Server solution should be determined. The MST is the highest load of message traffic that a system can handle indefinitely in a production environment. For more information about MST, see [Planning for Sustained Performance](http://go.microsoft.com/fwlink/?LinkID=158065) (<http://go.microsoft.com/fwlink/?LinkID=158065>) and [What Is Sustainable Performance?](http://go.microsoft.com/fwlink/?LinkID=132304) (<http://go.microsoft.com/fwlink/?LinkID=132304>) in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] documentation.  
  
## Schema complexity  
 The throughput for message parsing (especially flat-file parsing) is affected by the complexity of the schemas. As schema complexity increases, overall performance decreases. When designing schemas, reduce the length of node names, and move promoted properties to the top of the schema. This reduces retrieval time and thereby increases performance.  
  
## Map complexity  
 Depending on the complexity of the maps, map transformation can be resource-intensive. As map complexity increases, overall performance decreases. To improve overall performance, minimize the number of links and functoids used in your maps, especially functoids that call external resources such as the DB Lookup functoid.  
  
## Flat-file parsing considerations  
 The two factors that have the highest impact on the performance of flat-file parsing are file size and schema complexity. An ambiguous schema is a schema that contains many optional fields. When large file sizes are used, a schema with many optional fields can degrade performance because larger files may match different branches of the schema. Schema complexity has less impact on smaller files than on larger files.  
  
## See Also  
 [Optimizing BizTalk Server Applications](../technical-guides/optimizing-biztalk-server-applications.md)