---
description: "Learn more about: WCF-NetMsmq Transport Properties Dialog Box, Send, Messages Tab"
title: WCF-NetMsmq Transport Properties Dialog Box, Send, Messages Tab
TOCTitle: WCF-NetMsmq Transport Properties Dialog Box, Send, Messages Tab
ms:assetid: c2636e50-992f-4576-a013-992318c28e75
ms:mtpsurl: https://msdn.microsoft.com/library/Bb226510(v=BTS.80)
ms:contentKeyID: 51531087
ms.date: 08/30/2017
ms.topic: ui-reference
mtps_version: v=BTS.80
f1_keywords:
- bts10.adapters.wcf-netmsmq.transport.send.messages
---

# WCF-NetMsmq Transport Properties Dialog Box, Send, Messages Tab

 

Use the **Messages** tab to specify the data selection for the SOAP **Body** element.

| Use this | To do this |
|------------|-------------|
| Body -- BizTalk request message body      | Use the BizTalk message body part to create the content of the SOAP Body element for an outgoing message.<br />This is the default setting. |
| Template -- content specified by template | Use the template supplied in the XML text box to create the content of the SOAP Body element for an outgoing message.<br />The default value is cleared. |
| XML                                       | Type the XML-formatted template for the content of the SOAP Body element of an outgoing message. This property is required if the Template -- content specified by template option is selected.<br />Type: String<br />Minimum length: 0<br />Maximum length: 32767<br />The default is `bts-msg-body xmlns="http://www.microsoft.com/schemas/bts2007" encoding="xml"` |

## See Also

[How to Configure a WCF-NetMsmq Send Port](https://msdn.microsoft.com/library/bb245965\(v=bts.80\))  
[Specifying the Message Body for the WCF Adapters](https://msdn.microsoft.com/library/bb226478\(v=bts.80\))
