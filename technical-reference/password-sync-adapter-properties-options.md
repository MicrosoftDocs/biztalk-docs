---
title: 'Password Sync Adapter Properties: Options'
TOCTitle: 'Password Sync Adapter Properties: Options'
ms:assetid: 5ae65a82-cc7b-46ff-a2be-f138e7e8992e
ms:mtpsurl: https://msdn.microsoft.com/library/Aa560328(v=BTS.80)
ms:contentKeyID: 51528277
ms.date: 08/30/2017
mtps_version: v=BTS.80
f1_keywords:
- bts10.esso.pws.properties.options
---

# Password Sync Adapter Properties: Options

 

Use this dialog box to view or change options for the Password Sync Adapter.

<table>
<thead>
<tr class="header">
<th>Use this</th>
<th>To do this</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>Enabled</strong></td>
<td>Determines whether the adapter is enabled.</td>
</tr>
<tr class="even">
<td><strong>Receive password changes from adapter</strong></td>
<td>Determines whether the adapter is allowed to receive external password changes. Default is not selected.</td>
</tr>
<tr class="odd">
<td><strong>Verify old password</strong></td>
<td>Determines whether the adapter will verify the old password when an external password change is received. If this option is selected then with an external password change the external adapter must supply the old external password as well as the new external password. The old external password is then compared with the existing external password in the Enterprise Single Sign-On (SSO) database for that external account. If they match, the password change is accepted. If they do not match, the password change is rejected. Default is selected.</td>
</tr>
<tr class="even">
<td><strong>Change Windows password</strong></td>
<td>Determines whether the Windows password will also be changed in Active Directory when an external password change is received (full sync). Default is not selected.</td>
</tr>
<tr class="odd">
<td><strong>Send Windows password changes to adapter</strong></td>
<td>Determines whether Windows password changes will be sent to the external adapter. Default is not selected.</td>
</tr>
<tr class="even">
<td><strong>Send old password to adapter</strong></td>
<td>If selected, the old password value (from the SSO database) will also be sent to the external adapter as well as the new password value. Some external systems might require both the old and new password values to change the password. Default is not selected.</td>
</tr>
<tr class="odd">
<td><strong>Allow mapping conflicts</strong></td>
<td>Determines whether the adapter will allow mapping conflicts.<br />
<br />
A mapping conflict occurs when mappings are not unique. In a single SSO Individual application, mappings are always one-to-one: one Windows account is mapped to exactly one external account and vice versa.<br />
<br />
However, it is possible to assign more than one application to an adapter. Thus, it is possible to have a mapping in one application that conflicts with a mapping in the other.<br />
<br />
This purpose of this option is to prevent this from occurring. It is more secure to not allow mapping conflicts unless there is a specific, well understood requirement for this behavior.<br />
<br />
Default is not selected.</td>
</tr>
</tbody>
</table>


## See Also

[Implementing Enterprise Single Sign-On](https://msdn.microsoft.com/library/aa558712\(v=bts.80\))

