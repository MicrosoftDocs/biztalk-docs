---
title: "Streaming large object data types in Oracle Database adapter | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "streaming, support in the WCF service model"
  - "streaming, support for"
  - "streaming, support in BizTalk Server"
  - "streaming, support in the WCF channel model"
ms.assetid: c6cbe870-6794-4bf1-90c1-db65a242e8fe
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Streaming large object data types in Oracle Database adapter
The [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] supports streaming for Oracle large object (LOB) data types. With the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] operations are invoked and responses are returned by exchanging SOAP messages. A SOAP message body is composed of XML nodes.  
  
 There are two kinds of message streaming that are supported by the adapter:  
  
- **Node streaming**. In node streaming each node is buffered by the adapter before it is sent to the Oracle database (or returned to the client). This means that, for an LOB data type, the entire value is read into a buffer.  
  
- **Node-value streaming**. In node-value streaming the actual value of the node can be streamed in chunks between the Oracle database and the client. Node-value streaming supports end-to-end streaming of LOB data types between the adapter client and the Oracle database.  
  
  Both of these streaming modes rely on support for node streaming and node-value streaming on messages in WCF. For this reason, streaming for LOB types is tied closely to how messages are created and consumed both by the adapter and by a client application. One result of this is that support for streaming LOB types is not the same across all programming models.  
  
  The sections in this topic provide:  
  
- Fundamental background information about how message streaming is supported in WCF and how it is implemented by the adapter.  
  
- Information about how streaming for LOB data types is supported when you use the adapter in each programming model.  
  
## Streaming Fundamentals  
 The support for streaming implemented by the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] is a combination of:  
  
-   Message streaming support in WCF.  
  
-   Streaming support in the Oracle client library (ODP.NET).  
  
-   The way messages are created and consumed internally by the adapter.  
  
### Message Streaming Support in WCF  
 How WCF supports streaming on a message depends both on how the message is created and how the message is consumed.  
  
- A WCF message is created by using the static **Create** method of **System.ServiceModel.Channels.Message**. This method has several overloads that support different ways of passing the message body. A WCF message can be created by passing the message body using:  
  
  -   A **System.Xml.XmlReader**, or  
  
  -   A **System.ServiceModel.Channels.BodyWriter**.  
  
- A WCF message can be consumed using  
  
  -   An **XmlReader** by calling **Message.GetReaderAtBodyContents()**, or  
  
  -   An **XmlDictionaryWriter** by calling **Message.WriteBodyContents(XmlDictionaryWriter)**.  
  
  The following table shows how WCF behaves for different combinations of creating and consuming messages.  
  
|Message Created With|Message Consumed With|WCF Behavior|  
|--------------------------|---------------------------|------------------|  
|**XmlBodyWriter**|**XmlDictionaryWriter**|**Node-value streaming** is supported. WCF pipes the two writers together to enable streaming. Both the **XmlBodyWriter** and the **XmlDictionaryWriter** must support node-value streaming for it to occur.|  
|**XmlBodyWriter**|**XmlReader**|**Node streaming** is supported. WCF internally buffers the **XmlReader**.|  
|**XmlReader**|**XmlDictionaryWriter**|**Node streaming** is supported. WCF internally buffers the **XmlReader** and calls back into the **XmlDictionaryWriter**.|  
|**XmlReader**|**XmlReader**|**Node streaming** is supported. WCF internally buffers the **XmlReader**.|  
  
### Streaming Support in the Oracle Client Library (ODP.NET)  
 ODP.NET supports streaming in the following manner:  
  
-   Streaming is supported only on Oracle LOB data types.  
  
-   For some table (and view) operations, LOB data types are buffered. Therefore, no streaming is supported.  
  
### Internal Message Handling by the Adapter  
 The adapter supports streaming in the following manner:  
  
-   The adapter extends **Message** to implement a custom message class, **Microsoft.Adapters.AdapterUtilities.AdapterMessage**. It creates an **AdapterMessage** for all WCF messages that it provides to the adapter client; this includes the response messages for all outbound operations and the request message for the POLLINGSTMT operation. This enables the adapter to support node-value streaming for the ReadLOB operation by providing an **XmlReader** that supports **ReadValueChunk** to adapter clients.  
  
-   The adapter consumes all messages received from the client by using a custom implementation of **XmlDictionaryWriter**.  
  
-   The adapter creates all messages that it sends to the client by using a custom implementation of **XmlBodyWriter**, except for the ReadLOB response message. (This includes response messages for all outbound operations and the request message for the POLLINGSTMT operation.)  
  
## Streaming Support in the WCF Channel Model  
 The following table provides detailed information about how streaming is supported in the WCF channel model.  
  
|Operation|Node Streaming|Node-Value Streaming|Description|  
|---------------|--------------------|---------------------------|-----------------|  
|Table Insert operation|Supported*|Not supported between the adapter and the Oracle database. Supported between the client and adapter.*|End-to-end node-value streaming is not supported because the values of LOB columns are buffered by ODP.NET, and then the insert is performed. However, node-value streaming between the client and the adapter is possible for LOB columns, if the client creates the message with a **BodyWriter**.|  
|Table Select operation|Supported|Supported|The adapter uses a **BodyWriter** to create the response message. If the client consumes the message using an **XmlDictionaryWriter**, node-value streaming for LOB columns occurs.|  
|Table Update operation|Supported|Not supported between the adapter and the Oracle database. Supported between the client and adapter.|End-to-end node-value streaming is not supported because the values of LOB columns are buffered by ODP.NET, and then the update is performed. However, node-value streaming between the client and the adapter is possible for LOB columns if the client creates the message with a **BodyWriter**.|  
|Table Delete operation|Supported|Not supported between the adapter and the Oracle database. Supported between the client and adapter.|End-to-end node-value streaming is not supported because the values of LOB columns are buffered by ODP.NET and then the delete is performed. However, node-value streaming between the client and the adapter is possible for LOB columns if the client creates the message with a **BodyWriter**.|  
|Table ReadLOB operation|Supported|Supported|The ReadLOB operation is primarily designed to stream LOB data columns in the WCF service model. In the WCF channel model, if the client consumes the message using an **XmlReader** (by invoking the **GetReaderAtBodyContents** method on the response message), end-to-end node-value streaming occurs. This is because the adapter returns an **XmlReader** that supports **ReadValueChunk** calls for the ReadLOB response message. However, it is recommended that you do not use the ReadLOB operation from the WCF channel model. You can use a Select operation or a SQLEXECUTE operation instead.|  
|Table UpdateLOB operation|Supported|Supported|The adapter uses an **XmlDictionaryWriter** to consume the request message. If the client uses a **BodyWriter** to create the request message, end-to-end node-value streaming for LOB data occurs.|  
|SQLEXECUTE operation|Supported|Supported|The adapter uses a **BodyWriter** to create the response message.<br /><br /> If the client uses an **XmlDictionaryWriter** to consume the response message, end-to-end node-value streaming for the LOB data occurs.<br /><br /> End-to-end node-value streaming is not supported for the request message because the adapter must buffer all operands before it can invoke the operation on the Oracle database.|  
|Stored procedure and function operation|Supported|Supported|The adapter uses a **BodyWriter** to create the response message.<br /><br /> If the client uses an **XmlDictionaryWriter** to consume the response message, end-to-end node-value streaming for the LOB data occurs. (This means that streaming is supported for OUT and IN OUT procedure and function parameters in the response message.)<br /><br /> End-to-end node-value streaming is not supported for the request message because the adapter must buffer all operands before it can invoke the operation on the Oracle database.|  
|POLLINGSTMT operation|Supported|Supported|The adapter uses a **BodyWriter** to create the POLLINGSTMT request message. If the client consumes the message using an **XmlDictionaryWriter**, then node-value streaming for LOB columns occurs.|  
  
 For information about how to implement LOB data streaming in your code when you use the WCF channel model, see [Streaming Oracle Database LOB Data Types Using the WCF Channel Model](../../adapters-and-accelerators/adapter-oracle-database/streaming-oracle-database-lob-data-types-using-the-wcf-channel-model.md).  
  
## Streaming Support in the WCF Service Model  
 Serializing and deserializing between the XML representation of a message and the managed code object representation of that message requires writing and reading the entire message into memory. For this reason, neither node streaming nor node-value streaming is supported for most operations.  
  
 The only exception to this is the ReadLOB operation. This operation is implemented specifically to support end-to-end streaming for reading table and view LOB columns in the WCF service model.  
  
## Streaming Support in BizTalk Server  
 The following table provides detailed information about how streaming is supported in BizTalk Server. (All references to the "adapter" refer to the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]; the WCF-Custom adapter is always referred to by its full name in this table.)  
  
|Operation|Node Streaming|Node-Value Streaming|Description|  
|---------------|--------------------|---------------------------|-----------------|  
|Table Insert operation|Supported*|Not supported between the adapter and the Oracle database; however, data is streamed between BizTalk Server and the adapter.|End-to-end node-value streaming is not supported because the values of LOB columns are buffered by ODP.NET and then the insert is performed. However, node-value streaming between BizTalk Server and the adapter is supported for LOB data types because the WCF-Custom adapter creates the message with a **BodyWriter**.|  
|Table Select operation|Supported|Supported|The WCF-Custom adapter uses an **XmlDictionaryWriter** to consume the response message, so end-to-end node-value streaming for LOB types is supported.|  
|Table Update operation|Supported|Not supported between the adapter and the Oracle database; however, data is streamed between BizTalk Server and the adapter.|End-to-end node-value streaming is not supported because the values of LOB columns are buffered by ODP.NET and then the update is performed. However, node-value streaming between BizTalk Server and the adapter is supported for LOB data types because the WCF-Custom adapter creates the message with a **BodyWriter**.|  
|Table Delete operation|Supported|Not supported between the adapter and the Oracle database; however, data is streamed between BizTalk Server and the adapter.|End-to-end node-value streaming is not supported because the values of LOB columns are buffered by ODP.NET and then the delete is performed. However, node-value streaming between BizTalk Server and the adapter is supported for LOB data types because the WCF-Custom adapter creates the message with a **BodyWriter**.|  
|Table ReadLOB operation|The ReadLOB operation is not supported for BizTalk Server.|The ReadLOB operation is not supported for BizTalk Server.|The ReadLOB operation is not supported for BizTalk Server. Use the Select operation or a SQLEXECUTE operation instead.|  
|Table UpdateLOB operation|Supported|Supported|The WCF-Custom adapter uses a **BodyWriter** to create the request message, so end-to-end node-value streaming for LOB data types is supported.|  
|SQLEXECUTE operation|Supported|Supported|The WCF-Custom adapter uses an **XmlDictionaryWriter** to consume the response message, so end-to-end node-value streaming for LOB data types in the response message is supported.<br /><br /> End-to-end node-value streaming is not supported for the request message because the adapter must buffer all operands before it can invoke the operation on the Oracle database.|  
|Stored procedure and function operation|Supported|Supported|The WCF-Custom adapter uses an **XmlDictionaryWriter** to consume the response message, so end-to-end node-value streaming for LOB data types in the response message is supported. (This means that streaming is supported for OUT and IN OUT procedure and function parameters in the response message.)<br /><br /> End-to-end node-value streaming is not supported for the request message because the adapter must buffer all operands before it can invoke the operation on the Oracle database.|  
|POLLINGSTMT operation|Supported|Supported|The WCF-Custom adapter uses an **XmlDictionaryWriter** to consume the (inbound) request message, so end-to-end node-value streaming for LOB data types is supported.|  
  
## See Also  
[Develop your Oracle Database applications](../../adapters-and-accelerators/adapter-oracle-database/develop-your-oracle-database-applications.md)