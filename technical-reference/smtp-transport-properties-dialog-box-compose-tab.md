---
description: "Learn more about: SMTP Transport Properties Dialog Box, Compose Tab"
title: SMTP Transport Properties Dialog Box, Compose Tab
TOCTitle: SMTP Transport Properties Dialog Box, Compose Tab
ms:assetid: 2bfd6bf6-9cce-4c28-a53d-c93efef30c83
ms:mtpsurl: https://msdn.microsoft.com/library/Aa559368(v=BTS.80)
ms:contentKeyID: 51526977
ms.date: 08/30/2017
ms.topic: ui-reference
mtps_version: v=BTS.80
f1_keywords:
- bts10.adaptors.smtp.transport.compose
---

# SMTP Transport Properties Dialog Box, Compose Tab

 

In the **SMTP Transport Properties** dialog box, use the **Compose** tab to configure the send port for the Simple Mail Transfer Protocol (SMTP) adapter.

<table>
<thead>
<tr class="header">
<th><strong>Use this</strong></th>
<th><strong>To do this</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>BizTalk message body part</strong></td>
<td>Specify to use the BizTalk message body part for the body of the e-mail being sent.</td>
</tr>
<tr class="even">
<td><strong>Text</strong></td>
<td>Specify text to be used for the body of the e-mail being sent. Once the Text option is selected you can enter the text for the e-mail body into the text box.<br />
<br />
Maximum Length: 64Kb</td>
</tr>
<tr class="odd">
<td><strong>Charset for the text</strong></td>
<td>Specify the character set to use for encoding the body of the e-mail being sent. This option is only available if the Text option is selected.<br />
<br />
Default value: UTF-8 (65001)</td>
</tr>
<tr class="even">
<td><strong>File</strong></td>
<td>Specify that the contents of a file will be used for the body of the e-mail being sent and specify the path to the file. Once the File option is selected you can click the Ellipses button (…) to browse to the file.<br />
<br />
Maximum path length: 256 characters <strong>Note:</strong> We recommend as a best practice to specify a path on a file share that is accessible from all BizTalk servers in the BizTalk Server group to be used in production.</td>
</tr>
<tr class="odd">
<td><strong>Charset of the file</strong></td>
<td>Specify the character set of the contents of a file that will be used for encoding the body of the e-mail being sent. This option is only available if the File option is selected.<br />
<br />
Default value: UTF-8 (65001)</td>
</tr>
</tbody>
</table>


## See Also

[Restrictions on the SMTP To Property](https://msdn.microsoft.com/library/aa547966\(v=bts.80\))

