---
title: "How BizTalk Server Processes Large Messages | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 62c070be-dff5-4349-9e36-dd3a7caf1752
caps.latest.revision: 33
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How BizTalk Server Processes Large Messages
## What is a large message?  
 Unfortunately, the answer to this question isn't tied directly to a specific message size, but rather, depends on specific bottlenecks in your Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] system. The problems associated with large messages can be divided into the following categories:  
  
-   **Out of memory errors** Certain types of message processing - such as mapping, validation, and property promotion - load the entire message into memory. If the size of the message in memory exceeds available resources, then an out of memory error occurs. The size threshold for messages that fall into this category is much lower than the size threshold for messages that are not loaded into memory. For example, a 10 MB flat file that is parsed into XML and then mapped may grow by a factor of 10 or more to consume over 100 MB of memory, whereas a 100 MB XML document that is not parsed or mapped may actually only consume 1 MB of memory as it is streamed to the MessageBox database.  
  
-   **Performance problems for messages that are not loaded into memory** Messages that are not required to be loaded into memory are streamed to the MessageBox database using the .NET XmlReader interface. While they are not subject to the size limitations on messages that must be loaded into memory, there are some important factors that impact how BizTalk Server processes messages that are streamed to the MessageBox database.  
  
## Factors that affect the processing of large messages  
 The original message size, message format, and type of message processing all affect how BizTalk Server processes large messages.  
  
- **Original message size** The size of the message received by BizTalk Server is the most visible indication of how large the message will be when it is processed by BizTalk Server. The original size of a message has a much greater impact on performance if the entire message is loaded into memory than if the message is streamed to the MessageBox database.  
  
- **Message format** Messages are received into BizTalk Server in one of two primary formats: XML files or flat files.  
  
  -   **XML files** In order for BizTalk Server to perform any processing on a message other than pass through routing, the message must be in the XML file format. If the files to be processed are received in XML format then they will retain their original size for the most part.  
  
  -   **Flat files** Flat files must be parsed into an XML format before BizTalk Server can perform any processing other than pass through routing. Parsing a flat file into an XML file can greatly increase the size of the file. Flat files do not contain XML tags with descriptive information about their data. XML files, on the other hand, wrap all of their data in descriptive XML tags. In some scenarios parsing can increase the size of a flat file by a factor of 10 or more, depending on how much descriptive data is contained in the XML tags for the file.  
  
  -   **Flat file documents wrapped in a single CDATA section node in an XML document** This type of document is a combination of both XML and flat file and can be problematic because BizTalk Server must load the entire wrapped flat file document into memory before processing it.  
  
- **Type of message processing** In BizTalk Server, there are two types of message processing: Routing only and Mapping. The performance variables tied to the type of message processing that is performed are message size and whether the message is loaded into memory.  
  
  - **Routing only** If BizTalk Server is only used only for routing messages based upon promoted message properties, then the message is streamed into the Messagebox database using the .NET XmlReader interface, and message parts are not individually loaded into memory. In this scenario, out of memory errors are not an issue and the primary consideration is the amount of time that is required to write very large messages (over 100 MB) into the Messagebox database. The BizTalk Server development team has successfully tested the processing of messages up to 1 GB in size when performing routing only.  
  
     The primary factor that determines performance in this scenario is the **Large message fragment size** used to fragment the data into the database. The **Large message fragment size** is a configurable option on the **BizTalk Group Properties** configuration page and has a default value of 102400 bytes (100 KB). Increasing this value reduces the number of round trips required to stream a message into the MessageBox database.  
  
  - **Mapping** Transforming a document with a map can be a memory-intensive operation. When a document is transformed by a map, BizTalk Server passes the message to the .Net XSLCompileTransform class, which loads the XSL style sheet. After the Load method completes successfully, the Transform method can be called simultaneously from multiple threads. [XslCompiledTransform Class](http://go.microsoft.com/fwlink/p/?LinkID=282683) provides more information on the XSLCompiledTransform class.  
  
     [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] significantly improves memory management for large documents by implementing a configurable message size threshold for loading documents into memory during transforms. Any message with a size below this threshold is handled in memory; any message with a size above this threshold is buffered to the file system to reduce memory requirements. The default message size threshold is 1 MB.  
  
## Guidelines for processing large messages  
 Follow these guidelines to improve performance when processing large messages in BizTalk Server:  
  
1. Adjust the message size threshold above which documents are buffered to the file system during mapping. To modify the size threshold, create a DWORD value named **TransformThreshold** at the following location in the BizTalk Server registry:  
  
   ```  
   HKLM\Software\Microsoft\BizTalk Server\3.0\Administration\TransformThreshold  
   ```  
  
    After you have created this value, enter a decimal value with the number of bytes to set the new threshold to. For example, enter a decimal value of 2097152 to increase the message size threshold to 2 MB (from the default of 1 MB). Increase this value on systems with a large amount of available memory to improve throughput. Buffering documents to disk conserves memory at a cost to overall throughput.  
  
   > [!NOTE]
   >  By default, documents that are buffered to the file system during mapping are written to the *%temp%* directory of the BizTalk Server computer. Change the setting for the *%temp%* environment variable to a non-system disk to improve performance when buffering large messages to the file system during mapping.  
  
2. Minimize the use of maps in orchestrations:  
  
   -   If you are using a map to extract or set properties used with business logic in an orchestration, use distinguished fields or promoted properties instead. When extracting or setting values with a map the document is loaded into memory. When using distinguished fields or promoted properties, the Orchestration engine accesses the message context and does not load the document into memory.  
  
   -   If you are using a map to aggregate several fields into one field, use distinguished fields or promoted properties with an orchestration variable to accumulate the result set.  
  
   -   Do not configure an orchestration with multiple inputs to transform shapes. An orchestration that contains multiple inputs to transform shapes will not stream to the file system while mapping. This limitation will cause the entire document that is being mapped to load into memory if the document size exceeds the specified TransformThreshold registry value. One possible workaround to this issue would be to apply transforms at the receive port level so that the orchestration never accepts more than a single input to transform shapes.  
  
3. Adjust the **Large message fragment size** property exposed on the **BizTalk Group Properties** configuration page:  
  
    If the in-memory size of a received message exceeds the number of bytes specified for **Large message fragment size** then the message is split into fragments of the specified size and the fragments are written into the MessageBox under the context of a Microsoft Distributed Transaction Coordinator (MSDTC) transaction as follows:  
  
   1.  If the incoming message is being published under the context of an existing MSDTC transaction, then this transaction is used when writing the message fragments to the MessageBox. For example if the incoming message is being published by a transactional adapter configured to require transactions then the existing transaction would be used when writing the message fragments to the MessageBox.  
  
   2.  If the incoming message is not being published under the context of an existing MSDTC transaction, then a new MSDTC transaction is created to write the message fragments.  
  
   -   Increase the value for **Large message fragment size** to reduce the frequency with which large messages are fragmented and reduce the incidence of creating the associated MSDTC transactions. This should be done because excessive use of MSDTC transactions is expensive from a performance standpoint. Note that increasing this value may also increase the amount of available memory that is used.  
  
   -   If it takes longer than the maximum allowable MSDTC transaction timeout of 60 minutes to write a message to the MessageBox, then the transaction times out, an error results, and the attempt to write the message fails and is rolled back. The **Large message fragment size** value should be increased enough to avoid this problem when processing very large messages. Depending on available memory, this value should be increased up to a maximum value of 1000000 bytes.  
  
   -   Each message fragment in a message creates one or more SQL Server database locks against the MessageBox database. When the number of locks exceeds several hundred thousand, it is possible that SQL Server will start generating “out of lock” errors. If this problem occurs, increase the **Large message fragment size** to reduce the number of SQL Server database locks made against the MessageBox database.  
  
4. Consider housing your MessageBox database on a 64-bit version of SQL Server if you are experiencing "out of lock" errors. The number of available locks is significantly higher on the 64-bit version of SQL Server.  
  
5. Adjust the **Large message threshold** property exposed on the **BizTalk Group Properties** configuration page:  
  
    As a message batch is processed, if the in-memory size of a message batch reaches the number of bytes specified for **Large message threshold** then the portion of the message batch that has been processed is written to the MessageBox before the remainder of the message batch is processed. This is done under the context of an MSDTC transaction as follows:  
  
   1. If the message batch is being published under the context of an existing MSDTC transaction, then this transaction is used when writing the processed portion of the message batch to the MessageBox. For example if the incoming message batch is being published by a transactional adapter configured to require transactions then the existing transaction would be used when writing the processed portion of the message batch to the MessageBox.  
  
   2. If the message batch is not being published under the context of an existing MSDTC transaction, then a new MSDTC transaction must be created to write the portions of the message batch to the MessageBox. The MSDTC transaction is used to ensure that all of the portions of a given message batch are successfully written to the MessageBox database.  
  
      The **Large message threshold** setting is directly applicable to message batches but since a message batch can be set to a value of one, the **Large message threshold** setting can also be indirectly applicable to individual messages. For example when a message batch of one message exceeds the specified **Large message threshold** parameter then the **Large message threshold** in effect applies only to the single message in the batch.  
  
   -   The **Large message threshold** parameter should be adjusted to mitigate the creation of MSDTC transactions used to apportion message batches to the MessageBox. This should be done because the excessive use of MSDTC transactions is expensive from a performance standpoint. Use the following calculation to determine what the minimum value for the **Large message threshold** setting should be to avoid unnecessarily creating MSDTC transactions:  
  
       ```  
       Batch Size * Average size (in bytes) of each message in the batch after being processed by the receive pipeline < Large message threshold  
       ```  
  
        As long as the total size in bytes of a message batch does not exceed the specified value for **Large message threshold** then there is no need for BizTalk to initiate an MSDTC transaction to apportion the message batch to the MessageBox database.