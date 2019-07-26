---
title: Party Resolution Pipeline Component Properties
TOCTitle: Party Resolution Pipeline Component Properties
ms:assetid: 39f63895-f24d-4578-8031-689a05ebc94e
ms:mtpsurl: https://msdn.microsoft.com/library/Aa559640(v=BTS.80)
ms:contentKeyID: 51527415
ms.date: 08/30/2017
mtps_version: v=BTS.80
f1_keywords:
- Microsoft.BizTalk.Component.PartyRes
---

# Party Resolution Pipeline Component Properties

 

Use the Party resolution pipeline component to map the sender certificate or the sender security ID (SID) to the corresponding SourcePartyID.

The Party resolution pipeline component is intended for use in the ResolveParty stage of a Receive pipeline.

The properties of the Party resolution pipeline component can be set in the Properties window of Microsoft Visual Studio. To display the Properties window, select the component, right-click and select **Properties**, or press F4. The following table contains the configurable Party resolution pipeline component properties.

<table>
<thead>
<tr class="header">
<th>Use this</th>
<th>To do this</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>Resolve party by certificate</strong></td>
<td>Set this property to True if you want to enable party resolution based on the subject of the client's certificate of the party from where the messages are received.<br />
<br />
Default Value: True</td>
</tr>
<tr class="even">
<td><strong>Resolve party by SID</strong></td>
<td>Set this property to True if you want to enable party resolution based on the security ID of the sender account.<br />
<br />
If both properties are set to True, then the <strong>Resolve Party by Certificate</strong> property takes precedence over <strong>Resolve party by SID</strong> property, meaning that if both the certificate and the SID are available, then certificate subject is used. If the party cannot be resolved using the certificate subject, the process falls back to the resolution based on the SID.<br />
<br />
Default Value: True</td>
</tr>
</tbody>
</table>


## See Also

[Using Pipeline Designer](https://msdn.microsoft.com/library/aa578392\(v=bts.80\))  
[How to Configure the Party Resolution Pipeline Component](https://msdn.microsoft.com/library/aa547385\(v=bts.80\))  
[Party Resolution Pipeline Component](https://msdn.microsoft.com/library/aa560645\(v=bts.80\))

