---
description: "Learn more about: SMTP Transport Properties Dialog Box, Attachments Tab"
title: SMTP Transport Properties Dialog Box, Attachments Tab
TOCTitle: SMTP Transport Properties Dialog Box, Attachments Tab
ms:assetid: d0bba641-1112-4770-8e85-6e0fe74c0d3f
ms:mtpsurl: https://msdn.microsoft.com/library/Aa578523(v=BTS.80)
ms:contentKeyID: 51531497
ms.date: 08/30/2017
ms.topic: ui-reference
mtps_version: v=BTS.80
f1_keywords:
- bts10.adaptors.smtp.transport.attachments
---

# SMTP Transport Properties Dialog Box, Attachments Tab

 

In the **SMTP Transport Properties** dialog box, use the **Attachments** tab to configure the send port for the Simple Mail Transfer Protocol (SMTP) adapter.

<table>
<thead>
<tr class="header">
<th>Use this</th>
<th>To do this</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>Remaining BizTalk message parts</strong></td>
<td>Specify how BizTalk message parts are attached to the e-mail message.<br />
<br />
Options:<br />
<br />
- Do not attach parts<br />
- Attach only body part<br />
- Attach all parts<br />
<br />
Default value: Do not attach body parts.</td>
</tr>
<tr class="even">
<td><strong>Add</strong></td>
<td>Specify a file or files to attach to the e-mail message. After clicking the Add button you can browse to select a file and add it to the list of files to be attached.<br />
<br />
Maximum path length: 256 characters <strong>Note:</strong> We recommend as a best practice to specify a path on a file share that is accessible from all BizTalk servers in the BizTalk Server group to be used in production.</td>
</tr>
<tr class="odd">
<td><strong>Remove</strong></td>
<td>Removes the selected file from the list of files to be attached to the e-mail message.</td>
</tr>
</tbody>
</table>


## See Also

[Restrictions on the SMTP To Property](https://msdn.microsoft.com/library/aa547966\(v=bts.80\))

