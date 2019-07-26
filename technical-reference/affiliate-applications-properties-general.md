---
title: 'Affiliate Applications Properties: General'
TOCTitle: 'Affiliate Applications Properties: General'
ms:assetid: d0026e4d-38a8-46dc-9788-40391be41c91
ms:mtpsurl: https://msdn.microsoft.com/library/Aa578509(v=BTS.80)
ms:contentKeyID: 51531479
ms.date: 08/30/2017
mtps_version: v=BTS.80
f1_keywords:
- bts10.esso.affapp.properties.general
---

# Affiliate Applications Properties: General

 

Use this dialog box to view or change general properties for the affiliate application.

<table>
<thead>
<tr class="header">
<th>Use this</th>
<th>To do this</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>Application type</strong></td>
<td>Enterprise Single Sign-On (SSO) defines several different application types. The different application types support different types of mappings between the Windows account and the account on the non-Windows system.<br />
<br />
The application types are:<br />
<br />
 <strong>Individual</strong>: Individual applications support one-to-one mappings between the Windows account and the non-Windows account. In an Individual type application, one Windows account is mapped to one, and only one, non-Windows account. The mapping can be used in either direction, from Windows to non-Windows, or from non-Windows to Windows, or both, depending on the flags that have been set for this application. Thus, Individual applications may be used for Windows initiated SSO, Host initiated SSO, or both.<br />
<br />
 <strong>Group</strong>: Group mapping consists of mapping a Windows group, which contains multiple Windows users, to a single account in the affiliate application.<br />
<br />
You can also specify multiple accounts for the SSO Application Users role. Each account that you specify can be associated with an external account.<br />
<br />
For example, it is possible to map a domain user (domain\userA) to one set of external credentials (ExternalUser1). The same domain\userA could also be a member of Domain Group (domain\group1) and this group could be mapped to a different set of external credentials (ExternalUser2). In this case, it is important that the administrator (who must be an Application Administrator or above) specifies the correct order for the Application Users accounts.<br />
<br />
The mapping for the first account (in the Order) of which the caller is a member is the one that will be used. In this case, if mapping for domain\userA to ExternalUser1 is set to Order 0, SSO will return this set of credentials for domain\UserA.<br />
<br />
Only an application administrator, SSO affiliate administrator, or SSO administrator can create a group mapping.<br />
<br />
You cannot specify the same group application for Windows-initiated SSO and Host-initiated SSO.<br />
<br />
 <strong>Host Group</strong>: Host Group applications are conceptually the reverse of Group applications. They support mappings between a defined group of non-Windows accounts to a single Windows account. The single Windows account that will be used by the non-Windows accounts is defined by the Application Users account for the application. The group of non-Windows accounts that is allowed to access this application is defined by creating a mapping for each non-Windows account. Host Group applications may only be used for Host initiated SSO. <strong>Important:</strong> Mappings can be created only for Windows domain accounts. Local accounts cannot be mapped. <strong>Important:</strong> When you use group mappings, the members of the group can obtain the credential information for the group mapping.</td>
</tr>
<tr class="even">
<td><strong>Application name</strong></td>
<td>Name of the affiliate application. You cannot change this property after you create the affiliate application.</td>
</tr>
<tr class="odd">
<td><strong>Description</strong></td>
<td>Brief description of the affiliate application.</td>
</tr>
<tr class="even">
<td><strong>Contact information</strong></td>
<td>The main contact for this affiliate application that users can use. (Can be an e-mail address.)</td>
</tr>
<tr class="odd">
<td><strong>Allow local accounts for access accounts</strong></td>
<td>Determines whether you allow the use of local groups and accounts in the SSO system. You should select this option only in single-computer scenarios.</td>
</tr>
<tr class="even">
<td><strong>Use SSO Affiliate Admin Accounts for Application Admin accounts</strong></td>
<td>Determines whether the Application Admin accounts will be the same as the SSO Affiliate Admin accounts. Default is not selected.</td>
</tr>
</tbody>
</table>


## See Also

[Implementing Enterprise Single Sign-On](https://msdn.microsoft.com/library/aa558712\(v=bts.80\))

