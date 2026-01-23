---
description: "Learn more about: Create New Affiliate Application Wizard: General"
title: 'Create New Affiliate Application Wizard: General'
TOCTitle: 'Create New Affiliate Application Wizard: General'
ms:assetid: cfed85cd-794a-460e-a75b-88799656b005
ms:mtpsurl: https://msdn.microsoft.com/library/Aa578508(v=BTS.80)
ms:contentKeyID: 51531474
ms.date: 08/30/2017
mtps_version: v=BTS.80
f1_keywords:
- bts10.esso.newapp.wizard.general
ms.topic: ui-reference
---

# Create New Affiliate Application Wizard: General

 

Specify general properties for the new Affiliate Application.

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
 <strong>Group</strong>:Group applications support mappings between one or more Windows groups or users to one single non-Windows account. The Application Users account is used to define the Windows groups or users that will be used for this Group application.<br />
<br />
 <strong>Host Group</strong>: Host Group applications are conceptually the reverse of Group applications. They support mappings between a defined group of non-Windows accounts to a single Windows account. The single Windows account that will be used by the non-Windows accounts is defined by the Application Users account for the application. The group of non-Windows accounts that is allowed to access this application is defined by creating a mapping for each non-Windows account. Host Group applications may only be used for Host initiated SSO.</td>
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
<td>Determines whether you allow the use of local groups and accounts in the SSO system. You should only select this option in single-computer scenarios.</td>
</tr>
<tr class="even">
<td><strong>Use SSO Affiliate Admin Accounts for Application Admin accounts</strong></td>
<td>Determines whether the Application Admin Accounts will be the same as the SSO Affiliate Admin Accounts. Default is not selected.</td>
</tr>
</tbody>
</table>


## See Also

[Implementing Enterprise Single Sign-On](https://msdn.microsoft.com/library/aa558712\(v=bts.80\))

