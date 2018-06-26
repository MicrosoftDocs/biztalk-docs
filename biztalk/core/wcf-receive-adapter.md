---
title: "WCF Receive Adapter | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "messages, headers"
  - "receive adapters, Web service headers"
  - "SOAP messages, extracting information"
  - "SOAP messages, WCF adapters"
  - "WCF adapters, receive adapters"
  - "messages, SOAP"
  - "receive adapters, WCF adapters"
  - "Web services, headers"
  - "headers [messages]"
  - "SOAP messages, receive adapters"
ms.assetid: 6b3d5df1-5d9d-4240-a98f-ea29c3272e38
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# WCF Receive Adapter
The WCF receive adapter enables you to receive WCF service requests.  
  
## Extracting the BizTalk Message Body from the SOAP Message  
 The inbound BizTalk message body can be extracted from the SOAP message by using one of the following options:  
  
- Extract the content of the SOAP Body element  
  
- Extract the entire SOAP envelope  
  
- Extract the content of the element inside the SOAP envelope by using an XPath expression  
  
  You can configure these options in the transport properties dialog box.  
  
#### Extract the Content of the SOAP Body Element  
 When this option is selected, the inner content of the SOAP Body element is read from the SOAP message and placed into the body part of the BizTalk message.  
  
#### Extract the Entire SOAP Envelope  
 When this option is selected, the entire SOAP envelope including the tag is placed into the body part of the BizTalk message.  
  
#### Extract the Content of the Element by Using an XPath Expression  
 When this option is selected, the inner content of the element inside the SOAP Body element that is located by the XPath expression is placed into the body part of the BizTalk message. The rest of the data in the Body element is ignored. You also need to specify the node encoding—for example, XML, Base64, Hex, or String encoding.  
  
> [!NOTE]
>  When the XML encoding is selected, the outer content of the element is located by the XPath expression and placed into the body part.  
  
## Handling Web Services Headers  
 The receive adapter promotes a subset of the standard Web services headers onto the BizTalk message context to enable easy access and routing based on values of those headers. The following table lists the properties that will be saved onto the message context by the receive adapter. The properties are defined under the following namespaces: http://www.w3.org/2005/addressing and http://schemas.microsoft.com/BizTalk/2006/Adapters/WCF-properties.  
  
|Header|BizTalk property name|Is promoted?|  
|------------|---------------------------|------------------|  
|Action|Action|Yes|  
|MessageID|MessageID|No|  
|To|To|Yes|  
|ReplyTo/Address|ReplyTo|Yes|  
|From/Address|From|Yes|  
|Sequence/Identifier|SequenceId|Yes|  
|Sequence/MessageNumber|SequenceNumber|Yes|  
|Sequence/LastMessage|SequenceLastMessage|Yes|  
|\<soap:Header\>|InboundHeaders|No|  
  
## See Also  
 [Specifying the Message Body for the WCF Adapters](../core/specifying-the-message-body-for-the-wcf-adapters.md)   
 [WCF Send Adapter](../core/wcf-send-adapter.md)   
 [What Are the WCF Adapters?](../core/what-are-the-wcf-adapters.md)