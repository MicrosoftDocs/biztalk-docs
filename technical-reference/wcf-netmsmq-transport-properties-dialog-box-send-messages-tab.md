---
description: "Learn more about: WCF-NetMsmq Transport Properties Dialog Box, Send, Messages Tab"
title: WCF-NetMsmq Transport Properties Dialog Box, Send, Messages Tab
TOCTitle: WCF-NetMsmq Transport Properties Dialog Box, Send, Messages Tab
ms:assetid: c2636e50-992f-4576-a013-992318c28e75
ms:mtpsurl: https://msdn.microsoft.com/library/Bb226510(v=BTS.80)
ms:contentKeyID: 51531087
ms.date: 08/30/2017
mtps_version: v=BTS.80
f1_keywords:
- bts10.adapters.wcf-netmsmq.transport.send.messages
---

# WCF-NetMsmq Transport Properties Dialog Box, Send, Messages Tab

 

Use the **Messages** tab to specify the data selection for the SOAP **Body** element.

<table>
<thead>
<tr class="header">
<th>Use this</th>
<th>To do this</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>Body -- BizTalk request message body</strong></td>
<td>Use the BizTalk message body part to create the content of the SOAP <strong>Body</strong> element for an outgoing message.<br />
<br />
This is the default setting.</td>
</tr>
<tr class="even">
<td><strong>Template -- content specified by template</strong></td>
<td>Use the template supplied in the <strong>XML</strong> text box to create the content of the SOAP <strong>Body</strong> element for an outgoing message.<br />
<br />
The default value is cleared.</td>
</tr>
<tr class="odd">
<td><strong>XML</strong></td>
<td>Type the XML-formatted template for the content of the SOAP <strong>Body</strong> element of an outgoing message. This property is required if the <strong>Template -- content specified by template</strong> option is selected.<br />
<br />
Type: String<br />
<br />
Minimum length: 0<br />
<br />
Maximum length: 32767<br />
<br />
The default is &lt;bts-msg-body<br />
<br />
`xmlns="http://www.microsoft.com/schemas/bts2007" encoding="xml"`</td>
</tr>
</tbody>
</table>


## See Also

[How to Configure a WCF-NetMsmq Send Port](https://msdn.microsoft.com/library/bb245965\(v=bts.80\))  
[Specifying the Message Body for the WCF Adapters](https://msdn.microsoft.com/library/bb226478\(v=bts.80\))
