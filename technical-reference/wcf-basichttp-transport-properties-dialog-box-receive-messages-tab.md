---
description: "Learn more about: WCF-BasicHttp Transport Properties Dialog Box, Receive, Messages Tab"
title: WCF-BasicHttp Transport Properties Dialog Box, Receive, Messages Tab
TOCTitle: WCF-BasicHttp Transport Properties Dialog Box, Receive, Messages Tab
ms:assetid: e0336005-0370-4b4b-8cde-40c69065c00c
ms:mtpsurl: https://msdn.microsoft.com/library/Bb259938(v=BTS.80)
ms:contentKeyID: 51532888
ms.date: 08/30/2017
ms.topic: ui-reference
mtps_version: v=BTS.80
f1_keywords:
- bts10.adapters.wcf-basichttp.transport.receive.messages
---

# WCF-BasicHttp Transport Properties Dialog Box, Receive, Messages Tab

 

Use the **Messages** tab to specify the data selection for the SOAP **Body** element.

| Use this | To do this |
|-------|--------------------|
| Envelope -- entire `<soap:Envelope>`        | Create the BizTalk message body part from the entire SOAP Envelope of an incoming message.<br />The default value is cleared.   |
| Body -- contents of `<soap:Body>` element   | Use the content of the SOAP Body element of an incoming message to create the BizTalk message body part. If the Body element has more than one child element, only the first element becomes the BizTalk message body part.<br />This is the default setting.   |
| Path -- content located by body path      | Use the body path expression in the Body path expression text box to create the BizTalk message body part. The body path expression is evaluated against the immediate child element of the SOAP Body element of an incoming message.<br />The default value is cleared.   |
| Body path expression                      | Type the body path expression to identify a specific part of an incoming message used to create the BizTalk message body part. This body path expression is evaluated against the immediate child element of the SOAP Body element of an incoming message. If this body path expression returns more than one node, only the first node is chosen for the BizTalk message body part. This property is required if the Path -- content located by body path option is selected.<br />Type: String<br />Minimum length: 0<br />Maximum length: 32767<br />The default is an empty string.                 |
| Node encoding                             | Specify the type of encoding that the WCF-BasicHttp receive adapter uses to decode the node identified by the body path expression in the Body path expression text box.<br />This property is required if the Path -- content located by body path option is selected. Valid values include the following:<br />Base64: Base64 encoding.<br />Hex: Hexadecimal encoding.<br />String: Text encoding - UTF-8<br />XML: The WCF adapters create the BizTalk message body with the outer XML of the node selected by the body path expression in the Body path expression text box.<br />The default is XML. |
| Body -- BizTalk response message body     | Use the BizTalk message body part to create the content of the SOAP Body element of an outgoing response message. This property is valid only for request-response receive locations.<br />This is the default setting.  |
| Template -- content specified by template | Use the template supplied in the XML text box to create the content of the SOAP Body element for an outgoing message. This property is valid only for request-response receive locations.<br />The default value is cleared.  |
| XML                                       | Type the XML-formatted template for the content of the SOAP Body element of an outgoing message. This property is required if the Template -- BizTalk response message body option is selected. This property is valid only for request-response receive locations.<br />Type: String<br />Minimum length: 0<br />Maximum length: 32767<br />The default is `bts-msg-body xmlns='http://www.microsoft.com/schemas/bts2007' encoding='xml'`.  |
| Suspend request message on failure        | Specify whether to suspend the request message that fails inbound processing due to a receive pipeline failure or a routing failure.<br />The default value is cleared.  |
| Include exception detail in faults        | Specify whether to return SOAP faults when an error occurs to easy debugging.<br />The default value is cleared.  |

## See Also

[How to Configure a WCF-BasicHttp Receive Location](https://msdn.microsoft.com/library/bb246064\(v=bts.80\))  
[Specifying the Message Body for the WCF Adapters](https://msdn.microsoft.com/library/bb226478\(v=bts.80\))
