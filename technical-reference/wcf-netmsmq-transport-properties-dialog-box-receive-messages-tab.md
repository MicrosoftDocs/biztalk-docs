---
title: WCF-NetMsmq Transport Properties Dialog Box, Receive, Messages Tab
TOCTitle: WCF-NetMsmq Transport Properties Dialog Box, Receive, Messages Tab
ms:assetid: 95834c20-4d49-44a4-99c1-410f086135a7
ms:mtpsurl: https://msdn.microsoft.com/library/Bb226422(v=BTS.80)
ms:contentKeyID: 51529797
ms.date: 08/30/2017
mtps_version: v=BTS.80
f1_keywords:
- bts10.adapters.wcf-netmsmq.transport.receive.messages
---

# WCF-NetMsmq Transport Properties Dialog Box, Receive, Messages Tab

 

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
<td><strong>Envelope -- entire &lt;soap:Envelope&gt;</strong></td>
<td>Create the BizTalk message body part from the entire SOAP <strong>Envelope</strong> of an incoming message.<br />
<br />
The default value is cleared.</td>
</tr>
<tr class="even">
<td><strong>Body -- contents of &lt;soap:Body&gt; element</strong></td>
<td>Use the content of the SOAP <strong>Body</strong> element of an incoming message to create the BizTalk message body part. If the <strong>Body</strong> element has more than one child element, only the first element becomes the BizTalk message body part.<br />
<br />
This is the default setting.</td>
</tr>
<tr class="odd">
<td><strong>Path -- content located by body path</strong></td>
<td>Use the body path expression in the <strong>Body path expression</strong> text box to create the BizTalk message body part. The body path expression is evaluated against the immediate child element of the SOAP <strong>Body</strong> element of an incoming message.<br />
<br />
The default value is cleared.</td>
</tr>
<tr class="even">
<td><strong>Body path expression</strong></td>
<td>Type the body path expression to identify a specific part of an incoming message used to create the BizTalk message body part. This body path expression is evaluated against the immediate child element of the SOAP <strong>Body</strong> element of an incoming message. If this body path expression returns more than one node, only the first node is chosen for the BizTalk message body part. This property is required if the <strong>Path -- content located by body path</strong> option is selected.<br />
<br />
Type: String<br />
<br />
Minimum length: 0<br />
<br />
Maximum length: 32767<br />
<br />
The default is an empty string.</td>
</tr>
<tr class="odd">
<td><strong>Node encoding</strong></td>
<td>Specify the type of encoding that the WCF-NetMsmq receive adapter uses to decode for the node identified by the body path expression in the <strong>Body path expression</strong> text box. This property is required if the <strong>Path -- content located by body path</strong> option is selected. Valid values include the following:<br />
<br />
- <strong>Base64</strong>: Base64 encoding.<br />
- <strong>Hex</strong>: Hexadecimal encoding.<br />
- <strong>String</strong>: Text encoding - UTF-8<br />
- <strong>XML</strong>: The WCF adapters create the BizTalk message body with the outer XML of the node selected by the body path expression in the <strong>Body path expression</strong> text box.<br />
<br />
The default is <strong>XML</strong>.</td>
</tr>
<tr class="even">
<td><strong>Disable location on failure</strong></td>
<td>Specify whether to disable the receive location that fails inbound processing due to a receive pipeline failure or a routing failure.<br />
<br />
The default value is cleared.</td>
</tr>
<tr class="odd">
<td><strong>Suspend request message on failure</strong></td>
<td>Specify whether to suspend the request message that fails inbound processing due to a receive pipeline failure or a routing failure.<br />
<br />
The default value is selected.</td>
</tr>
</tbody>
</table>


## See Also

[How to Configure a WCF-NetMsmq Receive Location](https://msdn.microsoft.com/library/bb259976\(v=bts.80\))  
[Specifying the Message Body for the WCF Adapters](https://msdn.microsoft.com/library/bb226478\(v=bts.80\))

