---
title: <Host Name> Properties Dialog Box, Properties Tab (HTTP Adapter Send Handler)
TOCTitle: <Host Name> Properties Dialog Box, Properties Tab (HTTP Adapter Send Handler)
ms:assetid: e1395497-2631-4c1a-b40c-7e1d66c115ea
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa561531(v=BTS.80)
ms:contentKeyID: 51532919
ms.date: 08/30/2017
mtps_version: v=BTS.80
f1_keywords:
- bts10.adaptors.http.handler.send.props
---

# \<Host Name\> Properties Dialog Box, Properties Tab (HTTP Adapter Send Handler)

 

In the **\<Host Name\> Properties** dialog box, use the Properties tab to configure the send handler for the HTTP adapter.

<table>
<thead>
<tr class="header">
<th>Use this</th>
<th>To do this</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>Request timeout (sec)</strong></td>
<td>Specify the time-out in seconds when waiting for a response from the server.<br />
<br />
If set to zero (0), then the time-out is calculated based on the request message size.<br />
<br />
If a value is not provided, then the value for the handler is used.<br />
<br />
Default Value: 0<br />
<br />
Type: Long<br />
<br />
Minimum value: 0<br />
<br />
Maximum value: MAX_LONG</td>
</tr>
<tr class="even">
<td><strong>Maximum redirects</strong></td>
<td>Specify the maximum redirects allowed for the message being sent.<br />
<br />
Default value: 5<br />
<br />
Type:<br />
<br />
Minimum value: 0<br />
<br />
Maximum value: MAX_LONG</td>
</tr>
<tr class="odd">
<td><strong>Content type</strong></td>
<td>Specify the content type of the request messages.<br />
<br />
If a value is not provided, then the value for the handler is used.<br />
<br />
Default value: text/xml<br />
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

[How to Configure an HTTP Send Handler](https://msdn.microsoft.com/library/aa561097\(v=bts.80\))

