---
title: MSBTS_Server (WMI)
TOCTitle: MSBTS_Server (WMI)
ms:assetid: 849d3788-2edd-4fad-a230-afbe320353c1
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa561154(v=BTS.80)
ms:contentKeyID: 51529384
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# MSBTS\_Server (WMI)

 

Represents computers within a group that have Microsoft® BizTalk® Servers installed.

## Syntax

``` 
  
class MSBTS_Server : MSBTS_Service  
```

## Members

**MSBTS\_Server** defines the following properties:

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
<td>For more information about the <strong>CIM_ManagedSystemElement</strong> class, see the Windows Management Instrumentation documentation at <a href="http://go.microsoft.com/fwlink/?linkid=20245">http://go.microsoft.com/fwlink/?LinkID=20245</a>.</td>
</tr>
<tr class="even">
<td>Description (Inherited from <strong>CIM_ManagedSystemElement</strong>)</td>
<td>For more information about the <strong>CIM_ManagedSystemElement</strong> class, see the Windows Management Instrumentation documentation at <a href="http://go.microsoft.com/fwlink/?linkid=20245">http://go.microsoft.com/fwlink/?LinkID=20245</a>.</td>
</tr>
<tr class="odd">
<td>InstallDate (Inherited from <strong>CIM_ManagedSystemElement</strong>)</td>
<td>For more information about the <strong>CIM_ManagedSystemElement</strong> class, see the Windows Management Instrumentation documentation at <a href="http://go.microsoft.com/fwlink/?linkid=20245">http://go.microsoft.com/fwlink/?LinkID=20245</a>.</td>
</tr>
<tr class="even">
<td><a href="msbts-server-mgmtdbnameoverride-property-wmi.md">MgmtDbNameOverride</a></td>
<td>Overrides the initial catalog part of the BizTalk Management database connection string. This property was not implemented for BizTalk Server and is reserved for future use. <strong>Note:</strong> The BizTalk Management database is also referred to as the BizTalk Configuration database.</td>
</tr>
<tr class="odd">
<td><a href="msbts-server-mgmtdbserveroverride-property-wmi.md">MgmtDbServerOverride</a></td>
<td>Overrides the data source part of the BizTalk Management database connection string. This property was not implemented for BizTalk Server and is reserved for future use.</td>
</tr>
<tr class="even">
<td><a href="msbts-server-name-property-wmi.md">Name</a></td>
<td>Contains the name of the server.</td>
</tr>
<tr class="odd">
<td>Status (Inherited from <strong>CIM_ManagedSystemElement</strong>)</td>
<td>For more information about the <strong>CIM_ManagedSystemElement</strong> class, see the Windows Management Instrumentation documentation at <a href="http://go.microsoft.com/fwlink/?linkid=20245">http://go.microsoft.com/fwlink/?LinkID=20245</a>.</td>
</tr>
</tbody>
</table>


**MSBTS\_Server** defines the following methods:

<table>
<thead>
<tr class="header">
<th>Method</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><a href="msbts-server-checkifcaninstallhostinstances-method-wmi.md">MSBTS_Server.CheckIfCanInstallHostInstances Method (WMI)</a></td>
<td>Checks if the server can host BizTalk host instances.</td>
</tr>
<tr class="even">
<td><a href="msbts-server-start-method-wmi.md">Start</a></td>
<td>Starts all BizTalk Server services on a specific server.</td>
</tr>
<tr class="odd">
<td><a href="msbts-server-stop-method-wmi.md">Stop</a></td>
<td>Stops all BizTalk Server services on a specific server.</td>
</tr>
</tbody>
</table>


## Remarks

This class provides several server-wide operations. **MSBTS\_Server** is created with an **MSBTS\_ServerSetting** class instance.

For more information about the minimum security user rights required to administer a server, see [Minimum Security User Rights](https://msdn.microsoft.com/library/aa559845\(v=bts.80\)).

## Requirements

**Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

## See Also

[MSBTS\_Server.CheckIfCanInstallHostInstances Method (WMI)](msbts-server-checkifcaninstallhostinstances-method-wmi.md)  
[MSBTS\_Server.MgmtDbNameOverride Property (WMI)](msbts-server-mgmtdbnameoverride-property-wmi.md)  
[MSBTS\_Server.MgmtDbServerOverride Property (WMI)](msbts-server-mgmtdbserveroverride-property-wmi.md)  
[MSBTS\_Server.Name Property (WMI)](msbts-server-name-property-wmi.md)  
[MSBTS\_Server.Start Method (WMI)](msbts-server-start-method-wmi.md)  
[MSBTS\_Server.Stop Method (WMI)](msbts-server-stop-method-wmi.md)

