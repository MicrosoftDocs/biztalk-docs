---
description: "Learn more about: Configuration Wizard, Runtime Page"
title: Configuration Wizard, Runtime Page
TOCTitle: Configuration Wizard, Runtime Page
ms:assetid: a72538d7-aa60-4374-86e5-951a052d0e00
ms:mtpsurl: https://msdn.microsoft.com/library/Aa577921(v=BTS.80)
ms:contentKeyID: 51530328
ms.date: 08/30/2017
mtps_version: v=BTS.80
f1_keywords:
- bts10.config.wizard.runtime
ms.topic: ui-reference
---

# Configuration Wizard, Runtime Page

 

Use the **Runtime** page to configure the BizTalk Server runtime on this computer.

<table>
<thead>
<tr class="header">
<th>Use this</th>
<th>To do this</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>Enable BizTalk Server runtime components on this computer</strong></td>
<td>Select <strong>Enable BizTalk Server runtime components on this computer</strong> to enable host creation on this computer.</td>
</tr>
<tr class="even">
<td><strong>Create In-Process Host and Instance</strong></td>
<td>Select <strong>Create In-Process Host and Instance</strong> to create a host application on this computer.<br />
<br />
 <strong>Trusted</strong>: Select this if you want to pass the credentials (SSID and/or Party ID) of the sender when submitting messages to the MessageBox database. This is equivalent to creating a trust relationship between the servers.<br />
<br />
 <strong>Host name</strong>: Type the name of the BizTalk Host. By default this is <code>BizTalkServerApplication</code>.</td>
</tr>
<tr class="odd">
<td><strong>Create Isolated Host and Instance</strong></td>
<td>Select <strong>Create Isolated Host and Instance</strong> to create an isolated host application on this computer.<br />
<br />
 <strong>Trusted</strong>: Select this if you want to pass the credentials (SSID and/or Party ID) of the sender when submitting messages to the MessageBox database. This is equivalent to creating a trust relationship between the servers.<br />
<br />
 <strong>Isolated Host name</strong>: Type the name of the BizTalk Host. By default this is <code>BizTalkServerIsolatedHost</code>.</td>
</tr>
<tr class="even">
<td><strong>Windows Service</strong></td>
<td>The Windows Service list provides an editable view of the account used to run the BizTalk Host and Isolated Host Windows Services.</td>
</tr>
<tr class="odd">
<td><strong>Windows Groups</strong></td>
<td>The Windows Groups list provides an editable view of the BizTalk Host and Isolated Hosts Windows groups.</td>
</tr>
</tbody>
</table>


## See Also

[Installation Overview for BizTalk Server 2013 and 2013 R2](https://msdn.microsoft.com/library/jj248688\(v=bts.80\))  
[Getting Started](https://msdn.microsoft.com/library/aa560946\(v=bts.80\))

