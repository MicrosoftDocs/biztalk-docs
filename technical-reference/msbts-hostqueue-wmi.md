---
description: "Learn more about: MSBTS_HostQueue (WMI)"
title: MSBTS_HostQueue (WMI)
TOCTitle: MSBTS_HostQueue (WMI)
ms:assetid: 25a01b53-4759-4914-a742-df065b90c3e6
ms:mtpsurl: https://msdn.microsoft.com/library/Aa559246(v=BTS.80)
ms:contentKeyID: 51526840
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# MSBTS\_HostQueue (WMI)

 

Represents an application.

## Syntax

```C#
  
class MSBTS_HostQueue : MSBTS_BTSObject  
```

## Members

**MSBTS\_HostQueue** defines the following properties:

<table>
<thead>
<tr class="header">
<th>Property</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Caption (Inherited from <strong>CIM_ManagedSystemElement</strong>)</td>
<td>For more information about the <strong>CIM_ManagedSystemElement</strong> class, see the Windows Management Instrumentation documentation at <a href="/windows/win32/cimwin32prov/cim-managedsystemelement">https://go.microsoft.com/fwlink/?LinkID=20245</a>.</td>
</tr>
<tr class="even">
<td>Description (Inherited from <strong>CIM_ManagedSystemElement</strong>)</td>
<td>For more information about the <strong>CIM_ManagedSystemElement</strong> class, see the Windows Management Instrumentation documentation at <a href="/windows/win32/cimwin32prov/cim-managedsystemelement">https://go.microsoft.com/fwlink/?LinkID=20245</a>.</td>
</tr>
<tr class="odd">
<td><a href="msbts-hostqueue-hostname-property-wmi.md">HostName</a></td>
<td>Contains the name of the host that corresponds to the queue.</td>
</tr>
<tr class="even">
<td>InstallDate (Inherited from <strong>CIM_ManagedSystemElement</strong>)</td>
<td>For more information about the <strong>CIM_ManagedSystemElement</strong> class, see the Windows Management Instrumentation documentation at <a href="/windows/win32/cimwin32prov/cim-managedsystemelement">https://go.microsoft.com/fwlink/?LinkID=20245</a>.</td>
</tr>
<tr class="odd">
<td><a href="msbts-hostqueue-mgmtdbnameoverride-property-wmi.md">MgmtDbNameOverride</a></td>
<td>Overrides the initial catalog part of the BizTalk Management database connect string, and represents the database name. This property was not implemented for BizTalk Server and is reserved for future use.</td>
</tr>
<tr class="even">
<td><a href="msbts-hostqueue-mgmtdbserveroverride-property-wmi.md">MgmtDbServerOverride</a></td>
<td>Overrides the data source part of the BizTalk Management database connect string. This property was not implemented for BizTalk Server and is reserved for future use.</td>
</tr>
<tr class="odd">
<td>Name (Inherited from <strong>CIM_ManagedSystemElement</strong>)</td>
<td>For more information about the <strong>CIM_ManagedSystemElement</strong> class, see the Windows Management Instrumentation documentation at <a href="/windows/win32/cimwin32prov/cim-managedsystemelement">https://go.microsoft.com/fwlink/?LinkID=20245</a>.</td>
</tr>
<tr class="even">
<td>Status (Inherited from <strong>CIM_ManagedSystemElement</strong>)</td>
<td>For more information about the <strong>CIM_ManagedSystemElement</strong> class, see the Windows Management Instrumentation documentation at <a href="/windows/win32/cimwin32prov/cim-managedsystemelement">https://go.microsoft.com/fwlink/?LinkID=20245</a>.</td>
</tr>
</tbody>
</table>


**MSBTS\_HostQueue** defines the following methods:

<table>
<thead>
<tr class="header">
<th>Property</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><a href="msbts-hostqueue-resumeserviceinstancesbyid-method-wmi.md">ResumeServiceInstancesByID</a></td>
<td>Resubmits service instances by ID.</td>
</tr>
<tr class="even">
<td><a href="msbts-hostqueue-suspendserviceinstancesbyid-method-wmi.md">SuspendServiceInstancesByID</a></td>
<td>Moves service instances to the suspended queue by ID.</td>
</tr>
<tr class="odd">
<td><a href="msbts-hostqueue-terminateserviceinstancesbyid-method-wmi.md">TerminateServiceInstancesByID</a></td>
<td>Terminates service instances by ID.</td>
</tr>
</tbody>
</table>


## Requirements

**Header:** Declared in BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.