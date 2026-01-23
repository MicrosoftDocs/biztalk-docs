---
description: "Learn more about: HTTP Transport Properties Dialog Box"
title: HTTP Transport Properties Dialog Box
TOCTitle: HTTP Transport Properties Dialog Box
ms:assetid: aa3a9d4d-56d6-4db8-8636-347bd0293653
ms:mtpsurl: https://msdn.microsoft.com/library/Aa577971(v=BTS.80)
ms:contentKeyID: 51530351
ms.date: 08/30/2017
mtps_version: v=BTS.80
f1_keywords:
- bts10.adaptors.http.transport
ms.topic: ui-reference
---

# HTTP Transport Properties Dialog Box

 

Use the **HTTP Transport Properties** dialog box to configure the receive location for the HTTP adapter.

<table>
<thead>
<tr class="header">
<th>Use this</th>
<th>To do this</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>Virtual directory plus ISAPI extension</strong></td>
<td>Specify the name of the virtual directory where you post the messages received by the HTTP/HTTPS receive location. The virtual directory includes the name of the receive location DLL and an optional query string. Examples of virtual directory names are:<br />
<br />
/&lt;virtual directory&gt;/BTSHTTPReceive.dll<br />
<br />
/&lt;virtual directory&gt;/BTSHTTPReceive.dll?Purchase%20Order<br />
<br />
This location must not contain more than one BTSHTTPReceive.dll ISAPI extension, including all subfolders.<br />
<br />
Type: String<br />
<br />
Maximum length: 256</td>
</tr>
<tr class="even">
<td><strong>Public address</strong></td>
<td>Specify the fully qualified URI for this receive location. The value for this property is a combination of the server name and the virtual directory. This address is exposed to external partners.<br />
<br />
Type: String<br />
<br />
Minimum length: 0<br />
<br />
Maximum length: 256</td>
</tr>
<tr class="odd">
<td><strong>Return content type</strong></td>
<td>Specify the content type of HTTP response messages that the receive location sends back to clients. This property is valid only for request-response receive locations.<br />
<br />
Default value: text/xml<br />
<br />
Type: String<br />
<br />
Minimum length: 0<br />
<br />
Maximum length: 256</td>
</tr>
<tr class="even">
<td><strong>Loopback</strong></td>
<td>Define that the request message received on this location is routed either to a send port or back to this receive location to be sent as a response. This property is valid only for request-response receive locations.<br />
<br />
Default value: False<br />
<br />
Type: Boolean</td>
</tr>
<tr class="odd">
<td><strong>Return correlation handle on success (this setting is for one-way port only)</strong></td>
<td>Define that if successful, the receive location sends the correlation token of the submitted message on the HTTP response to the client. This property is valid only for one-way receive locations.<br />
<br />
Default value: True<br />
<br />
Type: Boolean</td>
</tr>
<tr class="even">
<td><strong>Use Single Sign-On</strong></td>
<td>Indicate that Enterprise Single Sign-On is used.<br />
<br />
Default value: False<br />
<br />
Type: Boolean</td>
</tr>
<tr class="odd">
<td><strong>Suspend failed requests</strong></td>
<td>Indicate whether to suspend an HTTP request that fails inbound processing due to a receive pipeline failure or a routing failure.<br />
<br />
Default value: False<br />
<br />
Type: Boolean</td>
</tr>
</tbody>
</table>


## See Also

[How to Configure an HTTP Receive Location](https://msdn.microsoft.com/library/aa561370\(v=bts.80\))  
[Configuring the HTTP Adapter](https://msdn.microsoft.com/library/aa560119\(v=bts.80\))

