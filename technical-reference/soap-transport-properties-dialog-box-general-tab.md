---
title: SOAP Transport Properties Dialog Box, General Tab
TOCTitle: SOAP Transport Properties Dialog Box, General Tab
ms:assetid: 28abbac8-d51d-4094-a5fb-b62df2d350b8
ms:mtpsurl: https://msdn.microsoft.com/library/Aa559300(v=BTS.80)
ms:contentKeyID: 51526959
ms.date: 08/30/2017
mtps_version: v=BTS.80
f1_keywords:
- bts10.adaptors.soap.transport.general
---

# SOAP Transport Properties Dialog Box, General Tab

 

In the **SOAP Transport Properties** dialog box, use the **General** tab to configure the send port for the SOAP adapter.

<table>
<thead>
<tr class="header">
<th>Use this</th>
<th>To do this</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>Web Service URL</strong></td>
<td>Specify the address of the Web service you want to call.</td>
</tr>
<tr class="even">
<td><strong>Authentication</strong></td>
<td>Indicate the authentication method used by the Web service you are calling.<br />
<br />
Options:<br />
<br />
- Anonymous<br />
- Basic<br />
- Digest<br />
- NTLM</td>
</tr>
<tr class="odd">
<td><strong>Credentials</strong></td>
<td>Specify the type of credentials to use.<br />
<br />
Only available if the Authentication type is Basic or Digest.<br />
<br />
Options:<br />
<br />
- Do Not Use Single Sign-On<br />
     <strong>User name</strong><br />
The user name to use for authentication with the destination server. If the Authentication type property is Anonymous or Kerberos, this option is disabled. This property requires a value if Basic or Digest is selected, and Enterprise Single Sign-On is not used.<br />
Minimum length: 0<br />
Maximum length: 256<br />
     <strong>Password</strong><br />
The password to use for authentication with the destination server. If the Authentication type property is Anonymous or Kerberos, this option is disabled. This property requires a value if Basic or Digest is selected, and Single Sign-On is not used.<br />
Minimum length: 0<br />
Maximum length: 256<br />
- Use Single Sign-On<br />
Specify whether to use Single Sign-On to retrieve client credentials for authentication with the destination server.<br />
     <strong>Affiliate Application</strong><br />
Specifies the affiliate application to use for Single Sign-On. For information about populating this list, see the appropriate topics in See Also.<br />
Minimum length: 0<br />
Maximum length: 256</td>
</tr>
<tr class="even">
<td><strong>Client Certificate Thumbprint</strong></td>
<td>Specify the thumbprint of the client certificate to use for establishing a connection.<br />
<br />
Minimum length: 0<br />
<br />
Maximum length: 59</td>
</tr>
</tbody>
</table>


## See Also

[How to Configure a SOAP Send Port](https://msdn.microsoft.com/library/aa559642\(v=bts.80\))  
[Using SSO](https://msdn.microsoft.com/library/aa561654\(v=bts.80\))

