---
title: WCF Adapters Transport Properties Dialog Box, Send, Client Credentials
TOCTitle: WCF Adapters Transport Properties Dialog Box, Send, Client Credentials
ms:assetid: 37d87be9-3664-4bab-a781-21dd8ad13337
ms:mtpsurl: https://msdn.microsoft.com/library/Bb246039(v=BTS.80)
ms:contentKeyID: 51527371
ms.date: 08/30/2017
mtps_version: v=BTS.80
f1_keywords:
- bts10.adapters.wcf-adapters.transport.send.clientcredentials
---

# WCF Adapters Transport Properties Dialog Box, Send, Client Credentials

 

Use the **Client Credentials** dialog box to specify the credentials to be used when sending messages.

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
<td>Specify the user name to use for authentication with the destination server when the <strong>Do not use Single Sign-On</strong> option is selected. You do not have to use the domain\user format for this property.<br />
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
</tbody>
</table>


## See Also

[Using SSO](https://msdn.microsoft.com/library/aa561654\(v=bts.80\))  
[How to Configure a WCF-BasicHttp Send Port](https://msdn.microsoft.com/library/bb226467\(v=bts.80\))  
[How to Configure a WCF-WSHttp Send Port](https://msdn.microsoft.com/library/bb245939\(v=bts.80\))  
[How to Configure a WCF-NetTcp Send Port](https://msdn.microsoft.com/library/bb226460\(v=bts.80\))  
[How to Configure a WCF-NetMsmq Send Port](https://msdn.microsoft.com/library/bb245965\(v=bts.80\))  
[How to Configure a WCF-NetNamedPipe Send Port](https://msdn.microsoft.com/library/bb246110\(v=bts.80\))

