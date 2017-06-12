---
title: "WCF-NetMsmq Transport Properties Dialog Box, Send, Messages Tab | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.adapters.wcf-netmsmq.transport.send.messages"
helpviewer_keywords: 
  - "WCF-NetMsmq adapters, properties"
  - "messages, WCF-NetMsmq adapters"
  - "properties, WCF-NetMsmq adapters"
  - "WCF-NetMsmq adapters, messages"
ms.assetid: c2636e50-992f-4576-a013-992318c28e75
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# WCF-NetMsmq Transport Properties Dialog Box, Send, Messages Tab
Use the **Messages** tab to specify the data selection for the SOAP **Body** element.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Body -- BizTalk request message body**|Use the BizTalk message body part to create the content of the SOAP **Body** element for an outgoing message.<br /><br /> This is the default setting.|  
|**Template -- content specified by template**|Use the template supplied in the **XML** text box to create the content of the SOAP **Body** element for an outgoing message.<br /><br /> The default value is cleared.|  
|**XML**|Type the XML-formatted template for the content of the SOAP **Body** element of an outgoing message. This property is required if the **Template -- content specified by template** option is selected.<br /><br /> Type: String<br /><br /> Minimum length: 0<br /><br /> Maximum length: 32767<br /><br /> The default is  <bts-msg-body<br /><br /> xmlns="http://www.microsoft.com/schemas/bts2007" encoding="xml"/>|  
  
## See Also  
 [How to Configure a WCF-NetMsmq Send Port](../core/how-to-configure-a-wcf-netmsmq-send-port.md)   
 [Specifying the Message Body for the WCF Adapters](../core/specifying-the-message-body-for-the-wcf-adapters.md)