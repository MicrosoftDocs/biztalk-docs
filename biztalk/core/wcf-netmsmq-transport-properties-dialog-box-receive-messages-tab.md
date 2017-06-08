---
title: "WCF-NetMsmq Transport Properties Dialog Box, Receive, Messages Tab | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.adapters.wcf-netmsmq.transport.receive.messages"
helpviewer_keywords: 
  - "WCF-NetMsmq adapters, properties"
  - "messages, WCF-NetMsmq adapters"
  - "properties, WCF-NetMsmq adapters"
  - "WCF-NetMsmq adapters, messages"
ms.assetid: 95834c20-4d49-44a4-99c1-410f086135a7
caps.latest.revision: 14
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# WCF-NetMsmq Transport Properties Dialog Box, Receive, Messages Tab
Use the **Messages** tab to specify the data selection for the SOAP **Body** element.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Envelope -- entire \<soap:Envelope>**|Create the BizTalk message body part from the entire SOAP **Envelope** of an incoming message.<br /><br /> The default value is cleared.|  
|**Body -- contents of \<soap:Body> element**|Use the content of the SOAP **Body** element of an incoming message to create the BizTalk message body part. If the **Body** element has more than one child element, only the first element becomes the BizTalk message body part.<br /><br /> This is the default setting.|  
|**Path -- content located by body path**|Use the body path expression in the **Body path expression** text box to create the BizTalk message body part. The body path expression is evaluated against the immediate child element of the SOAP **Body** element of an incoming message.<br /><br /> The default value is cleared.|  
|**Body path expression**|Type the body path expression to identify a specific part of an incoming message used to create the BizTalk message body part. This body path expression is evaluated against the immediate child element of the SOAP **Body** element of an incoming message. If this body path expression returns more than one node, only the first node is chosen for the BizTalk message body part. This property is required if the **Path -- content located by body path** option is selected.<br /><br /> Type: String<br /><br /> Minimum length: 0<br /><br /> Maximum length: 32767<br /><br /> The default is an empty string.|  
|**Node encoding**|Specify the type of encoding that the WCF-NetMsmq receive adapter uses to decode for the node identified by the body path expression in the **Body path expression** text box. This property is required if the **Path -- content located by body path** option is selected. Valid values include the following:<br /><br /> -   **Base64**: Base64 encoding.<br />-   **Hex**: Hexadecimal encoding.<br />-   **String**: Text encoding - UTF-8<br />-   **XML**: The WCF adapters create the BizTalk message body with the outer XML of the node selected by the body path expression in the **Body path expression** text box.<br /><br /> The default is **XML**.|  
|**Disable location on failure**|Specify whether to disable the receive location that fails inbound processing due to a receive pipeline failure or a routing failure.<br /><br /> The default value is cleared.|  
|**Suspend request message on failure**|Specify whether to suspend the request message that fails inbound processing due to a receive pipeline failure or a routing failure.<br /><br /> The default value is selected.|  
  
## See Also  
 [How to Configure a WCF-NetMsmq Receive Location](../core/how-to-configure-a-wcf-netmsmq-receive-location.md)   
 [Specifying the Message Body for the WCF Adapters](../core/specifying-the-message-body-for-the-wcf-adapters.md)