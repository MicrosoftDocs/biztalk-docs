---
description: "Learn more about: SOAP Transport Properties Dialog Box, Proxy Tab"
title: SOAP Transport Properties Dialog Box, Proxy Tab
TOCTitle: SOAP Transport Properties Dialog Box, Proxy Tab
ms:assetid: 070aaab8-0b67-419d-816c-15fb2594c7f1
ms:mtpsurl: https://msdn.microsoft.com/library/Aa547068(v=BTS.80)
ms:contentKeyID: 51526015
ms.date: 08/30/2017
mtps_version: v=BTS.80
f1_keywords:
- bts10.adaptors.soap.transport.proxy
---

# SOAP Transport Properties Dialog Box, Proxy Tab

 

In the **SOAP Transport Properties** dialog box, use the **Proxy** tab to configure the send port for the SOAP adapter.

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
<td>Indicate whether the SOAP send handler uses a proxy server.</td>
</tr>
<tr class="odd">
<td><strong>Use proxy</strong></td>
<td>Indicate whether the SOAP send handler uses a proxy server.</td>
</tr>
<tr class="even">
<td><strong>Server</strong></td>
<td>Specifies the name of the proxy server.<br />
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
<td>Specify the port the SOAP send handler uses.<br />
<br />
This property only requires a value if Use proxy is selected.<br />
<br />
Default Value: 80<br />
<br />
Type: Long<br />
<br />
Minimum value: 0<br />
<br />
Maximum value: 65,535</td>
</tr>
<tr class="even">
<td><strong>User name</strong></td>
<td>Specify the user name to use for authentication. If integrated authentication is used, the user name includes the domain, domain\username. If Basic or Digest authentication is used, the user name does not include domain\.<br />
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
<td>Specify the password to use for authentication.<br />
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

[How to Configure a SOAP Send Port](https://msdn.microsoft.com/library/aa559642\(v=bts.80\))

