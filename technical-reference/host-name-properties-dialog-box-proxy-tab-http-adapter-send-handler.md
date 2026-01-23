---
description: "Learn more about: <Host Name> Properties Dialog Box, Proxy Tab (HTTP Adapter Send Handler)"
title: <Host Name> Properties Dialog Box, Proxy Tab (HTTP Adapter Send Handler)
TOCTitle: <Host Name> Properties Dialog Box, Proxy Tab (HTTP Adapter Send Handler)
ms:assetid: 54aee60f-6cc6-4fd7-a6d5-59ac94a8fa83
ms:mtpsurl: https://msdn.microsoft.com/library/Aa560204(v=BTS.80)
ms:contentKeyID: 51528098
ms.date: 08/30/2017
mtps_version: v=BTS.80
f1_keywords:
- bts10.adaptors.proxy.props1
ms.topic: ui-reference
---

# \<Host Name\> Properties Dialog Box, Proxy Tab (HTTP Adapter Send Handler)

 

Use the **Proxy** tab to configure the send handler for the HTTP adapter.

<table>
<thead>
<tr class="header">
<th>Use this</th>
<th>To do this</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>Use proxy</strong></td>
<td>Specify whether the HTTP send handler uses the proxy server.<br />
<br />
Default value: False<br />
<br />
Type: Boolean</td>
</tr>
<tr class="even">
<td><strong>Server</strong></td>
<td>Specify the proxy server address for this send port.<br />
<br />
This property requires a value if Use proxy is True.<br />
<br />
Type: String<br />
<br />
Minimum length: 0<br />
<br />
Maximum length: 256</td>
</tr>
<tr class="odd">
<td><strong>Port</strong></td>
<td>Specify the proxy server port for this send port.<br />
<br />
This property requires a value if Use proxy is True.<br />
<br />
Default Value: 80<br />
<br />
Type: Long<br />
<br />
Minimum value: 0<br />
<br />
Maximum value: 65535</td>
</tr>
<tr class="even">
<td><strong>User name</strong></td>
<td>Specify the user name to use for authentication with the proxy server.<br />
<br />
This property requires a value if Use proxy is True.<br />
<br />
Type: String<br />
<br />
Minimum length: 0<br />
<br />
Maximum length: 256</td>
</tr>
<tr class="odd">
<td><strong>Password</strong></td>
<td>Specify the user password for authentication with the proxy server.<br />
<br />
This property requires a value if Use proxy is True.<br />
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

