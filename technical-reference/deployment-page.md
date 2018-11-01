---
title: Deployment Page
TOCTitle: Deployment Page
ms:assetid: cde65d26-8bff-4bf5-bcc3-3f5301be5e1b
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa578469(v=BTS.80)
ms:contentKeyID: 51531312
ms.date: 08/30/2017
mtps_version: v=BTS.80
f1_keywords:
- bts10.projectsystem.deployment
---

# Deployment Page

 

Use the **Deployment** page to provide project deployment information.

<table>
<thead>
<tr class="header">
<th>Use this</th>
<th>To do this</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>Application Name</strong></td>
<td>Specify the BizTalk application in which to deploy the assembly.</td>
</tr>
<tr class="even">
<td><strong>Configuration Database</strong></td>
<td>Select a Configuration database for deployment of your project. <strong>Note:</strong> The BizTalk Management database is also referred to as the BizTalk Configuration database.</td>
</tr>
<tr class="odd">
<td><strong>Server</strong></td>
<td>Select a server from the drop-down list to select a location to deploy your BizTalk solution.</td>
</tr>
<tr class="even">
<td><strong>Redeploy</strong></td>
<td>Select True from the drop-down list to redeploy a configuration.<br />
<br />
Default value: True<br />
<br />
Type: Boolean</td>
</tr>
<tr class="odd">
<td><strong>Install to Global Assembly Cache</strong></td>
<td>Select True from the drop-down list to register the assembly in the global assembly cache (GAC).<br />
<br />
Default value: True<br />
<br />
Type: Boolean</td>
</tr>
<tr class="even">
<td><strong>Restart Host Instances</strong></td>
<td>Specifies whether to restart all BizTalk in-process host instances on the local machine. This can be useful when debugging.</td>
</tr>
<tr class="odd">
<td><strong>Enable Unit Testing</strong></td>
<td>Specifies whether to enable unit testing for the project. For more information see: <a href="https://msdn.microsoft.com/en-us/library/dd257907(v=bts.80)">Unit Testing with BizTalk Server Projects</a>.</td>
</tr>
</tbody>
</table>


## See Also

[Project Designer: Deployment Tab](https://msdn.microsoft.com/en-us/library/aa560343\(v=bts.80\))

