---
title: HTTP Transport Properties Dialog Box, Authentication Tab
TOCTitle: HTTP Transport Properties Dialog Box, Authentication Tab
ms:assetid: d9d510e4-c34f-4ef3-817e-62e9ed199e24
ms:mtpsurl: https://msdn.microsoft.com/library/Aa578713(v=BTS.80)
ms:contentKeyID: 51531663
ms.date: 08/30/2017
mtps_version: v=BTS.80
f1_keywords:
- bts10.adaptors.http.transport.authentication
---

# HTTP Transport Properties Dialog Box, Authentication Tab

 

In the **HTTP Transport Properties** dialog box, use the **Authentication** tab to configure the send port for the HTTP adapter.

<table>
<thead>
<tr class="header">
<th>Use this</th>
<th>To do this</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>Authentication Type</strong></td>
<td>Specify the type of authentication to use with the destination server.<br />
<br />
Options:<br />
<br />
- Anonymous<br />
- Basic<br />
- Digest<br />
- Kerberos<br />
<br />
Default Value: Anonymous</td>
</tr>
<tr class="even">
<td><strong>Credentials</strong></td>
<td>Specify the type of credentials to use.<br />
<br />
Only available if the Authentication Type is Basic or Digest.<br />
<br />
Options:<br />
<br />
- <strong>Do Not Use Single Sign-On</strong><br />
     <strong>User name</strong><br />
The user name to use for authentication with the destination server. If the Authentication Type property is Anonymous or Kerberos, this option is disabled. This property requires a value if Basic or Digest is selected, and Enterprise Single Sign-On is not used.<br />
Minimum length: 0<br />
Maximum length: 256<br />
     <strong>Password</strong><br />
The password to use for authentication with the destination server. If the Authentication Type property is Anonymous or Kerberos, this option is disabled. This property requires a value if Basic or Digest is selected, and Single Sign-On is not used.<br />
Minimum length: 0<br />
Maximum length: 256<br />
- <strong>Use Single Sign-On</strong><br />
Specify whether to use Single Sign-On to retrieve client credentials for authentication with the destination server.<br />
     <strong>Affiliate Application</strong><br />
Specifies the affiliate application to use for Single Sign-On.<br />
Choose the applications that you want to include in Single Sign-On.<br />
Minimum length: 0<br />
Maximum length: 256</td>
</tr>
<tr class="odd">
<td><strong>SSL client certificate thumbprint</strong></td>
<td>Specify the thumbprint of the client certificate to use for establishing a Secure Sockets Layer (SSL) connection.<br />
<br />
Minimum length: 0<br />
<br />
Maximum length: 59</td>
</tr>
</tbody>
</table>


## See Also

[Configuring an HTTP Send Port](https://msdn.microsoft.com/library/aa577941\(v=bts.80\))

