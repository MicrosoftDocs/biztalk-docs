---
title: "Streaming and the SAP Adapter | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "streaming, support in WCF service model"
  - "streaming, node-value"
  - "streaming, node"
  - "streaming, support in BizTalk Server"
  - "streaming, and the SAP adapter"
  - "streaming, support in WCF channel model"
ms.assetid: 9fa1788b-f21b-4dec-be14-27dd8080a9d4
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Streaming and the SAP Adapter
The [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)] supports message streaming between itself and a client application. With the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] operations are invoked and responses are returned by exchanging SOAP messages. A SOAP message body is composed of XML nodes.  
  
 There are two kinds of message streaming that are supported by the adapter:  
  
-   **Node streaming**. In node streaming, a message can be streamed a node at a time between the client and the adapter. This means that, the entire value of a node is read into a buffer and then sent on to the receiver.  
  
-   **Node-value streaming**. In node-value streaming the actual value of the node can be streamed in chunks between the client and the adapter. Node-value streaming is useful for sending or receiving large IDOCs using the SendIdoc or the ReceiveIdoc operations. This is because the entire IDOC is contained in a single node. (As opposed to a strongly-typed Send or Receive operation in which the IDOC data is broken into many nodes).  
  
> [!IMPORTANT]
>  Node-value streaming is only supported between the adapter and a client application. The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] does not support end-to-end node-value streaming with the SAP system. This is because this functionality is not supported by the SAP client library.  
  
 Both of these streaming modes rely on support for node streaming and node-value streaming on messages in WCF. For this reason, streaming is tied closely to how messages are created and consumed both by the adapter and by a client application. One result of this is that support for message streaming is not the same across all programming models.  
  
 The sections in this topic provide:  
  
-   Fundamental background information about how message streaming is supported in WCF and how it is implemented by the adapter.  
  
-   Information about how message streaming is supported when you use the adapter in each programming model.  
  
## Streaming Fundamentals  
 The support for streaming implemented by the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] is a combination of:  
  
-   Message streaming support in WCF.  
  
-   Streaming support in the SAP client library.  
  
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
  
### Streaming Support in the SAP Client Library  
 The SAP client library does not support streaming. Therefore end-to-end node-value streaming is not supported by the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].  
  
### Internal Message Handling by the Adapter  
 The adapter supports streaming in the following manner:  
  
-   The adapter consumes the SendIdDoc request message received from the client by using a custom implementation of **XmlDictionaryWriter**. It consumes all other messages received from the client using an **XmlReader**.  
  
-   The adapter creates the ReceiveIdoc request message that it sends to the client by using a custom implementation of **XmlBodyWriter**. It creates all other messages that it sends to the client using an **XmlReader**.  
  
## Streaming Support in the WCF Channel Model  
 The following table provides detailed information about how streaming is supported in the WCF channel model.  
  
|Operation|Node Streaming|Node-Value Streaming|Description|  
|---------------|--------------------|---------------------------|-----------------|  
|Outbound RFC and BAPI operations (from the client to the adapter)|Not supported|Not supported||  
|Outbound tRFC operations (from the client to the adapter)|Not supported|Not supported||  
|IDOC Send operation (strongly typed)|Not supported|Not supported||  
|IDOC Receive operation (strongly typed)|Supported|Not supported||  
|SendIdoc operation (string)|Supported|Supported|The adapter uses an **XmlDictionaryWriter** to consume the request message. If the client creates the message with a **BodyWriter**, node-value streaming from the client to the adapter occurs.|  
|ReceiveIdoc operation (string)|Supported|Supported|The adapter uses a **BodyWriter** to create the request message. If the client consumes the message using an **XmlDictionaryWriter**, node-value streaming from the adapter to the client occurs.|  
|Inbound RFC operations|Not supported|Not supported||  
|Inbound tRFC operations|Not supported|Not supported||  
  
 For information about how to implement node-value streaming in your code to send and receive flat file (string) IDOCs using the SendIdoc and ReceiveIdoc operations, see [Stream Flat-File IDOCs in SAP using the WCF Channel Model](../../adapters-and-accelerators/adapter-sap/stream-flat-file-idocs-in-sap-using-the-wcf-channel-model.md).  
  
## Streaming Support in the WCF Service Model  
 Serializing and deserializing between the XML representation of a message and the managed code object representation of that message requires writing and reading the entire message into memory. For this reason, neither node streaming nor node-value streaming is supported from the WCF service model.  
  
## Streaming Support in BizTalk Server  
 The following table provides detailed information about how streaming is supported in BizTalk Server.  
  
|Operation|Node Streaming|Node-Value Streaming|Description|  
|---------------|--------------------|---------------------------|-----------------|  
|RFC and BAPI operations (from the client to the adapter)|Not supported|Not supported||  
|tRFC operations (from the client to the adapter)|Not supported|Not supported||  
|IDOC Send operation (strongly typed)|Not supported|Not supported||  
|IDOC Receive operation (strongly typed)|Supported|Not supported||  
|SendIdoc operation (string)|Supported|Supported|The WCF-Custom adapter uses a **BodyWriter** to create the request message, so node-value streaming is supported.|  
|ReceiveIdoc operation (string)|Supported|Supported|The WCF-Custom adapter uses an **XmlDictionaryWriter** to consume the request message, so node-value streaming is supported.|  
|Inbound RFC operations|Not supported|Not supported||  
|Inbound tRFC operations|Not supported|Not supported||  
  
## See Also  
[Develop your SAP applications](../../adapters-and-accelerators/adapter-sap/develop-your-sap-applications.md)