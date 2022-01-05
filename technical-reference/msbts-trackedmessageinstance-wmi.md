---
description: "Learn more about: MSBTS_TrackedMessageInstance (WMI)"
title: MSBTS_TrackedMessageInstance (WMI)
TOCTitle: MSBTS_TrackedMessageInstance (WMI)
ms:assetid: 03d251f7-4f09-4f7b-bd8a-388b6669258a
ms:mtpsurl: https://msdn.microsoft.com/library/Aa546797(v=BTS.80)
ms:contentKeyID: 51525930
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# MSBTS\_TrackedMessageInstance (WMI)

 

Represents tracked message instances stored in the MessageBox or Archived databases.

## Syntax

```C#
class MSBTS_TrackedMessageInstance : MSBTS_BTSObject  
```

## Members

**MSBTS\_TrackedMessageInstance** defines the following properties:

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
<td>InstallDate (Inherited from <strong>CIM_ManagedSystemElement</strong>)</td>
<td>For more information about the <strong>CIM_ManagedSystemElement</strong> class, see the Windows Management Instrumentation documentation at <a href="/windows/win32/cimwin32prov/cim-managedsystemelement">https://go.microsoft.com/fwlink/?LinkID=20245</a>.</td>
</tr>
<tr class="even">
<td><a href="msbts-trackedmessageinstance-messageinstanceid-property-wmi.md">MessageInstanceID</a></td>
<td>Contains the ID of the message instance.</td>
</tr>
<tr class="odd">
<td>Name (Inherited from <strong>CIM_ManagedSystemElement</strong>)</td>
<td>For more information about the <strong>CIM_ManagedSystemElement</strong> class, see the Windows Management Instrumentation documentation at <a href="/windows/win32/cimwin32prov/cim-managedsystemelement">https://go.microsoft.com/fwlink/?LinkID=20245</a>.</td>
</tr>
<tr class="even">
<td><a href="msbts-trackedmessageinstance-partcount-property-wmi.md">PartCount</a></td>
<td>Contains the number of message parts.</td>
</tr>
<tr class="odd">
<td>Status (Inherited from <strong>CIM_ManagedSystemElement</strong>)</td>
<td>For more information about the <strong>CIM_ManagedSystemElement</strong> class, see the Windows Management Instrumentation documentation at <a href="/windows/win32/cimwin32prov/cim-managedsystemelement">https://go.microsoft.com/fwlink/?LinkID=20245</a>.</td>
</tr>
<tr class="even">
<td><a href="msbts-trackedmessageinstance-sourcedbname-property-wmi.md">SourceDBName</a></td>
<td>Contains the name of the SQL database where the tracked message is stored, either the MessageBox or Archived database.</td>
</tr>
<tr class="odd">
<td><a href="msbts-trackedmessageinstance-sourcedbservername-property-wmi.md">SourceDBServerName</a></td>
<td>Contains the name of the SQL Server where the tracked message is stored, either the MessageBox or Archived database.</td>
</tr>
</tbody>
</table>


**MSBTS\_TrackedMessageInstance** defines the following method:

<table>
<thead>
<tr class="header">
<th>Property</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><a href="msbts-trackedmessageinstance-savetofile-method-wmi.md">SaveToFile</a></td>
<td>Saves the message context and parts into multiple output files.</td>
</tr>
</tbody>
</table>


## Remarks

This class only supports **GetObject**, and does not support **Create**, **Update**, **Delete**, or **Enum** operations.

For sample code illustrating the **MSBTS\_TrackedMessageInstance** class, see [Saving a Message to a File Using WMI](saving-a-message-to-a-file-using-wmi.md).

## Requirements

**Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.