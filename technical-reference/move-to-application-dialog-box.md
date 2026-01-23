---
description: "Learn more about: Move to Application Dialog Box"
title: Move to Application Dialog Box
TOCTitle: Move to Application Dialog Box
ms:assetid: a12e2b40-61df-4baf-b5e1-55db51828e89
ms:mtpsurl: https://msdn.microsoft.com/library/Aa577687(v=BTS.80)
ms:contentKeyID: 51530096
ms.date: 08/30/2017
mtps_version: v=BTS.80
ms.topic: ui-reference
f1_keywords:
- bts10.admin.movetoapplication
---

# Move to Application Dialog Box

 

Use the **Move to Application** dialog box to move artifacts from the default application in the Administrative Console to separate applications. During an upgrade to BizTalk Server, artifacts that existed in earlier versions of BizTalk Server are placed into the default application. After the upgrade, the **Move to Application** dialog box enables you to distribute these artifacts among different applications that reflect your business topology. You can also use the **Move to Application** dialog box to move artifacts between applications at any time.

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
<td><strong>Destination application</strong></td>
<td>From the drop-down list, select the application to which you want to move the artifacts you selected in the Administration Console details pane.</td>
</tr>
<tr class="even">
<td><strong>Moving Artifacts - Name</strong></td>
<td>Displays a list of artifacts that will be moved. The list contains all artifacts that were selected when you opened the Move to Application dialog box and any dependent artifacts whose relationship with other artifacts in the list would be violated by the move.</td>
</tr>
<tr class="odd">
<td><strong>Moving Artifacts - Dependency Details</strong></td>
<td>Summarizes reasons why the artifact will be moved. Possible reasons include:<br />
<br />
- <strong>(Artifact1 is) Dependent On &lt;Artifact2&gt;</strong>. Artifact1 and Artifact2 must share the same application, or Artifact2 must be in an application referenced by the application that contains Artifact1. You can avoid moving Artifact1 when moving Artifact2 by adding a reference from the destination application to the application that contains Artifact1.<br />
- <strong>(Artifact1 is) Required By &lt;Artifact2&gt;</strong>. Artifact1 and Artifact2 must share the same application, or Artifact1 must be in an application referenced by the application that contains Artifact2. You can avoid moving Artifact1 when moving Artifact2 by adding a reference from the application that contains Artifact1 to the destination application.<br />
- <strong>(Artifact1 is) [Packaged In/Contains/Assembled with] &lt;Artifact2&gt;</strong>. Artifact1 and Artifact2, though displayed separately in the Management Console, are actually part of a single object and must be kept in the same application. They will always move together.<br />
- <strong>(Artifact1 is) Selected by User</strong>. The artifact is one that you selected to move.</td>
</tr>
</tbody>
</table>

