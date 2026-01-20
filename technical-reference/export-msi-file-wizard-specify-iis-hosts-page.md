---
description: "Learn more about: Export MSI File Wizard, Specify IIS Hosts Page"
title: Export MSI File Wizard, Specify IIS Hosts Page
TOCTitle: Export MSI File Wizard, Specify IIS Hosts Page
ms:assetid: f5cdfde4-23a8-43b5-928a-df2cf433d1c9
ms:mtpsurl: https://msdn.microsoft.com/library/Aa561956(v=BTS.80)
ms:contentKeyID: 51533463
ms.date: 08/30/2017
mtps_version: v=BTS.80
f1_keywords:
- bts10.appdeploy.app.export.hosts
ms.topic: ui-reference
---

# Export MSI File Wizard, Specify IIS Hosts Page

 

Use the **Specify IIS Hosts** page to specify the Web server from which to export virtual directory resources. If you selected a virtual directory to export on the previous page of the wizard, and the wizard cannot locate the virtual directory in order to include it in the .msi file, you may need to provide the host name and port number used by the Web server on this page. Otherwise, click Next to continue the wizard.

<table>
<thead>
<tr class="header">
<th>Use this</th>
<th>To do this</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>Protocol</strong></td>
<td>Indicates the protocol used for the virtual directory. You do not need to provide information in this box.</td>
</tr>
<tr class="even">
<td><strong>Host</strong></td>
<td>If the instructions on the page indicate that this is necessary, type the host name and port (if other than 80) used by the Web server for the virtual directory. Example: MyWebServer:81</td>
</tr>
<tr class="odd">
<td><strong>Path</strong></td>
<td>Indicates the path of the virtual directory. You do not need to provide information in this box.</td>
</tr>
</tbody>
</table>


## See Also

[How to Export a BizTalk Application](https://msdn.microsoft.com/library/aa577804\(v=bts.80\))  
[What Happens When Artifacts Are Exported](https://msdn.microsoft.com/library/aa578034\(v=bts.80\))  
[The Application Deployment Process](https://msdn.microsoft.com/library/aa559316\(v=bts.80\))

