---
title: SMTP Transport Properties Dialog Box, General Tab
TOCTitle: SMTP Transport Properties Dialog Box, General Tab
ms:assetid: 3c38713b-853b-4f35-bce1-795b73e07d43
ms:mtpsurl: https://msdn.microsoft.com/library/Aa559688(v=BTS.80)
ms:contentKeyID: 51527421
ms.date: 08/30/2017
mtps_version: v=BTS.80
f1_keywords:
- bts10.adaptors.smtp.transport.general
---

# SMTP Transport Properties Dialog Box, General Tab

 

In the **SMTP Transport Properties** dialog box, use the **General** tab to configure the send port for the Simple Mail Transfer Protocol (SMTP) adapter.

<table>
<thead>
<tr class="header">
<th>Use this</th>
<th>To do this</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>To</strong></td>
<td>Required. Specify the e-mail address for where to send messages.<br />
<br />
You can specify more than one address.<br />
<br />
Maximum length: 256</td>
</tr>
<tr class="even">
<td><strong>CC</strong></td>
<td>Specify the e-mail address to send the carbon copy of the message(s).<br />
<br />
You can specify more than one address.<br />
<br />
Maximum length: 1,024</td>
</tr>
<tr class="odd">
<td><strong>Subject</strong></td>
<td>Specify the subject header for the message(s).<br />
<br />
Minimum length: 0<br />
<br />
Maximum length: 256</td>
</tr>
<tr class="even">
<td><strong>Notification</strong></td>
<td>Specify the type of notification receipt. You can select one or both types of receipts. Notification receipt types are:<br />
<br />
- Read Receipt. Confirmation e-mail is sent when the message is read.<br />
- Delivery Receipt. Confirmation e-mail is sent when the message is delivered.</td>
</tr>
</tbody>
</table>


## See Also

[Restrictions on the SMTP To Property](https://msdn.microsoft.com/library/aa547966\(v=bts.80\))

