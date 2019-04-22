---
title: Policy Properties Dialog Box
TOCTitle: Policy Properties Dialog Box
ms:assetid: b44d2456-7079-4a08-89f5-a79029178ee6
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa578202(v=BTS.80)
ms:contentKeyID: 51530683
ms.date: 08/30/2017
mtps_version: v=BTS.80
f1_keywords:
- bts10.admin.policy.properties
---

# Policy Properties Dialog Box

 

Use the **Policy Properties** window to view the rule sets that have been added to the application and to configure tracking options. Policy properties are defined in the Microsoft Business Rules Composer.

## General Tab

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
<td><strong>Name</strong></td>
<td>Displays the policy name.</td>
</tr>
<tr class="even">
<td><strong>Version</strong></td>
<td>Displays the policy version.</td>
</tr>
<tr class="odd">
<td><strong>State</strong></td>
<td>Indicates whether the policy is unpublished (in process of development), published (protected from further change) or deployed (placed into production).</td>
</tr>
<tr class="even">
<td><strong>Description</strong></td>
<td>Displays notes about the policy. This description is specified in the rule composer or through the rules engine.</td>
</tr>
</tbody>
</table>


## Tracking Tab

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
<td><strong>Track - Fact activity</strong></td>
<td>Select this check box to track the instance data on which the policy operates.</td>
</tr>
<tr class="even">
<td><strong>Track - Condition evaluation</strong></td>
<td>Select this check box to track the true/false results of conditions in the selected policy.</td>
</tr>
<tr class="odd">
<td><strong>Track - Rule firings</strong></td>
<td>Select this check box to track the actions triggered as a result of the policy.</td>
</tr>
<tr class="even">
<td><strong>Track - Agenda updates</strong></td>
<td>Select this check box to track updates to the agenda. The agenda contains a list of actions that are &quot;true&quot; and need to fire.</td>
</tr>
</tbody>
</table>



> [!NOTE]
> <P>You can view tracked rules and policies during runtime using the queries on the Group Hub page.</P>



## See Also

[Importing BizTalk Applications, Bindings, and Policies](https://msdn.microsoft.com/library/aa560565\(v=bts.80\))

