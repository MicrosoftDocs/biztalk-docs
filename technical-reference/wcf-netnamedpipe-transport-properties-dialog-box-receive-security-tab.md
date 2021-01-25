---
description: "Learn more about: WCF-NetNamedPipe Transport Properties Dialog Box, Receive, Security Tab"
title: WCF-NetNamedPipe Transport Properties Dialog Box, Receive, Security Tab
TOCTitle: WCF-NetNamedPipe Transport Properties Dialog Box, Receive, Security Tab
ms:assetid: 702200bf-70c8-45e1-a220-ecaee474158e
ms:mtpsurl: https://msdn.microsoft.com/library/Bb226347(v=BTS.80)
ms:contentKeyID: 51528849
ms.date: 08/30/2017
mtps_version: v=BTS.80
f1_keywords:
- bts10.adapters.wcf-netnamedpipe.transport.receive.security
---

# WCF-NetNamedPipe Transport Properties Dialog Box, Receive, Security Tab

 

Use the **Security** tab to define the security capabilities of the WCF-NetNamedPipe receive adapter.

<table>
<thead>
<tr class="header">
<th>Use this</th>
<th>To do this</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>Security mode</strong></td>
<td>Specify the type of security that is applied to this binding. Valid values include the following:<br />
<br />
- <strong>None</strong>: This disables security.<br />
- <strong>Transport</strong>: Security is provided using underlying transport based security. It is possible to control the protection level with this mode.<br />
<br />
The default value is <strong>Transport</strong>.</td>
</tr>
<tr class="even">
<td><strong>Transport protection level</strong></td>
<td>Define protection level of the named pipe. Signing messages mitigates the risk of a third party tampering with the message while it is being transferred. Encryption provides data-level privacy during transport. Valid values include the following:<br />
<br />
- <strong>None</strong>: No protection.<br />
- <strong>Sign</strong>: Messages are signed.<br />
- <strong>EncryptAndSign</strong>: Messages are encrypted and signed.<br />
<br />
The default value is <strong>EncryptAndSign</strong>.</td>
</tr>
<tr class="odd">
<td><strong>Use Single Sign-On</strong></td>
<td>Specify whether to use Single Sign-On to retrieve client credentials to issue an SSO ticket.<br />
<br />
The default value is cleared.</td>
</tr>
</tbody>
</table>


## See Also

[How to Configure a WCF-NetNamedPipe Receive Location](https://msdn.microsoft.com/library/bb259943\(v=bts.80\))

