---
title: "Overview of the WCF channel model with the Oracle E-Business Suite adapter | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3afd2a97-5734-4c25-87a3-702d8461898b
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Overview of the WCF channel model with the Oracle E-Business Suite adapter
To invoke operations on the [!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)], your code acts as a WCF client and sends outbound operations to the adapter. In the WCF channel model, your code invokes operations on the adapter by sending a request message over a channel.  
  
 To invoke inbound operations, such as receiving polling-based data-changed messages using the **Poll** operation provided by the adapter, your code acts as a WCF service and receives the inbound operation from the adapter. In other words, your code receives a request message from the adapter over a channel.  
  
 The topics in this section provide an overview of using the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] with the WCF channel model.  
  
## WCF Channel Model Overview  
 Clients and services communicate by exchanging SOAP messages. The WCF channel model is a low-level abstraction of this message exchange. It provides interfaces and types that enable you to send and receive messages by using a layered protocol stack called a channel stack. Each layer of the stack is composed of a channel, and each channel is created from a WCF binding. At the lowest layer is the transport channel. The transport channel implements the underlying transport mechanism between a service and a client and presents each message to the higher layers (and ultimately the consuming application) as a **System.ServiceModel.Message**. The WCF **Message** class is an abstraction of a SOAP message. WCF provides several channel interfaces, called channel shapes, that model the basic SOAP message exchange patterns, such as request-reply or one-way. A WCF transport binding provides an implementation of one or more channel shapes that higher layers can use to send and receive messages. For more information about the WCF channel model, see "Channel Model Overview" at [http://go.microsoft.com/fwlink/?LinkId=82614](http://go.microsoft.com/fwlink/?LinkId=82614).  
  
 The [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] is a WCF custom transport binding that exposes an Oracle E-Business Suite artifact as a WCF service.  
  
## Supported Channel Shapes for the Oracle E-Business Suite Adapter  
 The adapter implements the following WCF channel shapes:  
  
- **IRequestChannel** (**System.ServiceModel.Channels.IRequestChannel**). The **IRequestChannel** interface implements the client side of a request-reply message exchange. You can use an **IRequestChannel** to perform operations for which you want to consume a response, for example to perform a SELECT query on an interface table.  
  
- **IOutputChannel** (**System.ServiceModel.Channels.IOutputChannel**). This shape implements the client side of a one-way message exchange. You can use an **IOutputChannel** to invoke an operation for which you do not need to consume a response, for example to call a procedure that has no OUT parameters.  
  
  > [!IMPORTANT]
  >  All underlying calls by the adapter to the Oracle client are synchronous. This includes calls to the Oracle client that are the result of operations invoked over an **IOutputChannel**. When you use an **IOutputChannel**, the adapter discards the response received from the Oracle client.  
  
- **IInputChannel** (**System.ServiceModel.Channels.IInputChannel**). This shape implements the service side of a one-way message exchange. You use an **IInputChannel** to receive inbound messages from the adapter.  
  
  Like any WCF binding, the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] uses a factory pattern to provide channels to application code. You use a **Microsoft.Adapters.OracleEBSBinding** object to create instances of:  
  
- **System.ServiceModel.ChannelFactory\<IRequestChannel\>** to provide **IRequestChannel** channels you can use to invoke request-response operations on the adapter.  
  
- **System.ServiceModel.ChannelFactory\<IOutputChannel\>** to provide **IOutputChannel** channels you can use to invoke one-way operations on the adapter.  
  
- **System.ServiceModel.IChannelListener\<IInputChannel\>** to provide **IInputChannel** channels you can use to receive inbound messages from the adapter.  
  
### Creating Messages for the Oracle Enterprise Business Solution in the WCF Channel Model  
 In WCF the **System.ServiceModel.Channels.Message** class provides an in memory representation of a SOAP message. You create a **Message** instance by invoking the static **Message.Create** method.  
  
 There are two important parts to the SOAP message that you must specify when you create a **Message** instance to send to the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)].  
  
- The message action is a string that is part of the SOAP message header. The message action identifies the operation that should be invoked on the Oracle E-Business Suite. The following shows the message action specified to invoke the **Customer Interface** concurrent program under the **Receivables** application in Oracle E-Business Suite: `ConcurrentPrograms/AR/RACUST`.  
  
- The message body contains the parameter data for the operation. The message body is composed of well-formed XML that corresponds to the message schema expected by the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] for the requested operation. The following message body specifies a request message to invoke the **Customer Interface** concurrent program.  
  
  ```  
  <RACUST xmlns="http://schemas.microsoft.com/OracleEBS/2008/05/ConcurrentPrograms/AR">  
    <Description>Customer Interface Program</Description>  
    <StartTime></StartTime>  
    <CREATE_RECIPROCAL_CUSTOMER>Yes</CREATE_RECIPROCAL_CUSTOMER>  
    <ORG_ID>203</ORG_ID>  
  </RACUST>  
  
  ```  
  
  For information about the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] message schemas and message actions for operations, see [Messages and Message Schemas for BizTalk Adapter for Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/messages-and-message-schemas-for-biztalk-adapter-for-oracle-e-business-suite.md).  
  
  The **Create** method is overloaded and offers many different options for providing the message body. The following code shows how to create a **Message** instance by using an **XmlReader** to supply the message body. In this code, the message body is read from a file.  
  
```  
XmlReader readerIn = XmlReader.Create("ConcProgRequest.xml");  
Message messageIn = Message.CreateMessage(MessageVersion.Default,  
    "ConcurrentPrograms/AR/RACUST",  
    readerIn);  
```  
  
 where, ConProgRequest.xml contains the request message.  
  
> [!IMPORTANT]
>  You must provide a message action in your **Message** instance. This is typically done when the **Message** instance is created.  
  
## See Also  
 [Develop Oracle E-Business Suite applications using the WCF Channel Model](../../adapters-and-accelerators/adapter-oracle-ebs/develop-oracle-e-business-suite-applications-using-the-wcf-channel-model.md)