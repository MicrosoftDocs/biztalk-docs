---
description: "Learn more about: <Host Name> Properties Dialog Box, WCF Extensions Tab (WCF-Custom or WCF-CustomIsolated Adapter Receive Handler)"
title: <Host Name> Properties Dialog Box, WCF Extensions Tab (WCF-Custom or WCF-CustomIsolated Adapter Receive Handler)
TOCTitle: <Host Name> Properties Dialog Box, WCF Extensions Tab (WCF-Custom or WCF-CustomIsolated Adapter Receive Handler)
ms:assetid: 2647fd12-92b5-4682-a4f7-b262bcef8a0a
ms:mtpsurl: https://msdn.microsoft.com/library/Ff629696(v=BTS.80)
ms:contentKeyID: 51526904
ms.date: 08/30/2017
mtps_version: v=BTS.80
f1_keywords:
- bts10.adapters.wcf-custom.handler.receive.extensions
---

# \<Host Name\> Properties Dialog Box, WCF Extensions Tab (WCF-Custom or WCF-CustomIsolated Adapter Receive Handler)

 

Use the **WCF Extensions** tab to configure the receive handler for the WCF-Custom or WCF-CustomIsolated adapter.


> [!NOTE]
> <P>For all Send and Receive WCF-Custom and WCF-CustomIsolated handlers, the name of the binding extension element should always map to the same Binding Type. This is regardless of the host the handler is tied to.</P>



<table>
<thead>
<tr class="header">
<th>Use this</th>
<th>To do this</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>Import</strong></td>
<td>Imports a WCF configuration file with WCF custom behavior extensions. Clicking this button opens the <strong>Import WCF configuration</strong> dialog box to browse and locate a WCF configuration file. Note that the file should be a valid WCF configuration file. For more information about WCF configuration schema, see “Windows Communication Foundation Configuration Schema” at <a href="https://go.microsoft.com/fwlink/?linkid=163953">https://go.microsoft.com/fwlink/?LinkId=163953</a>.</td>
</tr>
<tr class="even">
<td><strong>Export</strong></td>
<td>Exports the WCF custom behavior extension to a WCF configuration file. Clicking this button opens the <strong>Export WCF configuration</strong> dialog box to browse and save the WCF configuration file.</td>
</tr>
<tr class="odd">
<td><strong>Clear</strong></td>
<td>Clears the existing WCF custom behavior extension from the adapter handler properties.</td>
</tr>
</tbody>
</table>


## See Also

[How to Configure a WCF-Custom Receive Handler](https://msdn.microsoft.com/library/ff629675\(v=bts.80\))  
[How to Configure a WCF-CustomIsolated Receive Handler](https://msdn.microsoft.com/library/ff629709\(v=bts.80\))
