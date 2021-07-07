---
description: "Learn more about: WCF-BasicHttp Transport Properties Dialog Box, Send, Messages Tab"
title: WCF-BasicHttp Transport Properties Dialog Box, Send, Messages Tab
TOCTitle: WCF-BasicHttp Transport Properties Dialog Box, Send, Messages Tab
ms:assetid: e1c56ff3-819c-47ae-babe-482a9d5b1479
ms:mtpsurl: https://msdn.microsoft.com/library/Bb259940(v=BTS.80)
ms:contentKeyID: 51532898
ms.date: 08/30/2017
mtps_version: v=BTS.80
f1_keywords:
- bts10.adapters.wcf-basichttp.transport.send.messages
---

# WCF-BasicHttp Transport Properties Dialog Box, Send, Messages Tab

 

Use the **Messages** tab to specify the data selection for the SOAP **Body** element.

| Use this | To do this |
|---------|-----|
| Body -- BizTalk request message body      | Use the BizTalk message body part to create the content of the SOAP Body element for an outgoing message.<br />This is the default setting. |
| Template -- content specified by template | Use the template supplied in the XML text box to create the content of the SOAP Body element for an outgoing message.<br />The default value is cleared. |
| XML | Type the XML-formatted template for the content of the SOAP Body element of an outgoing message. This property is required if the Template -- BizTalk response message body option is selected.<br />Type: String<br />Minimum length: 0<br />Maximum length: 32767<br />The default is `bts-msg-body xmlns="http://www.microsoft.com/schemas/bts2007" encoding="xml"`. |
| Envelope -- entire `<soap:Envelope>`        | Create the BizTalk message body part from the entire SOAP Envelope of an incoming message. This property is valid only for solicit-response ports.<br />The default value is cleared.  |
| Body -- contents of `<soap:Body>` element   | Use the content of the SOAP Body element of an incoming message to create the BizTalk message body part. If the Body element has more than one child element, only the first element becomes the BizTalk message body part. This property is valid only for solicit-response ports.<br />This is the default setting. |
| Path -- content located by body path      | Use the body path expression in the Body path expression text box to create the BizTalk message body part. The body path expression is evaluated against the immediate child element of the SOAP Body element of an incoming message. This property is valid only for solicit-response ports.<br />The default value is cleared. |
| Body path expression                      | Type the body path expression to identify a specific part of an incoming message used to create the BizTalk message body part. This body path expression is evaluated against the immediate child element of the SOAP Body node of an incoming message. If this body path expression returns more than one node, only the first node is chosen for the BizTalk message body part. This property is required if the Path -- content located by body path option is selected. This property is valid only for solicit-response ports.<br />Type: String<br />Minimum length: 0<br />Maximum length: 32767<br />The default is an empty string.                    |
| Node encoding                             | Specify the type of encoding that the WCF-BasicHttp send adapter uses to decode for the node identified by the body path expression in the Body path expression text box. This property is required if the Path -- content located by body path option is selected. This property is valid only for solicit-response ports. Valid values include the following:<br />Base64: Base64 encoding.
Hex: Hexadecimal encoding.<br />String: Text encoding - UTF-8<br />XML: The WCF adapters create the BizTalk message body with the outer XML of the node selected by the body path expression in the Body path expression text box.<br />The default is XML. |
| Propagate fault message                   | Select this check box to route the message that fails outbound processing to a subscribing application (such as another receive port or orchestration schedule). Clear the check box to suspend failed messages and generate a negative acknowledgment (NACK). This property is valid only for solicit-response ports.<br />The default value is selected. |

## See Also

[How to Configure a WCF-BasicHttp Send Port](https://msdn.microsoft.com/library/bb226467\(v=bts.80\))  
[Specifying the Message Body for the WCF Adapters](https://msdn.microsoft.com/library/bb226478\(v=bts.80\))
