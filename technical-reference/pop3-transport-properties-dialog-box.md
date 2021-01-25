---
description: "Learn more about: POP3 Transport Properties Dialog Box"
title: POP3 Transport Properties Dialog Box
TOCTitle: POP3 Transport Properties Dialog Box
ms:assetid: 7a8f6bc5-2af2-4fd7-abbc-865f9995d60a
ms:mtpsurl: https://msdn.microsoft.com/library/Aa560945(v=BTS.80)
ms:contentKeyID: 51529108
ms.date: 08/30/2017
mtps_version: v=BTS.80
f1_keywords:
- bts10.adaptors.pop3.receive
---

# POP3 Transport Properties Dialog Box

 

Use the **POP3 Transport Properties** dialog box to configure the receive location for the POP3 adapter.

<table>
<thead>
<tr class="header">
<th>Use this</th>
<th>To do this</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>Apply MIME decoding</strong></td>
<td>Specify whether or not to apply MIME decoding to messages that are received by the POP3 adapter.<br />
<br />
Default value: True<br />
<br />
Type: Boolean <strong>Important:</strong> If this value is set to False then the POP3 adapter will submit the complete e-mail body including message headers to BizTalk Server.</td>
</tr>
<tr class="even">
<td><strong>Body Part Content Type</strong></td>
<td>Specify the MIME Body Part of the incoming e-mail message to be submitted to BizTalk Server.<br />
<br />
Type: String <strong>Note:</strong> The POP3 adapter is designed to recognize the Body Part Content Types that are defined in RFC 2046.<br />
<br />
For more information about the POP3 adapter, see the topics in See Also.</td>
</tr>
<tr class="odd">
<td><strong>Body Part Index</strong></td>
<td>Specify the Body Part Index of the incoming e-mail messages to submit to BizTalk Server.<br />
<br />
Default value: 0<br />
<br />
Type: Long<br />
<br />
For more information about the POP3 adapter, see the topics in See Also.</td>
</tr>
<tr class="even">
<td><strong>Mail Server</strong></td>
<td>Required. Specify the POP3 mail server that houses the mailbox that will be polled by the POP3 adapter.<br />
<br />
Type: String<br />
<br />
Minimum length: 0<br />
<br />
Maximum length: 256</td>
</tr>
<tr class="odd">
<td><strong>Port</strong></td>
<td>Specify the TCP Port to use for the connection to the specified POP3 server.<br />
<br />
Default value: 0<br />
<br />
Type: Long <strong>Note:</strong> A value of 0 indicates to use the default POP3 port of 110 if Use SSL is False or port 443 if Use SSL is True.</td>
</tr>
<tr class="even">
<td><strong>Authentication Scheme</strong></td>
<td>Specify the type of authentication to use when connecting to the POP3 server.<br />
<br />
Options:<br />
<br />
- Basic<br />
- Digest<br />
- SPA<br />
<br />
Type: String <strong>Note:</strong> When using SPA authentication, the user name must be specified with one of the following formats: Domain accounts must be entered with the syntax &lt;domain name&gt;\&lt;username&gt; Local accounts must be entered with the syntax &lt;machine name&gt;\&lt;username&gt;</td>
</tr>
<tr class="odd">
<td><strong>Password</strong></td>
<td>Specify the password used to authenticate to the POP3 mailbox.<br />
<br />
Type: String<br />
<br />
Minimum length: 0<br />
<br />
Maximum length: 256</td>
</tr>
<tr class="even">
<td><strong>Use SSL</strong></td>
<td>Specify whether to connect to the POP3 server over SSL (TCP Port 443).<br />
<br />
Default value: False<br />
<br />
Type: Boolean</td>
</tr>
<tr class="odd">
<td><strong>User Name</strong></td>
<td>Required. This is the user name used to access the specified mailbox.<br />
<br />
Type: String<br />
<br />
Minimum length: 0<br />
<br />
Maximum length: 256</td>
</tr>
<tr class="even">
<td><strong>Error Threshold</strong></td>
<td>Specify the maximum number of network or protocol errors to wait before shutting down the adapter.<br />
<br />
Default value: 10<br />
<br />
Type: Long<br />
<br />
Minimum value: 0</td>
</tr>
<tr class="odd">
<td><strong>Polling Interval</strong></td>
<td>Specify the interval between attempts to retrieve messages from the POP3 server.<br />
<br />
Default value: 5<br />
<br />
Type: Long<br />
<br />
Minimum value: 2<br />
<br />
Maximum value: 120</td>
</tr>
<tr class="even">
<td><strong>Polling Interval Unit</strong></td>
<td>Specify the unit of measure to be used for the Polling Interval.<br />
<br />
Options:<br />
<br />
- Seconds<br />
- Minutes<br />
- Hours<br />
- Days<br />
- Default value: Minutes<br />
<br />
Type: String</td>
</tr>
</tbody>
</table>


## See Also

[How to Configure a POP3 Receive Handler](https://msdn.microsoft.com/library/aa559164\(v=bts.80\))  
[What Is the POP3 Adapter?](https://msdn.microsoft.com/library/aa547008\(v=bts.80\))

