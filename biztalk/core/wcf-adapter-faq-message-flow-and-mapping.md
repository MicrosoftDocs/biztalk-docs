---
title: "WCF Adapter FAQ: Message Flow and Mapping | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 907e5c6a-a095-4b3a-9362-506832b6bc8c
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# WCF Adapter FAQ: Message Flow and Mapping
## What is the message flow within the WCF and BizTalk systems?  
 Here is a description of the flow of an incoming WCF message to BizTalk Server:  
  
1. A WCF message arrives at a receive location, and BizTalk Server instantiates a hosted WCF service.  
  
2. The WCF runtime instantiates the service’s channel stack and its channel listeners. A channel stack is a sequence of stages that handle differing processing tasks. Each channel stack consists of at least a transport channel, most often a message encoder, and zero or more protocol channels. The transport channel reads the incoming message stream upon arrival. It invokes an encoder to interpret the message and to produce a WCF Message object. At this point each protocol channel will have an opportunity to operate on the WCF message in order.  
  
3. The WCF message is received by a listener that forwards it through the configured WCF channel stack and dispatches it to the proper service instance. At this point the WCF message is converted (mapped) to a BizTalk message. Briefly stated, the WCF message headers are written into the BizTalk message context, and the WCF message body is written into the  BizTalk message body part. Mapping controls what part of the WCF message becomes the BizTalk message body: Envelope, body, or sub-element.  
  
4. Any pipeline components configured in the receive location processes the BizTalk message.  
  
5. The BizTalk message is stored in the MessageBox database.  
  
   Here is a description of the flow of an outgoing WCF message from BizTalk Server:  
  
6. A BizTalk message is received by a send port according to its subscription.  
  
7. Any pipeline components configured in the send port process the BizTalk message.  
  
8. A WCF channel stack is instantiated, and the BizTalk message is converted (mapped) into a WCF message based upon the service’s external visible contract.  
  
9. The WCF channel stack transmits the WCF message to the external WCF service.  
  
## How is a WCF message converted (mapped) into a BizTalk message?  
 In order to understand the mapping, we need to look at the structure of a WCF message and a BizTalk message.  
  
 A WCF message is modeled on the SOAP message structure and consists of message properties, message headers, and a single message body.  
  
- The **message properties** are Common Language Runtime (CLR) objects that are attached to the Message object. Properties are internal to the WCF stack and the user’s application at each end of the communication. They are never directly transferred between client and server.  
  
- **Message headers**, however, are transferred between client and server. There can be many headers on a message, but there is only one message body, and unlike the headers the message body is streamed. Both the message headers and the message body are defined as an XML Infoset.  
  
- The **body** of a WCF message is the main content of the message for which the properties and headers provide more information.  
  
  A BizTalk message has a different structure.  
  
- There is a single set of context properties on each message. Each context property consists of a namespace name/value pair. Context properties can be either promoted or written. If they are promoted, they can take part in the routing rules that execute within BizTalk Server.  
  
- The data of a message in BizTalk Server can consist of multiple streams. A BizTalk message is multipart because each stream can be read independently. One of the message parts is special and it is referred to as the body part.  
  
  Because the communication can sometimes be two-way, the WCF adapter allows the particular translation or mapping to be configured for both inbound and outbound directions of message exchange. This can be done for both the receive locations and send ports within BizTalk Server.  
  
  The BizTalk WCF adapters support a number of permutations of translating at run time between these two message structures. Mapping is controlled through the **Messages** tab in the **Transport Properties** dialog box for a WCF adapter. For example, the most obvious translation, and the default, is when the body of an inbound WCF message becomes the body of the BizTalk message. For more information about mapping modes, see [http://go.microsoft.com/fwlink/?LinkID=119792](http://go.microsoft.com/fwlink/?LinkID=119792).  
  
## How can you preserve the complete incoming WCF message inside the BizTalk message?  
 One of the inbound BizTalk message body options is the **Envelope** option. Choosing this option takes the entire SOAP message contained within the soap:Envelope element into the incoming BizTalk message body. The resulting BizTalk message contains the Envelope tags, all the headers, and the body.  
  
## How can you extract specific elements of the incoming WCF message into a BizTalk message, or map elements of an outgoing BizTalk message to an outgoing WCF message?  
 To map a section of a WCF or BizTalk message body, use the Path or Template option. This allows you to enter an XPath expression to extract specific parts of the message body. Full XPath syntax is not supported in this situation as the extraction is streamed and the reader must therefore always walk forward. This is why in the **Messages** tab it is called “Path – content located by body path” instead of “XPath – content located by body path.”  
  
 On the receive side, use a Path expression that dictates how data is to be read from the WCF message. For an inbound message, the specific element extracted by the Path statement gets substituted for the content of the BizTalk message. The adapter uses this Path expression to locate and extract the desired data for the BizTalk message.  
  
 On the send side, use a template to create a WCF message from the BizTalk message. The template option for outbound messages is designed to allow the exact opposite of the XPath option. In the WCF adapter configuration, the snippet of XML is used as the basis for the structure of the outbound message. The content of the BizTalk message is inserted at run time into this structure.  
  
 For an outgoing message, you must also choose the type of the element written by using the Node Encoding setting from XML, Base64, String, or Hexadecimal. This option is very useful when you want to extract a binary data stream contained in a WCF message. Using this feature instructs the WCF Adapter to use the ReadContextAsBase64 calls on the body Reader of the WCF Message. This call allows binary data to be read directly through the XmlReader API, so using this feature binary data can be moved directly from the WCF Transport into the BizTalk MessageBox database. By writing a path to the node containing the binary data you can pull it out and place it into the BizTalk message.  
  
## How do you access WCF message properties within an incoming WCF message?  
 To access properties within an incoming WCF message before it is transformed into a BizTalk message, you can use a custom WCF channel component or a service model extensibility point with a WCF behavior. For example, an **IDispatchMessageInspector** object. The BizTalk WCF-Custom and WCF-CustomIsolated adapters provide a simple way for your application to plug into the power of WCF behaviors using the **Behavior** tab in the **Transport Properties** dialog for those adapters.  
  
 To allow the properties of a WCF message to be available to the WCF adapter, those properties first have to be written into the message body or header as content. The headers are copied into the BizTalk message context automatically for you. If you want a property value promoted, you can use a custom BizTalk pipeline component to promote the WCF message property into the BizTalk message context from within the **IComponent:Execute** method. Using custom WCF behaviors with the WCF custom adapters allows you to take advantage of both WCF and BizTalk extensibility to make your solution more powerful and flexible. The WCF adapter allows you to combine existing BizTalk and WCF extensibilities to solve your problem.  
  
 The good news is that there is a shortcut in the WCF adapter for this common property case. Rather than writing to both extensibility stories, you can simply have the WCF extension create a new “well known” property that is understood by the WCF adapter.  
  
 In order to write or promote SOAP header values into the BizTalk message context, the WCF message must contain a collection of value pairs that consist of property names and namespaces. This allows the WCF adapters to recognize that the header values are to be written or promoted.  
  
 A WCF adapter expects the following message properties in the WCF messages for writing or promoting SOAP header values to the BizTalk message context:  
  
-   To promote the SOAP header values to the BizTalk message context, WCF adapters are looking for the pair of key **http://schemas.microsoft.com/BizTalk/2006/01/Adapters/WCF-properties/Promote** and value **List<KeyValuePair\<XmlQualifiedName, object\>>**. Using this pair, WCF adapters take the namespace, name, and value from the **XmlQualifiedName** object and use them for promoting the header values.  
  
-   To write, but not promote, the SOAP header values into the BizTalk message context, WCF adapters are looking for the pair of key **http://schemas.microsoft.com/BizTalk/2006/01/Adapters/WCF-properties/WriteToContext** and value **List<KeyValuePair\<XmlQualifiedName, object\>>.** Using this pair, WCF adapters write the values to the message context.  
  
> [!NOTE]
>  Promoted properties must also be specified in a BizTalk property schema in order to be accepted by the BizTalk runtime.  
  
## You have an existing orchestration (or send port, etc.) that expects a BizTalk multipart message. How can you get a multipart message in the WCF scenario?  
 A BizTalk multipart message is composed of one or more message parts. However, WCF has no concept of a multipart message. Because WCF does not use multipart messages, the BizTalk WCF adapters also do not use them. The problem is that you may have an existing BizTalk orchestration or pipeline that is written to produce or consume multipart messages.  
  
 If you need to get a multipart message into BizTalk Server by using an incoming WCF message and the WCF adapters, render your multipart data as XML in your WCF message. Develop a custom BizTalk pipeline component to process the incoming XML stream (WCF message) and create the appropriate BizTalk multipart message for your application. These steps can be done in reverse for the Send side if required.