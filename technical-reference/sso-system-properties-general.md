---
title: 'SSO System Properties: General'
TOCTitle: 'SSO System Properties: General'
ms:assetid: 5f61cfef-5afa-4a1a-b2ab-959c02d028f2
ms:mtpsurl: https://msdn.microsoft.com/library/Aa560424(v=BTS.80)
ms:contentKeyID: 51528390
ms.date: 08/30/2017
mtps_version: v=BTS.80
f1_keywords:
- bts10.esso.system.properties.general
---

# SSO System Properties: General

 

This screen displays general properties for the overall SSO system.

<table>
<thead>
<tr class="header">
<th>Use this</th>
<th>To do this</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>Master secret server</strong></td>
<td>The master secret server is the Enterprise Single Sign-On (SSO) server that stores the master secret (encryption key). The master secret server generates the master secret when an SSO Administrator requests it. The master secret server stores the encrypted master secret in the registry. Only SSO Administrators can access the master secret.</td>
</tr>
<tr class="even">
<td><strong>Ticket timeout (in minutes)</strong></td>
<td>This property specifies the length of time for which a ticket that SSO issues is valid. To satisfy most of the scenarios in an enterprise that use SSO, the default ticket time-out is 2 minutes. The SSO Administrator can change this based on the application requirements.</td>
</tr>
<tr class="odd">
<td><strong>Credential cache timeout (in minutes)</strong></td>
<td>This property specifies the credential cache time-out for all SSO servers. SSO servers cache the credentials after the first lookup. By default, the credential cache time-out is 60 minutes. The SSO Administrator can change this to a suitable value based on the security requirements.</td>
</tr>
</tbody>
</table>


## See Also

[Implementing Enterprise Single Sign-On](https://msdn.microsoft.com/library/aa558712\(v=bts.80\))

