---
description: "Learn more about: MSBTS_DeploymentService (WMI)"
title: MSBTS_DeploymentService (WMI)
TOCTitle: MSBTS_DeploymentService (WMI)
ms:assetid: b2ff0753-edef-494c-980a-b5071faf23b2
ms:mtpsurl: https://msdn.microsoft.com/library/Aa578176(v=BTS.80)
ms:contentKeyID: 51530589
ms.date: 08/30/2017
mtps_version: v=BTS.80
ms.topic: reference
---

# MSBTS\_DeploymentService (WMI)

 

Encapsulates BizTalk assemblies for deployment or undeployment and bindings export or import.

## Declaration

```C#
class MSBTS_DeploymentService : MSBTS_Setting  
```

## Members

**MSBTS\_DeploymentService** defines the following properties:

<table>
<thead>
<tr class="header">
<th>Property</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Caption (Inherited from <strong>CIM_Setting</strong>)</td>
<td>For more information about the <strong>CIM_Setting</strong> class, see the Windows Management Instrumentation documentation at <a href="/windows/win32/cimwin32prov/cim-setting">https://go.microsoft.com/fwlink/?LinkID=20246</a>.</td>
</tr>
<tr class="even">
<td>Description (Inherited from <strong>CIM_Setting</strong>)</td>
<td>For more information about the <strong>CIM_Setting</strong> class, see the Windows Management Instrumentation documentation at <a href="/windows/win32/cimwin32prov/cim-setting">https://go.microsoft.com/fwlink/?LinkID=20246</a>.</td>
</tr>
<tr class="odd">
<td><a href="msbts-deploymentservice-mgmtdbnameoverride-property-wmi.md">MgmtDbNameOverride</a></td>
<td>Overrides the initial catalog part of the BizTalk Management database connect string, and represents the database name. This property was not implemented for BizTalk Server and is reserved for future use.</td>
</tr>
<tr class="even">
<td><a href="msbts-deploymentservice-mgmtdbserveroverride-property-wmi.md">MgmtDbServerOverride</a></td>
<td>Overrides the data source part of the BizTalk Management database connect string. This property was not implemented for BizTalk Server and is reserved for future use.</td>
</tr>
<tr class="odd">
<td>SettingID (Inherited from <strong>CIM_Setting</strong>)</td>
<td>For more information about the <strong>CIM_Setting</strong> class, see the Windows Management Instrumentation documentation at <a href="/windows/win32/cimwin32prov/cim-setting">https://go.microsoft.com/fwlink/?LinkID=20246</a>.</td>
</tr>
</tbody>
</table>


**MSBTS\_DeploymentService** defines the following methods:

<table>
<thead>
<tr class="header">
<th>Method</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><a href="msbts-deploymentservice-deploy-method-wmi.md">Deploy</a></td>
<td>Deploys the assembly into the target database.</td>
</tr>
<tr class="even">
<td><a href="msbts-deploymentservice-export-method-wmi.md">Export</a></td>
<td>Exports the binding file from the target database.</td>
</tr>
<tr class="odd">
<td><a href="msbts-deploymentservice-import-method-wmi.md">Import</a></td>
<td>Imports the binding file into the target database.</td>
</tr>
<tr class="even">
<td><a href="msbts-deploymentservice-remove-method-wmi.md">Remove</a></td>
<td>Removes the assembly from the target database.</td>
</tr>
</tbody>
</table>


## Requirements

**Header:** Declared in BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.
