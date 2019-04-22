---
title: WCF-Custom Transport Properties Dialog Box, Send, Credentials Tab
TOCTitle: WCF-Custom Transport Properties Dialog Box, Send, Credentials Tab
ms:assetid: 8bde7371-7635-407f-ac56-74631e15c811
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Bb226399(v=BTS.80)
ms:contentKeyID: 51529574
ms.date: 08/30/2017
mtps_version: v=BTS.80
f1_keywords:
- bts10.adapters.wcf-custom.transport.send.clientcredentials
---

# WCF-Custom Transport Properties Dialog Box, Send, Credentials Tab

 

Use the **Credentials** tab to specify the credentials to be used when sending messages.

<table>
<thead>
<tr class="header">
<th>Use this</th>
<th>To do this</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>Do not use Single Sign-On</strong></td>
<td>Use the <strong>User name</strong> and <strong>Password</strong> properties to set client credentials for authentication with the destination server.<br />
<br />
This is the default setting.</td>
</tr>
<tr class="even">
<td><strong>User name</strong></td>
<td>Specify the user name to use for authentication with the destination server when the <strong>Do not use Single Sign-On</strong> option is selected.<br />
<br />
Minimum length: 0<br />
<br />
Maximum length: 256<br />
<br />
The default is an empty string.</td>
</tr>
<tr class="odd">
<td><strong>Password</strong></td>
<td>Specify the password to use for authentication with the destination server when the <strong>Do not use Single Sign-On</strong> option is selected.<br />
<br />
Minimum length: 0<br />
<br />
Maximum length: 256<br />
<br />
The default is an empty string.</td>
</tr>
<tr class="even">
<td><strong>Use Single Sign-On</strong></td>
<td>Use Single Sign-On to retrieve client credentials for authentication with the destination server. <strong>Note:</strong> For a WCF send port to validate and redeem an SSO ticket properly, the <strong>SSOTicket</strong> and <strong>OriginatorSID</strong> context properties must be available in a message to be sent. A receive location with Single Sign-On enabled can promote these properties from a sender's Windows account.<br />
<br />
The default value is cleared.</td>
</tr>
<tr class="odd">
<td><strong>Affiliated application</strong></td>
<td>Specify the affiliate application to use for Single Sign-On. For information about populating this list, see the appropriate topics in See Also.<br />
<br />
Minimum length: 0<br />
<br />
Maximum length: 256<br />
<br />
The default value is cleared.</td>
</tr>
<tr class="even">
<td><strong>Address</strong></td>
<td>Specify the address of the proxy server. Use the <strong>https</strong> or the <strong>http</strong> scheme depending on the security configuration. This address can be followed by a colon and the port number. For example, http://127.0.0.1:8080. This property requires a value only if you intend to configure the proxy settings.<br />
<br />
Type: String<br />
<br />
Maximum length: 256<br />
<br />
The default is an empty string.</td>
</tr>
<tr class="odd">
<td><strong>User name</strong></td>
<td>Specify the user name to use for authentication. If integrated authentication is used, the user name includes the domain, that is, domain\username. If Basic or Digest authentication is used, the user name does not include domain\. This property requires a value only if you intend to configure the proxy settings.<br />
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
This property requires a value only if you intend to configure the proxy settings.<br />
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

[How to Configure a WCF-Custom Send Port](https://msdn.microsoft.com/library/bb226446\(v=bts.80\))  
[Using SSO](https://msdn.microsoft.com/library/aa561654\(v=bts.80\))

