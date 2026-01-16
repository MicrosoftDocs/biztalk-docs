---
description: "Learn more about: Adapter Handler Properties Dialog Box"
title: Adapter Handler Properties Dialog Box
TOCTitle: Adapter Handler Properties Dialog Box
ms:assetid: e67f67df-cf15-4c2f-bbb8-5a8d6ad8556d
ms:mtpsurl: https://msdn.microsoft.com/library/Aa561639(v=BTS.80)
ms:contentKeyID: 51533025
ms.date: 08/30/2017
mtps_version: v=BTS.80
f1_keywords:
- bts10.admin.adapterhandler.properties.general
ms.topic: ui-reference 
---

# Adapter Handler Properties Dialog Box

 

Use the **Adapter Handler Properties** window to create and configure new adapter instances and to review and configure information for existing adapter instances. An adapter handler is a host that is responsible for executing the adapter and contains properties for a specific instance of an adapter.

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
<td><strong>Adapter name</strong></td>
<td>Displays the name of the adapter with which the adapter handler is associated. Default adapters are named for the transport protocol they represent.</td>
</tr>
<tr class="even">
<td><strong>Properties</strong></td>
<td>Click to display the … <strong>&lt;Adapter&gt; Transport Properties</strong> window, where you can configure adapter properties.</td>
</tr>
<tr class="odd">
<td><strong>Host name</strong></td>
<td>From the drop-down list, select the name of the BizTalk Host with which the adapter handler is associated. When the adapter handler is created, BizTalk Server assigns the default host to run it. You can change that setting in this box.</td>
</tr>
<tr class="even">
<td><strong>Direction</strong></td>
<td>Displays the direction of communication for which the adapter is configured; specifically, whether the adapter supports a send port or a receive port.</td>
</tr>
<tr class="odd">
<td><strong>Make this the default handler</strong></td>
<td>Select this check box to make the current adapter send handler the default. This check box is visible only for send handlers.</td>
</tr>
<tr class="even">
<td><strong>Description</strong></td>
<td>Type any text that is useful to you.</td>
</tr>
</tbody>
</table>


## See Also

[Using Adapters](https://msdn.microsoft.com/library/aa578103\(v=bts.80\))  
[Adapter Groups and Group Adapters](https://msdn.microsoft.com/library/aa744384\(v=bts.80\))

