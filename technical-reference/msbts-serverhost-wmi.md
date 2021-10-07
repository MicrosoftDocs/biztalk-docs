---
description: "Learn more about: MSBTS_ServerHost (WMI)"
title: MSBTS_ServerHost (WMI)
TOCTitle: MSBTS_ServerHost (WMI)
ms:assetid: 81e42b3b-c75f-47ae-837a-a38ef2304f56
ms:mtpsurl: https://msdn.microsoft.com/library/Aa561095(v=BTS.80)
ms:contentKeyID: 51529308
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# MSBTS\_ServerHost (WMI)

 

Reflects the mapping between BizTalk servers and BizTalk Hosts.

## Syntax

```C#
  
class MSBTS_ServerHost : MSBTS_BTSObject  
```

## Members

**MSBTS\_ServerHost** defines the following properties:

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
<td><a href="msbts-serverhost-hostname-property-wmi.md">HostName</a></td>
<td>Contains the name of the host.</td>
</tr>
<tr class="even">
<td>InstallDate (Inherited from <strong>CIM_ManagedSystemElement</strong>)</td>
<td>For more information about the <strong>CIM_ManagedSystemElement</strong> class, see the Windows Management Instrumentation documentation at <a href="/windows/win32/cimwin32prov/cim-managedsystemelement">https://go.microsoft.com/fwlink/?LinkID=20245</a>.</td>
</tr>
<tr class="odd">
<td><a href="msbts-serverhost-ismapped-property-wmi.md">IsMapped</a></td>
<td>Indicates whether the specified server works with the specified MessageBox.</td>
</tr>
<tr class="even">
<td><a href="msbts-serverhost-mgmtdbnameoverride-property-wmi.md">MgmtDbNameOverride</a></td>
<td>Overrides the initial catalog part of the BizTalk Management database connect string, and represents the database name. This property was not implemented for BizTalk Server and is reserved for future use.</td>
</tr>
<tr class="odd">
<td><a href="msbts-serverhost-mgmtdbserveroverride-property-wmi.md">MgmtDbServerOverride</a></td>
<td>Overrides the data source part of the BizTalk Management database connect string. This property was not implemented for BizTalk Server and is reserved for future use.</td>
</tr>
<tr class="even">
<td>Name (Inherited from <strong>CIM_ManagedSystemElement</strong>)</td>
<td>For more information about the <strong>CIM_ManagedSystemElement</strong> class, see the Windows Management Instrumentation documentation at <a href="/windows/win32/cimwin32prov/cim-managedsystemelement">https://go.microsoft.com/fwlink/?LinkID=20245</a>.</td>
</tr>
<tr class="odd">
<td><a href="msbts-serverhost-servername-property-wmi.md">ServerName</a></td>
<td>Contains the name of the server.</td>
</tr>
<tr class="even">
<td>Status (Inherited from <strong>CIM_ManagedSystemElement</strong>)</td>
<td>For more information about the <strong>CIM_ManagedSystemElement</strong> class, see the Windows Management Instrumentation documentation at <a href="/windows/win32/cimwin32prov/cim-managedsystemelement">https://go.microsoft.com/fwlink/?LinkID=20245</a>.</td>
</tr>
</tbody>
</table>


**MSBTS\_ServerAppType** defines the following methods:

<table>
<thead>
<tr class="header">
<th>Method</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><a href="msbts-serverhost-forceunmap-method-wmi.md">ForceUnmap</a></td>
<td>Unmaps the server from the MessageBox even whether or if not all applications cannot be uninstalled.</td>
</tr>
<tr class="even">
<td><a href="msbts-serverhost-map-method-wmi.md">Map</a></td>
<td>Maps the server to the MessageBox without installing applications.</td>
</tr>
<tr class="odd">
<td><a href="msbts-serverhost-unmap-method-wmi.md">Unmap</a></td>
<td>Unmaps the server from the MessageBox.</td>
</tr>
</tbody>
</table>


## Remarks

There is one instance of this Windows Management Instrumentation (WMI )class per every server/host combination in the BizTalk group. Instances of this class are created and deleted automatically.

For samples illustrating the **MSBTS\_ServerHost** class, see [WMI Script Samples](wmi-script-samples.md).

## Requirements

**Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.