---
description: "Learn more about: MSBTS_Orchestration (WMI)"
title: MSBTS_Orchestration (WMI)
TOCTitle: MSBTS_Orchestration (WMI)
ms:assetid: 7811deb6-775f-4b9d-9587-d61c5b65a5ce
ms:mtpsurl: https://msdn.microsoft.com/library/Aa560904(v=BTS.80)
ms:contentKeyID: 51529057
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# MSBTS\_Orchestration (WMI)

 

Represents an instance of an orchestration that belongs to the installed module.

## Declaration

```C#
class MSBTS_Orchestration : MSBTS_Service  
```

## Members

**MSBTS\_Orchestration** defines the following properties:

<table>
<thead>
<tr class="header">
<th>Property</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><a href="msbts-orchestration-assemblyculture-property-wmi.md">AssemblyCulture</a></td>
<td>Contains the culture of the .NET assembly to which this orchestration belongs.</td>
</tr>
<tr class="even">
<td><a href="msbts-orchestration-assemblyname-property-wmi.md">AssemblyName</a></td>
<td>Contains the name of the Microsoft .NET-based assembly to which the orchestration belongs.</td>
</tr>
<tr class="odd">
<td><a href="msbts-orchestration-assemblypublickeytoken-property-wmi.md">AssemblyPublicKeyToken</a></td>
<td>Contains the public key token of the .NET assembly to which this orchestration belongs.</td>
</tr>
<tr class="even">
<td><a href="msbts-orchestration-assemblyversion-property-wmi.md">AssemblyVersion</a></td>
<td>Contains the version of the .NET assembly to which this orchestration belongs.</td>
</tr>
<tr class="odd">
<td>Caption (Inherited from <strong>CIM_ManagedSystemElement</strong>)</td>
<td>For more information about the <strong>CIM_ManagedSystemElement</strong> class, see the Windows Management Instrumentation documentation at <a href="https://go.microsoft.com/fwlink/?linkid=20245">https://go.microsoft.com/fwlink/?LinkID=20245</a>.</td>
</tr>
<tr class="even">
<td>Description (Inherited from <strong>CIM_ManagedSystemElement</strong>)</td>
<td>For more information about the <strong>CIM_ManagedSystemElement</strong> class, see the Windows Management Instrumentation documentation at <a href="https://go.microsoft.com/fwlink/?linkid=20245">https://go.microsoft.com/fwlink/?LinkID=20245</a>.</td>
</tr>
<tr class="odd">
<td><a href="msbts-orchestration-hostname-property-wmi.md">HostName</a></td>
<td>Contains the name of the BizTalk Host with which this orchestration is enlisted.</td>
</tr>
<tr class="even">
<td><a href="msbts-orchestration-mgmtdbnameoverride-property-wmi.md">MgmtDbNameOverride</a></td>
<td>Overrides the initial catalog part of the BizTalk Management database connect string, and represents the database name. This property was not implemented for BizTalk Server and is reserved for future use.</td>
</tr>
<tr class="odd">
<td>InstallDate (Inherited from <strong>CIM_ManagedSystemElement</strong>)</td>
<td>For more information about the <strong>CIM_ManagedSystemElement</strong> class, see the Windows Management Instrumentation documentation at <a href="https://go.microsoft.com/fwlink/?linkid=20245">https://go.microsoft.com/fwlink/?LinkID=20245</a>.</td>
</tr>
<tr class="even">
<td><a href="msbts-orchestration-mgmtdbserveroverride-property-wmi.md">MgmtDbServerOverride</a></td>
<td>Overrides the data source part of the BizTalk Management database connect string. This property was not implemented for BizTalk Server and is reserved for future use.</td>
</tr>
<tr class="odd">
<td><a href="msbts-orchestration-name-property-wmi.md">Name</a></td>
<td>Contains the name of the orchestration.</td>
</tr>
<tr class="even">
<td><a href="msbts-orchestration-orchestrationstatus-property-wmi.md">OrchestrationStatus</a></td>
<td>Indicates the status of the orchestration.</td>
</tr>
<tr class="odd">
<td>Status (Inherited from <strong>CIM_ManagedSystemElement</strong>)</td>
<td>For more information about the <strong>CIM_ManagedSystemElement</strong> class, see the Windows Management Instrumentation documentation at <a href="https://go.microsoft.com/fwlink/?linkid=20245">https://go.microsoft.com/fwlink/?LinkID=20245</a>.</td>
</tr>
</tbody>
</table>


**MSBTS\_Orchestration** defines the following methods:

<table>
<thead>
<tr class="header">
<th>Method</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><a href="msbts-orchestration-enlist-method-wmi.md">Enlist</a></td>
<td>Enlists the orchestration by creating its activation subscription.</td>
</tr>
<tr class="even">
<td><a href="msbts-orchestration-querydependencyinfo-method-wmi.md">QueryDependencyInfo</a></td>
<td>Retrieves information about services that this service depends on through either a <strong>CALL</strong> or <strong>START</strong> relationship.</td>
</tr>
<tr class="odd">
<td><a href="msbts-orchestration-queryinstanceinfo-method-wmi.md">QueryInstanceInfo</a></td>
<td>Retrieves information about instances of the orchestration in various states.</td>
</tr>
<tr class="even">
<td><a href="msbts-orchestration-start-method-wmi.md">Start</a></td>
<td>Starts the orchestration by enabling its activation subscription.</td>
</tr>
<tr class="odd">
<td><a href="msbts-orchestration-stop-method-wmi.md">Stop</a></td>
<td>Stops the orchestration by disabling its activation subscription.</td>
</tr>
<tr class="even">
<td><a href="msbts-orchestration-unenlist-method-wmi.md">Unenlist</a></td>
<td>Terminates all instances of the orchestration and removes its activation subscription.</td>
</tr>
</tbody>
</table>


## Requirements

**Header:** Declared in BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.
