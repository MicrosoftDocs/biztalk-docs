---
title: SMTP Transport Properties Dialog Box, Handler Override Tab
TOCTitle: SMTP Transport Properties Dialog Box, Handler Override Tab
ms:assetid: bfacf52d-37af-418c-8deb-e43ccb5de825
ms:mtpsurl: https://msdn.microsoft.com/library/Aa578424(v=BTS.80)
ms:contentKeyID: 51530918
ms.date: 08/30/2017
mtps_version: v=BTS.80
f1_keywords:
- bts10.adaptors.smtp.transport.override
---

# SMTP Transport Properties Dialog Box, Handler Override Tab

 

In the **SMTP Transport Properties** dialog box, use the **Handler Override** tab to configure the send port for the Simple Mail Transfer Protocol (SMTP) adapter.

<table>
<thead>
<tr class="header">
<th>Use this</th>
<th>To do this</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>SMTP server name</strong></td>
<td>Specify the name of the SMTP server to use when sending messages.<br />
<br />
Maximum length: 256</td>
</tr>
<tr class="even">
<td><strong>From (e-mail address)</strong></td>
<td>Specify the e-mail address to place on the SMTP From header.<br />
<br />
Maximum length: 256</td>
</tr>
<tr class="odd">
<td><strong>Authentication type</strong></td>
<td>Specify the type of authentication to use with the SMTP server.<br />
<br />
Options:<br />
<br />
- (Default)<br />
- Do not authenticate<br />
- Basic authentication<br />
- Process account (NTLM)</td>
</tr>
<tr class="even">
<td><strong>User name</strong></td>
<td>Specify the user name to use for authentication with the SMTP server.<br />
<br />
This property requires a value if Authentication type is Basic authentication.<br />
<br />
Minimum length: 0<br />
<br />
Maximum length: 256</td>
</tr>
<tr class="odd">
<td><strong>Password</strong></td>
<td>Specify the password to use for authentication with the SMTP server.<br />
<br />
This property requires a value if Authentication type is Basic authentication.<br />
<br />
Minimum length: 0<br />
<br />
Maximum length: 256</td>
</tr>
</tbody>
</table>

