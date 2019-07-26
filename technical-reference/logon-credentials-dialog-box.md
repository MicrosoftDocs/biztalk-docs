---
title: Logon Credentials Dialog Box
TOCTitle: Logon Credentials Dialog Box
ms:assetid: 3a96bd80-3959-456c-b3a3-aa3ffc1a9857
ms:mtpsurl: https://msdn.microsoft.com/library/Aa559652(v=BTS.80)
ms:contentKeyID: 51527432
ms.date: 08/30/2017
mtps_version: v=BTS.80
f1_keywords:
- bts10.admin.hostinstance.properties.general.logon
---

# Logon Credentials Dialog Box

 

Use the **Logon Credentials** dialog box to supply the account name and password of the SQL account under which the host instance will run. When you set up this account, BizTalk Server adds the account to the "Log on as a service" security policy.

## UIElement List

<table>
<thead>
<tr class="header">
<th>Use this</th>
<th>To do this</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>Logon</strong></td>
<td>Type the domain and account name of the SQL account under which the host instance will run. The account name specified must be a member of the BizTalk Server Host Windows group.</td>
</tr>
<tr class="even">
<td><strong>Password</strong></td>
<td>Type the password that the host instance SQL account will use to authenticate the host instance on the BizTalk server.</td>
</tr>
</tbody>
</table>


## See Also

[Host Instances](https://msdn.microsoft.com/library/aa560673\(v=bts.80\))  
[Managing BizTalk Hosts and Host Instances](https://msdn.microsoft.com/library/aa561042\(v=bts.80\))  
[How to Update the SSO Database](https://msdn.microsoft.com/library/aa559867\(v=bts.80\))

