---
title: WCF-NetTcp Transport Properties Dialog Box, Receive, Messages Tab
TOCTitle: WCF-NetTcp Transport Properties Dialog Box, Receive, Messages Tab
ms:assetid: 5d672b29-151c-4539-9cfe-b50ab4565745
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Bb246123(v=BTS.80)
ms:contentKeyID: 51528350
ms.date: 08/30/2017
mtps_version: v=BTS.80
f1_keywords:
- bts10.adapters.wcf-nettcp.transport.receive.messages
---

# WCF-NetTcp Transport Properties Dialog Box, Receive, Messages Tab

 

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
<td>Specify the type of encoding that the WCF-NetTcp receive adapter uses to decode for the node identified by the body path expression in the <strong>Body path expression</strong> text box. This property is required if the <strong>Path -- content located by body path</strong> option is selected. Valid values include the following:<br />
<br />
- <strong>Base64</strong>: Base64 encoding.<br />
- <strong>Hex</strong>: Hexadecimal encoding.<br />
- <strong>String</strong>: Text encoding - UTF-8<br />
- <strong>XML</strong>: The WCF adapters create the BizTalk message body with the outer XML of the node selected by the body path expression in the <strong>Body path expression</strong> text box.<br />
<br />
The default is <strong>XML</strong>.</td>
</tr>
<tr class="even">
<td><strong>Body -- BizTalk response message body</strong></td>
<td>Use the BizTalk message body part to create the content of the SOAP <strong>Body</strong> element of an outgoing response message. This property is valid only for request-response receive locations.<br />
<br />
This is the default setting.</td>
</tr>
<tr class="odd">
<td><strong>Template -- content specified by template</strong></td>
<td>Use the template supplied in the <strong>XML</strong> text box to create the content of the SOAP <strong>Body</strong> element for an outgoing message. This property is valid only for request-response receive locations.<br />
<br />
The default value is cleared.</td>
</tr>
<tr class="even">
<td><strong>XML</strong></td>
<td>Type the XML-formatted template for the content of the SOAP <strong>Body</strong> element of an outgoing message. This property is required if the <strong>Template -- BizTalk response message body</strong> option is selected. This property is valid only for request-response receive locations.<br />
<br />
Type: String<br />
<br />
Minimum length: 0<br />
<br />
Maximum length: 32767<br />
<br />
The default is <strong>&lt;bts-msg-body xmlns=&quot;http://www.microsoft.com/schemas/bts2007&quot; encoding=&quot;xml&quot;/&gt;</strong>.</td>
</tr>
<tr class="odd">
<td><strong>Suspend request message on failure</strong></td>
<td>Specify whether to suspend the request message that fails inbound processing due to a receive pipeline failure or a routing failure.<br />
<br />
The default value is cleared.</td>
</tr>
<tr class="even">
<td><strong>Include exception detail in faults</strong></td>
<td>Specify whether to return SOAP faults when an error occurs to easy debugging.<br />
<br />
The default value is cleared.</td>
</tr>
</tbody>
</table>


## See Also

[Specifying the Message Body for the WCF Adapters](https://msdn.microsoft.com/en-us/library/bb226478\(v=bts.80\))  
[How to Configure a WCF-NetTcp Receive Location](https://msdn.microsoft.com/en-us/library/bb226412\(v=bts.80\))

