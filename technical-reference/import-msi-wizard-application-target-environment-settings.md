---
description: "Learn more about: Import MSI Wizard: Application Target Environment Settings"
title: 'Import MSI Wizard: Application Target Environment Settings'
TOCTitle: 'Import MSI Wizard: Application Target Environment Settings'
ms:assetid: b0f80f12-e530-4c53-86e6-fec8417fbdd2
ms:mtpsurl: https://msdn.microsoft.com/library/Aa578134(v=BTS.80)
ms:contentKeyID: 51530545
ms.date: 08/30/2017
mtps_version: v=BTS.80
f1_keywords:
- bts10.appdeploy.app.import.environment
ms.topic: reference
---

# Import MSI Wizard: Application Target Environment Settings


Use the **Application Target Environment Settings** page to specify which bindings to apply to this application on import. If you added one or more binding files to the application before it was exported into the .msi file, and specified a target environment for each binding file you added, the target environments that you specified will appear in the list. Otherwise, only \<Default\> will display. This option applies all of the application bindings that were exported into the .msi file and that do not have a target environment specified.

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
<td><strong>Target Staging Environment</strong></td>
<td>In the drop-down list, select the bindings to apply to this application. Select &lt;Default&gt; if you want to apply all bindings in the application except for those that have a target environment specified. If the .msi file does not contain a binding file that you want to apply explicitly, you can leave &lt;Default&gt; selected.</td>
</tr>
</tbody>
</table>


## See Also

[How to Import a BizTalk Application](https://msdn.microsoft.com/library/aa560132\(v=bts.80\))  
[How to Add a Binding File to an Application](https://msdn.microsoft.com/library/aa558708\(v=bts.80\))  
[Binding Files and Application Deployment](https://msdn.microsoft.com/library/aa559631\(v=bts.80\))  
[The Application Deployment Process](https://msdn.microsoft.com/library/aa559316\(v=bts.80\))  
[What Happens When Artifacts Are Imported](https://msdn.microsoft.com/library/aa577939\(v=bts.80\))

