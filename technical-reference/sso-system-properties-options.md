---
description: "Learn more about: SSO System Properties: Options"
title: 'SSO System Properties: Options'
TOCTitle: 'SSO System Properties: Options'
ms:assetid: d8df3e47-49e4-4acc-9b8e-7b4a2e5de21b
ms:mtpsurl: https://msdn.microsoft.com/library/Aa578685(v=BTS.80)
ms:contentKeyID: 51531622
ms.date: 08/30/2017
mtps_version: v=BTS.80
ms.topic: ui-reference
f1_keywords:
- bts10.esso.system.properties.options
---

# SSO System Properties: Options

 

This screen displays options for the overall Enterprise Single Sign-On (SSO) system.

<table>
<thead>
<tr class="header">
<th>Use this</th>
<th>To do this</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>Allow tickets</strong></td>
<td>Determines whether tickets are allowed at the system level. Only an SSO Administrator can configure tickets at the SSO system level and at the Affiliate Application level.<br />
<br />
If ticketing is disabled at the system level, it cannot be used at the Affiliate Application level either. It is possible to enable tickets at the system level and disable them at the Affiliate Application level.</td>
</tr>
<tr class="even">
<td><strong>Allow host initiated SSO</strong></td>
<td>By default, host initiated Single Sign-On is not enabled in the Single Sign-On system, and must be enabled by the SSO Administrator.</td>
</tr>
<tr class="odd">
<td><strong>From Windows to adapters</strong></td>
<td>Determines whether Windows password changes (in Active Directory) will be sent to password sync adapters. Default is not selected.</td>
</tr>
<tr class="even">
<td><strong>From adapters to SSO database (partial sync)</strong></td>
<td>Determines whether external password changes received from password sync adapters will cause the password to be changed in the SSO database. Default is not selected.</td>
</tr>
<tr class="odd">
<td><strong>From adapters to Windows (full sync)</strong></td>
<td>Determines whether external password changes received from password sync adapters will cause the Windows password to be changed in Active Directory. Default is not selected.</td>
</tr>
</tbody>
</table>


## See Also

[Implementing Enterprise Single Sign-On](https://msdn.microsoft.com/library/aa558712\(v=bts.80\))

