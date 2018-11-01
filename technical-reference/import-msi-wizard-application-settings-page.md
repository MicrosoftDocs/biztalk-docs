---
title: Import MSI Wizard, Application Settings Page
TOCTitle: Import MSI Wizard, Application Settings Page
ms:assetid: 4555894a-95d7-4d65-97a6-953c95f441dc
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa559858(v=BTS.80)
ms:contentKeyID: 51527712
ms.date: 08/30/2017
mtps_version: v=BTS.80
f1_keywords:
- bts10.appdeploy.app.import.settings
---

# Import MSI Wizard, Application Settings Page

 

Use the **Application Settings** page to view or select the application into which the .msi file will be imported, view the references required by the application, and select the applications, if any, to which you want to add a reference.

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
<td><strong>Application name</strong></td>
<td>If you started the Import Wizard by right-clicking an application, clicking <strong>Import</strong> and then clicking <strong>MSI file</strong>, this box displays the name of the application into which this .msi file will be imported. You cannot select a different application.<br />
<br />
If you started the Import Wizard by right-clicking <strong>Applications</strong>, clicking <strong>Import</strong>, and then clicking <strong>MSI file</strong>, you can select the application into which to import this .msi file. From the drop-down list, select the application. The list includes the application that you are importing along with all of the applications that exist in the BizTalk group. If the application you are importing does not already exist in the group, and you select it, the application will be created and the artifacts in the .msi file added to it. Otherwise, the artifacts will be added to an existing application that you select.</td>
</tr>
<tr class="even">
<td><strong>Application References and Resources</strong></td>
<td>Lists the required references for the application being installed and the resources (artifacts) in this .msi file.</td>
</tr>
<tr class="odd">
<td><strong>Available applications to add references to</strong></td>
<td>Select the check boxes of applications that are referenced by the application you are importing, as listed in the <strong>Application References and Resources</strong> box. If the application you are importing has a dependency on an artifact in another application, you must add a reference, or the application will not function correctly. If the application on which this application depends does not exist in the group, you must either import it into the group or add the required artifact to the application.</td>
</tr>
<tr class="even">
<td><strong>Overwrite resources</strong></td>
<td>Select this check box to overwrite existing resources. If you are importing bindings in this .msi file they will automatically overwrite any bindings having the same name in an existing application, even if this option is not selected.</td>
</tr>
</tbody>
</table>


## See Also

[How to Import a BizTalk Application](https://msdn.microsoft.com/en-us/library/aa560132\(v=bts.80\))  
[The Application Deployment Process](https://msdn.microsoft.com/en-us/library/aa559316\(v=bts.80\))  
[What Happens When Artifacts Are Imported](https://msdn.microsoft.com/en-us/library/aa577939\(v=bts.80\))

