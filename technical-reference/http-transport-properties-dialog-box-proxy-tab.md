---
title: HTTP Transport Properties Dialog Box, Proxy Tab
TOCTitle: HTTP Transport Properties Dialog Box, Proxy Tab
ms:assetid: 9567b416-b440-46ff-bd9e-6960ea788b78
ms:mtpsurl: https://msdn.microsoft.com/library/Aa577427(v=BTS.80)
ms:contentKeyID: 51529824
ms.date: 08/30/2017
mtps_version: v=BTS.80
f1_keywords:
- bts10.adaptors.http.transport.proxy
---

# HTTP Transport Properties Dialog Box, Proxy Tab

 

In the **HTTP Transport Properties** dialog box, use the **Proxy (Handler override)** tab to configure the send port for the HTTP adapter.

<table>
<thead>
<tr class="header">
<th>Use this</th>
<th>To do this</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>Use Handler's default proxy configuration</strong></td>
<td>Specify that the configuration for the send port uses the proxy handler.<br />
<br />
This is the default setting.</td>
</tr>
<tr class="even">
<td><strong>Do not use proxy</strong></td>
<td>Specify whether the HTTP send handler uses the proxy server.<br />
<br />
If selected, the HTTP send handler does not use the proxy server.</td>
</tr>
<tr class="odd">
<td><strong>Use proxy</strong></td>
<td>Specify whether the HTTP send handler uses the proxy server.<br />
<br />
If selected, the HTTP send handler uses the proxy server.</td>
</tr>
<tr class="even">
<td><strong>Server</strong></td>
<td>Specify the proxy server address for this send port.<br />
<br />
This property only requires a value if Use proxy is selected.<br />
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
This property only requires a value if Use proxy is selected.<br />
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
<td>Specify the user name for authentication with the proxy server.<br />
<br />
This property only requires a value if Use proxy is selected.<br />
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
This property only requires a value if Use proxy is selected.<br />
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

