---
title: "Overview of the WCF channel model with the SAP adapter | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "WCF channel model, overview"
  - "WCF channel model, creating messages for the SAP adapter"
ms.assetid: 6192d637-efac-4580-8880-b5bae9d16f31
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Overview of the WCF channel model with the SAP adapter
To invoke RFCs, tRFCs, or BAPIs on an SAP system, or to send IDOCS to an SAP system, your code acts as a WCF client and sends outbound operations to the adapter. In the WCF channel model, your code invokes operations on the adapter by sending a request message over a channel.  
  
 To act as a tRFC or RFC server to an SAP system, your code behaves as a WCF service. That is, the adapter invokes an inbound operation on your code—for example, an RFC or the ReceiveIdoc operation (to receive an IDOC in string format from an SAP system). In this scenario, your code receives a request message for the operation over a channel from the adapter.  
  
 The topics in this section provide an overview of using the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] with the WCF channel model.  
  
## WCF Channel Model Overview  
 Clients and services communicate by exchanging SOAP messages. The WCF channel model is a low-level abstraction of this message exchange. It provides interfaces and types that enable you to send and receive messages by using a layered protocol stack called a channel stack. Each layer of the stack is composed of a channel, and each channel is created from a WCF binding. At the lowest layer is the transport channel. The transport channel implements the underlying transport mechanism between a service and a client and presents each message to the higher layers (and ultimately the consuming application) as a **System.ServiceModel.Message**. The WCF **Message** class is an abstraction of a SOAP message. WCF provides several channel interfaces, called channel shapes, that model the basic SOAP message exchange patterns, such as request-reply or one-way. A WCF transport binding provides an implementation of one or more channel shapes that higher layers can use to send and receive messages. For more information about the WCF channel model, see [Channel Model Overview](https://msdn.microsoft.com/library/ms729840.aspx).
  
 The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] is a WCF custom transport binding that exposes an SAP system as a WCF service.  
  
## Supported Channel Shapes for the SAP Adapter  
 The adapter implements the following WCF channel shapes:  
  
- **IRequestChannel** (**System.ServiceModel.Channels.IRequestChannel**). The **IRequestChannel** interface implements the client side of a request-reply message exchange. You can use an **IRequestChannel** to perform operations for which you want to consume a response, for example to invoke an RFC on the SAP system that returns data.  
  
- **IOutputChannel** (**System.ServiceModel.Channels.IOutputChannel**). This shape implements the client side of a one-way message exchange. You can use an **IOutputChannel** to invoke an operation for which you do not need to consume a response, for example to invoke an RFC on the SAP system that does not return any data.  
  
- **IReplyChannel** (**System.ServiceModel.Channels.IReplyChannel**). This shape implements the service side of a request-reply message exchange. You can use an **IReplyChannel** to implement an RFC or tRFC server or to receive IDOCs from a SAP system.  
  
  Like any WCF binding, the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] uses a factory pattern to provide channels to application code. You use a **Microsoft.Adapters.SAPBinding** object to create instances of:  
  
- **System.ServiceModel.ChannelFactory\<IRequestChannel\>** to provide **IRequestChannel** channels you can use to invoke request-response operations on the adapter.  
  
- **System.ServiceModel.ChannelFactory\<IOutputChannel\>** to provide **IOutputChannel** channels you can use to invoke one-way operations on the adapter.  
  
- **System.ServiceModel.IChannelListener\<IReplyChannel\>** to provide **IReplyChannel** channels you can use to receive request-response operations from the adapter.  
  
## Creating Messages for the SAP Adapter in the WCF Channel Model  
 In WCF the **System.ServiceModel.Channels.Message** class provides an in memory representation of a SOAP message. You create a **Message** instance by invoking the static **Message.Create** method.  
  
 There are two important parts to the SOAP message that you must specify when you construct a **Message** instance to send to the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].  
  
- The message action is a string that is part of the SOAP message header. The message action identifies the operation that should be invoked on [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]. The following shows the message action that is specified to invoke the SD_RFC_CUSTOMER_GET RFC on an SAP system: `http://Microsoft.LobServices.Sap/2007/03/Rfc/SD_RFC_CUSTOMER_GET`.  
  
- The message body contains the parameter data for the operation. The message body is composed of well-formed XML that corresponds to the message schema expected by the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] for the requested operation. The following message body contains the parameters for the SD_RFC_CUSTOMER_GET RFC on an SAP system.  
  
  ```  
  <SD_RFC_CUSTOMER_GET xmlns=\"http://Microsoft.LobServices.Sap/2007/03/Rfc/\"> <KUNNR i:nil=\"true\" xmlns:i=\"http://www.w3.org/2001/XMLSchema-instance\"> </KUNNR> <NAME1>AB*</NAME1> <CUSTOMER_T> </CUSTOMER_T> </SD_RFC_CUSTOMER_GET>  
  ```  
  
  For information about the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] message schemas and message actions for operations, see [Messages and Message Schemas for BizTalk Adapter for mySAP Business Suite](../../adapters-and-accelerators/adapter-sap/messages-and-message-schemas-for-biztalk-adapter-for-mysap-business-suite.md).  
  
  The **Message.Create** method is overloaded and offers many different options for providing the message body. The following code shows how to create a **Message** instance by using an **System.Xml.XmlReader** to supply the message body. In this code, the message body is read from a string constant.  
  
```  
//create an XML message to send to the SAP system  
//We are invoking the SD_RFC_CUSTOMER_GET RFC.  
//The XML below specifies that we want to search for customers with names starting with "AB"  
string inputXml = "<SD_RFC_CUSTOMER_GET xmlns=\"http://Microsoft.LobServices.Sap/2007/03/Rfc/\"> <KUNNR i:nil=\"true\" xmlns:i=\"http://www.w3.org/2001/XMLSchema-instance\"> </KUNNR> <NAME1>AB*</NAME1> <CUSTOMER_T> </CUSTOMER_T> </SD_RFC_CUSTOMER_GET>";  
  
//create an XML reader from the input XML  
XmlReader reader = XmlReader.Create(new MemoryStream(Encoding.Default.GetBytes(inputXml)));  
  
//create a WCF message from the XML reader  
Message inputMessge = Message.CreateMessage(MessageVersion.Soap11, "http://Microsoft.LobServices.Sap/2007/03/Rfc/SD_RFC_CUSTOMER_GET", reader);  
```  
  
> [!IMPORTANT]
>  You must provide a message action in your **Message** instance. This is typically done when the **Message** instance is created.  
  
## Streaming Support on the SAP Adapter in the WCF Channel Model  
 How you create and consume the messages that you exchange with the SAP adapter determines how the message is streamed between your code and the adapter.  
  
### Node streaming  
 Node streaming is the only level of streaming supported for all operations except the SendIdoc and ReceiveIdoc operations.  
  
 To perform node streaming for a message, you:  
  
-   Create an outbound message using an **XmlReader** to supply the message body.  
  
-   Consume an inbound message using an **XmlReader**. You get the reader by calling the **GetReaderAtBodyContents** method on the inbound **Message**.  
  
### Node-value Streaming  
 Because the SendIdoc and ReceiveIdoc operations contain the IDOC data in a string under a single XML node (\<idocData\>), the adapter supports node-value streaming on these operations.  
  
 To perform node-value streaming for these operations, you can:  
  
- Create the SendIdoc request message (outbound) using a **BodyWriter** that implements node-value streaming to supply the message body.  
  
- Consume the ReceiveIdoc request message (inbound) by calling the **WriteBodyContents** method on the message with an **XmlDictionaryWriter** that implements node-value streaming.  
  
  For more information about streaming flat file (string) IDOCs using the WCF channel model, see [Streaming Flat-File IDOCs in SAP using the WCF Channel Model](../../adapters-and-accelerators/adapter-sap/stream-flat-file-idocs-in-sap-using-the-wcf-channel-model.md).  
  
## See Also  
[Develop applications using the WCF Channel Model](../../adapters-and-accelerators/adapter-sap/develop-sap-applications-using-the-wcf-channel-model.md)