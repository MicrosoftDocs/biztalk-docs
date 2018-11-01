---
title: Group Properties Dialog Box
TOCTitle: Group Properties Dialog Box
ms:assetid: 0e9524fe-5a9b-44c6-bfc6-e0656848483b
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa547381(v=BTS.80)
ms:contentKeyID: 51526238
ms.date: 08/30/2017
mtps_version: v=BTS.80
f1_keywords:
- bts10.admin.group.properties
---

# Group Properties Dialog Box

 

Use the **Group Properties** window to view or modify BizTalk Group properties.

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
<td>Type the group name. The name in this box appears next to the <strong>Group</strong> node in the Console tree, along with the server name and the management database name.</td>
</tr>
<tr class="even">
<td><strong>Server</strong></td>
<td>Displays the server on which the management database is physically stored.</td>
</tr>
<tr class="odd">
<td><strong>Database</strong></td>
<td>Displays the management database on which all configuration settings for this group are stored.</td>
</tr>
<tr class="even">
<td><strong>SSO Server name</strong></td>
<td>Type the name of the Enterprise Single Sign-On server that this computer will use to access the configuration information for the adapters. This is the name of the SSO Server used to connect to the SSO database.</td>
</tr>
<tr class="odd">
<td><strong>BizTalk Administrator Group</strong></td>
<td>Displays the name of the administrators group that has rights to manage the BizTalk Server environment after installation.</td>
</tr>
<tr class="even">
<td><strong>BizTalk Operators Group</strong></td>
<td>Displays the name of the operators group that has rights to view configuration, run queries, and perform machine maintenance and basic application monitoring.</td>
</tr>
<tr class="odd">
<td><strong>BizTalk B2B Operators Group</strong></td>
<td>Displays the name of the B2B operators group that has rights to view and manage party(Trading Partner) data including EDI/AS2 settings for the parties.</td>
</tr>
<tr class="even">
<td></td>
<td></td>
</tr>
<tr class="odd">
<td></td>
<td></td>
</tr>
</tbody>
</table>


## Databases Tab

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
<td><strong>Databases</strong></td>
<td>Displays the names of all databases in the application and the servers on which they reside, as specified during configuration.</td>
</tr>
</tbody>
</table>


## Certificate Tab

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
<td><strong>Signature certificate - Common Name</strong></td>
<td>Displays the common name of the selected certificate.</td>
</tr>
<tr class="even">
<td><strong>Signature certificate - Thumbprint</strong></td>
<td>Displays the thumbprint of the private key certificate that is used to digitally sign outbound messages from this group. The certificate thumbprint has the format HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH, where H is a hexadecimal digit (a number 0 to 9 or a letter A to F).</td>
</tr>
<tr class="odd">
<td><strong>Signature certificate - Remove certificate</strong></td>
<td>Click to remove the displayed certificate.</td>
</tr>
<tr class="even">
<td><strong>Signature certificate - Browse</strong></td>
<td>Click to display the <strong>Select Certificate</strong> dialog box, where you select the signature certificate you want to use with the group.</td>
</tr>
</tbody>
</table>


## See Also

[BizTalk Groups](https://msdn.microsoft.com/en-us/library/aa559010\(v=bts.80\))  
[How to Add a Server to a Group](https://msdn.microsoft.com/en-us/library/aa560729\(v=bts.80\))  
[How to Remove a Server from a Group](https://msdn.microsoft.com/en-us/library/aa561173\(v=bts.80\))  
[Managing Groups](https://msdn.microsoft.com/en-us/library/aa560678\(v=bts.80\))  
[How to Modify Group Properties](https://msdn.microsoft.com/en-us/library/aa560305\(v=bts.80\))  
[How to Export Bindings for a BizTalk Group](https://msdn.microsoft.com/en-us/library/aa560143\(v=bts.80\))  
[How to Move a Server from One Group to Another](https://msdn.microsoft.com/en-us/library/aa559752\(v=bts.80\))

