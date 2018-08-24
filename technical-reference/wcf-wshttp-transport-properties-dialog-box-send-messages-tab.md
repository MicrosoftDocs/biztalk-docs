---
title: WCF-WSHttp Transport Properties Dialog Box, Send, Messages Tab
TOCTitle: WCF-WSHttp Transport Properties Dialog Box, Send, Messages Tab
ms:assetid: d19d620c-a5f0-4ca5-bf4e-a074dd206916
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Bb226545(v=BTS.80)
ms:contentKeyID: 51531522
ms.date: 08/30/2017
mtps_version: v=BTS.80
f1_keywords:
- bts10.adapters.wcf-wshttp.transport.send.messages
---

# WCF-WSHttp Transport Properties Dialog Box, Send, Messages Tab

 

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
<td>Type the XML-formatted template for the content of the SOAP <strong>Body</strong> element of an outgoing message. This property is required if the <strong>Template -- BizTalk response message body</strong> option is selected.<br />
<br />
Type: String<br />
<br />
Minimum length: 0<br />
<br />
Maximum length: 32767<br />
<br />
The default is &lt;bts-msg-body<br />
<br />
xmlns=&quot;http://www.microsoft.com/schemas/bts2007&quot; encoding=&quot;xml&quot;/&gt;</td>
</tr>
<tr class="even">
<td><strong>Envelope -- entire &lt;soap:Envelope&gt;</strong></td>
<td>Create the BizTalk message body part from the entire SOAP <strong>Envelope</strong> of an incoming message. This property is valid only for solicit-response ports.<br />
<br />
The default value is cleared.</td>
</tr>
<tr class="odd">
<td><strong>Body -- contents of &lt;soap:Body&gt; element</strong></td>
<td>Use the content of the SOAP <strong>Body</strong> element of an incoming message to create the BizTalk message body part. If the <strong>Body</strong> element has more than one child element, only the first element becomes the BizTalk message body part. This property is valid only for solicit-response ports.<br />
<br />
This is the default setting.</td>
</tr>
<tr class="even">
<td><strong>Path -- content located by body path</strong></td>
<td>Use the body path expression in the <strong>Body path expression</strong> text box to create the BizTalk message body part. The body path expression is evaluated against the immediate child element of the SOAP <strong>Body</strong> element of an incoming message. This property is valid only for solicit-response ports.<br />
<br />
The default value is cleared.</td>
</tr>
<tr class="odd">
<td><strong>Body path expression</strong></td>
<td>Type the body path expression to identify a specific part of an incoming message used to create the BizTalk message body part. This body path expression is evaluated against the immediate child element of the SOAP <strong>Body</strong> node of an incoming message. If this body path expression returns more than one node, only the first node is chosen for the BizTalk message body part. This property is required if the <strong>Path -- content located by body path</strong> option is selected. This property is valid only for solicit-response ports.<br />
<br />
Type: String<br />
<br />
Minimum length: 0<br />
<br />
Maximum length: 32767<br />
<br />
The default is an empty string.</td>
</tr>
<tr class="even">
<td><strong>Node encoding</strong></td>
<td>Specify the type of encoding that the WCF-WSHttp send adapter uses to decode for the node identified by the body path expression in the <strong>Body path expression</strong> text box. This property is required if the <strong>Path -- content located by body path</strong> option is selected. This property is valid only for solicit-response ports. Valid values include the following:<br />
<br />
- <strong>Base64</strong>: Base64 encoding.<br />
- <strong>Hex</strong>: Hexadecimal encoding.<br />
- <strong>String</strong>: Text encoding - UTF-8<br />
- <strong>XML</strong>: The WCF adapters create the BizTalk message body with the outer XML of the node selected by the body path expression in the <strong>Body path expression</strong> text box.<br />
<br />
The default is <strong>XML</strong>.</td>
</tr>
<tr class="odd">
<td><strong>Propagate fault message</strong></td>
<td>Select this check box to route the message that fails outbound processing to a subscribing application (such as another receive port or orchestration schedule). Clear the check box to suspend failed messages and generate a negative acknowledgment (NACK). This property is valid only for solicit-response ports.<br />
<br />
The default value is selected.</td>
</tr>
</tbody>
</table>


## See Also

[How to Configure a WCF-WSHttp Send Port](https://msdn.microsoft.com/en-us/library/bb245939\(v=bts.80\))  
[Specifying the Message Body for the WCF Adapters](https://msdn.microsoft.com/en-us/library/bb226478\(v=bts.80\))

