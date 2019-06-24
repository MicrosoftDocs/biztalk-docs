---
title: <Host Name> Properties Dialog Box, Proxy Tab (WCF-BasicHttp Adapter Send Handler)
TOCTitle: <Host Name> Properties Dialog Box, Proxy Tab (WCF-BasicHttp Adapter Send Handler)
ms:assetid: acea821f-2941-4498-94d6-12e5ff1b76d3
ms:mtpsurl: https://msdn.microsoft.com/library/Bb226468(v=BTS.80)
ms:contentKeyID: 51530432
ms.date: 08/30/2017
mtps_version: v=BTS.80
f1_keywords:
- bts10.adapters.wcf-basichttp.sendhandler.proxy
---

# \<Host Name\> Properties Dialog Box, Proxy Tab (WCF-BasicHttp Adapter Send Handler)

 

Use the **Proxy** tab to configure the send handler for the WCF-BasicHttp adapter.

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
<td>Indicate whether this send port uses a proxy server.<br />
<br />
The default value is cleared.</td>
</tr>
<tr class="even">
<td><strong>Address</strong></td>
<td>Specify the address of the proxy server. Specify the address of the proxy server. Use the <strong>https</strong> or the <strong>http</strong> scheme depending on the security configuration. This address can be followed by a colon and the port number. For example, http://127.0.0.1:8080.<br />
<br />
This property requires a value only if <strong>Use proxy</strong> is selected.<br />
<br />
Type: String<br />
<br />
Maximum length: 256<br />
<br />
The default is an empty string.</td>
</tr>
<tr class="odd">
<td><strong>User name</strong></td>
<td>Specify the user name to use for authentication. If integrated authentication is used, the user name includes the domain, that is, domain\username. If Basic or Digest authentication is used, the user name does not include domain\.<br />
<br />
This property requires a value only if <strong>Use proxy</strong> is selected.<br />
<br />
Type: String<br />
<br />
Minimum length: 0<br />
<br />
Maximum length: 256<br />
<br />
The default is an empty string.</td>
</tr>
<tr class="even">
<td><strong>Password</strong></td>
<td>Specify the password to use for authentication.<br />
<br />
This property requires a value only if <strong>Use proxy</strong> is selected.<br />
<br />
Type: String<br />
<br />
Minimum length: 0<br />
<br />
Maximum length: 256<br />
<br />
The default is an empty string.</td>
</tr>
</tbody>
</table>


## See Also

[How to Configure a WCF-BasicHttp Send Handler](https://msdn.microsoft.com/library/bb245976\(v=bts.80\))

