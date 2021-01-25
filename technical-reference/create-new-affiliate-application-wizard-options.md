---
description: "Learn more about: Create New Affiliate Application Wizard: Options"
title: 'Create New Affiliate Application Wizard: Options'
TOCTitle: 'Create New Affiliate Application Wizard: Options'
ms:assetid: 5baebd21-cf3a-4b84-af00-1e20ca4afb97
ms:mtpsurl: https://msdn.microsoft.com/library/Aa560351(v=BTS.80)
ms:contentKeyID: 51528290
ms.date: 08/30/2017
mtps_version: v=BTS.80
f1_keywords:
- bts10.esso.newapp.wizard.options
---

# Create New Affiliate Application Wizard: Options

 

Specify options for the new Affiliate Application.

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
<td>The status (enabled/disabled) of this affiliate application.</td>
</tr>
<tr class="even">
<td><strong>Allow Windows initiated SSO</strong></td>
<td>Select if Windows initiated Enterprise Single Sign-On (SSO) is allowed. Default is selected.</td>
</tr>
<tr class="odd">
<td><strong>Disable credential cache</strong></td>
<td>The SSO server stores credentials in a cache to expedite access. Default is not selected.</td>
</tr>
<tr class="even">
<td><strong>Tickets allowed</strong></td>
<td>Determines whether the SSO system uses tickets for this affiliate application. You must be an SSO administrator to select this option.</td>
</tr>
<tr class="odd">
<td><strong>Validate tickets</strong></td>
<td>Determines whether the SSO system validates tickets when the user redeems them. You must be an SSO Administrator to select this option.</td>
</tr>
<tr class="even">
<td><strong>Timeout tickets</strong></td>
<td>Determines whether tickets have an expiration time. Default is checked. Unless it is required, do not disable ticket time-outs. You must be an SSO Administrator to set this option.</td>
</tr>
<tr class="odd">
<td><strong>Ticket timeout (in minutes)</strong></td>
<td>Specifies a ticket time-out specific to the affiliate application. If ticketing is enabled for this application and this property is not, the time-out specified at the SSO System (Global) level is used. You must be an SSO Administrator to set this option.</td>
</tr>
<tr class="even">
<td><strong>Allow host initiated SSO</strong></td>
<td>Select this if Host initiated SSO is allowed. Default is not selected.</td>
</tr>
<tr class="odd">
<td><strong>Verify external credentials</strong></td>
<td>Select to verify external credentials.</td>
</tr>
<tr class="even">
<td><strong>Direct Password Sync from Windows</strong></td>
<td>Select to allow Direct Password Sync for this application.</td>
</tr>
<tr class="odd">
<td><strong>Application users cannot create mappings</strong></td>
<td>Increases system security by allowing only administrators to create mappings.</td>
</tr>
</tbody>
</table>


## See Also

[Implementing Enterprise Single Sign-On](https://msdn.microsoft.com/library/aa558712\(v=bts.80\))

