---
title: "WCF-Custom Transport Properties Dialog Box, Send, Messages Tab | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.adapters.wcf-custom.transport.send.messages"
helpviewer_keywords: 
  - "WCF-Custom adapters, messages"
  - "WCF-Custom adapters, properties"
  - "properties, WCF-Custom adapters"
  - "messages, WCF-Custom adapters"
ms.assetid: a12fdf10-4955-4596-b8d5-888a529276a8
caps.latest.revision: 11
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# WCF-Custom Transport Properties Dialog Box, Send, Messages Tab
Use the **Messages** tab to specify the data selection for the SOAP **Body** element.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Body -- BizTalk response message body**|Use the BizTalk message body part to create the content of the SOAP **Body** element for an outgoing message.<br /><br /> This is the default setting.|  
|**Template -- content specified by template**|Use the template supplied in the **XML** text box to create the content of the SOAP **Body** element for an outgoing message.<br /><br /> The default value is cleared.|  
|**XML**|Type the XML-formatted template for the content of the SOAP **Body** element of an outgoing message. This property is required if the **Template -- BizTalk response message body** option is selected.<br /><br /> Type: String<br /><br /> Minimum length: 0<br /><br /> Maximum length: 32767<br /><br /> The default is an empty string.|  
|**Envelope -- entire \<soap:Envelope>**|Create the BizTalk message body part from the entire SOAP **Envelope** of an incoming message. This property is valid only for solicit-response ports.<br /><br /> The default value is cleared.|  
|**Body -- contents of \<soap:Body> element**|Use the content of the SOAP **Body** element of an incoming message to create the BizTalk message body part. If the **Body** element has more than one child element, only the first element becomes the BizTalk message body part. This property is valid only for solicit-response ports.<br /><br /> This is the default setting.|  
|**Path -- content located by body path**|Use the body path expression in the **Body path expression** text box to create the BizTalk message body part. The body path expression is evaluated against the immediate child element of the SOAP **Body** element of an incoming message. This property is valid only for solicit-response ports.<br /><br /> The default value is cleared.|  
|**Body path expression**|Type the body path expression to identify a specific part of an incoming message used to create the BizTalk message body part. This body path expression is evaluated against the immediate child element of the SOAP **Body** node of an incoming message. If this body path expression returns more than one node, only the first node is chosen for the BizTalk message body part. This property is required if the **Path -- content located by body path** option is selected. This property is valid only for solicit-response ports.<br /><br /> Type: String<br /><br /> Minimum length: 0<br /><br /> Maximum length: 32767<br /><br /> The default is an empty string.|  
|**Node encoding**|Specify the type of encoding that the WCF-Custom send adapter uses to decode for the node identified by the body path expression in the **Body path expression** text box. This property is required if the **Path -- content located by body path** option is selected. This property is valid only for solicit-response ports. Valid values include the following:<br /><br /> -   **Base64**: Base64 encoding.<br />-   **Hex**: Hexadecimal encoding.<br />-   **String**: Text encoding - UTF-8<br />-   **XML**: The WCF adapters create the BizTalk message body with the outer XML of the node selected by the body path expression in the **Body path expression** text box.<br /><br /> The default is **XML**.|  
|**Propagate fault message**|Select this check box to route the message that fails outbound processing to a subscribing application (such as another receive port or orchestration schedule). Clear the check box to suspend failed messages and generate a negative acknowledgment (NACK). This property is valid only for solicit-response ports.<br /><br /> The default value is selected.|  
|**Use Transaction**|Select this checkbox to send messages under transaction scope. The default value is clear.<br /><br /> You can also specify the Isolation Level for the transaction using the dropdown box.<br /><br /> Valid values for Isolation Level include the following:<br /><br /> 1.  Serializable<br />2.  RepeatableRead<br />3.  ReadCommitted<br />4.  ReadUncommitted<br />5.  Snapshot<br />6.  Chaos<br />7.  Unspecified<br /><br /> The default value for transaction Isolation Level is 'Serializable'.|  
  
## See Also  
 [How to Configure a WCF-Custom Send Port](../core/how-to-configure-a-wcf-custom-send-port.md)   
 [Specifying the Message Body for the WCF Adapters](../core/specifying-the-message-body-for-the-wcf-adapters.md)