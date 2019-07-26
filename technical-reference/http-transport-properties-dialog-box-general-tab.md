---
title: HTTP Transport Properties Dialog Box, General Tab
TOCTitle: HTTP Transport Properties Dialog Box, General Tab
ms:assetid: bfec6b41-c556-4f10-9d42-0815b655f686
ms:mtpsurl: https://msdn.microsoft.com/library/Aa578430(v=BTS.80)
ms:contentKeyID: 51530922
ms.date: 08/30/2017
mtps_version: v=BTS.80
f1_keywords:
- bts10.adaptors.http.transport.general
---

# HTTP Transport Properties Dialog Box, General Tab

 

In the **HTTP Transport Properties** dialog box, use the **General**tab to configure the send port for the HTTP adapter.

<table>
<thead>
<tr class="header">
<th>Use this</th>
<th>To do this</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>Destination URL</strong></td>
<td>Required. Specify the address to send HTTP requests. Include query strings appended to the base URL.<br />
<br />
Type: String<br />
<br />
Maximum length: 256</td>
</tr>
<tr class="even">
<td><strong>Enable chunked encoding</strong></td>
<td>It is an optimization done for http protocol. If it is selected, the http adapter will use chunked transfer encoding.<br />
<br />
Valid values are:<br />
<br />
True (checked) The http adapter will use chunked transfer encoding.<br />
<br />
False (not checked) The http adapter will not use chunked transfer encoding.<br />
<br />
Default Value: True</td>
</tr>
<tr class="odd">
<td><strong>Request timeout (sec)</strong></td>
<td>Specify the time-out in seconds for the HTTP/HTTPS transmission. If the response is not received within this time, the service logs the error and resubmits the message based on the retry infrastructure.<br />
<br />
If set to zero (0), then the time-out is calculated based on the request message size. If the value is not provided, then the value for the handler is used.<br />
<br />
Type: Long<br />
<br />
Minimum value: 0<br />
<br />
Maximum value: MAX_LONG</td>
</tr>
<tr class="even">
<td><strong>Maximum redirects</strong></td>
<td>This property is not implemented by the HTTP send port.</td>
</tr>
<tr class="odd">
<td><strong>Content type</strong></td>
<td>Specify the content type of the request messages.<br />
<br />
If this value is not set, then the value for the handler is used.<br />
<br />
Type: String<br />
<br />
Minimum length: 0<br />
<br />
Maximum length: 256</td>
</tr>
</tbody>
</table>


## See Also

[Configuring an HTTP Send Port](https://msdn.microsoft.com/library/aa577941\(v=bts.80\))  
[Restrictions on the Destination URL Property](https://msdn.microsoft.com/library/aa577471\(v=bts.80\))

