---
description: "Learn more about: <Host Name> Properties Dialog Box, Properties Tab (SMTP Adapter)"
title: <Host Name> Properties Dialog Box, Properties Tab (SMTP Adapter)
TOCTitle: <Host Name> Properties Dialog Box, Properties Tab (SMTP Adapter)
ms:assetid: a4e09d76-8304-4eb1-b23e-0dd2fe7b9388
ms:mtpsurl: https://msdn.microsoft.com/library/Aa577870(v=BTS.80)
ms:contentKeyID: 51530204
ms.date: 08/30/2017
mtps_version: v=BTS.80
f1_keywords:
- bts10.adaptors.smtp.props1
ms.topic: ui-reference
---

# \<Host Name\> Properties Dialog Box, Properties Tab (SMTP Adapter)

 

Use the **Properties** tab to configure the send handler for the Simple Mail Transfer Protocol (SMTP) adapter.

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
This property requires a value.<br />
<br />
Maximum length: 256</td>
</tr>
<tr class="even">
<td><strong>From (e-mail address)</strong></td>
<td>Required. Specify the e-mail address to place on the SMTP From header.<br />
<br />
Maximum length: 256</td>
</tr>
<tr class="odd">
<td><strong>Authentication type</strong></td>
<td>Specify the type of authentication to use with the SMTP server.<br />
<br />
Options:<br />
<br />
- Do not authenticate<br />
- Basic authentication<br />
- Process account (NTLM)<br />
<br />
Default value: Process account (NTLM)</td>
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


## See Also

[How to Configure an SMTP Send Handler](https://msdn.microsoft.com/library/aa578257\(v=bts.80\))

