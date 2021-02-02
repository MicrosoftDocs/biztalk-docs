---
description: "Learn more about: MSBTS_HostInstance (WMI)"
title: MSBTS_HostInstance (WMI)
TOCTitle: MSBTS_HostInstance (WMI)
ms:assetid: 6bb4aa2b-84b4-4213-b711-eb2fb82e5748
ms:mtpsurl: https://msdn.microsoft.com/library/Aa560660(v=BTS.80)
ms:contentKeyID: 51528716
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# MSBTS\_HostInstance (WMI)

 

Represents a single instance of a BizTalk Host.

## Declaration

```C#
class MSBTS_HostInstance : MSBTS_Service  
```

## Members

**MSBTS\_HostInstance** defines the following properties:

<table>
<thead>
<tr class="header">
<th>Property</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><a href="msbts-hostinstance-clusterinstancetype-property-wmi.md">MSBTS_HostInstance.ClusterInstanceType Property (WMI)</a></td>
<td>This property tells whether the BizTalk Host Instance NT service is clustered.</td>
</tr>
<tr class="even">
<td>Caption (Inherited from <strong>CIM_ManagedSystemElement</strong>)</td>
<td>For more information about the <strong>CIM_ManagedSystemElement</strong> class, see the Windows Management Instrumentation documentation at <a href="https://go.microsoft.com/fwlink/?linkid=20245">https://go.microsoft.com/fwlink/?LinkID=20245</a>.</td>
</tr>
<tr class="odd">
<td><a href="msbts-hostinstance-configurationstate-property-wmi.md">ConfigurationState</a></td>
<td>Contains the installation state for given instance of the BizTalk host.</td>
</tr>
<tr class="even">
<td>Description (Inherited from <strong>CIM_ManagedSystemElement</strong>)</td>
<td>For more information about the <strong>CIM_ManagedSystemElement</strong> class, see the Windows Management Instrumentation documentation at <a href="https://go.microsoft.com/fwlink/?linkid=20245">https://go.microsoft.com/fwlink/?LinkID=20245</a>.</td>
</tr>
<tr class="odd">
<td><a href="msbts-hostinstance-hostname-property-wmi.md">HostName</a></td>
<td>Contains the name of the BizTalk host to which this BizTalk host instance belongs.</td>
</tr>
<tr class="even">
<td><a href="msbts-hostinstance-hosttype-property-wmi.md">HostType</a></td>
<td>Indicates which runtime model the instances of the BizTalk host will be running in.</td>
</tr>
<tr class="odd">
<td>InstallDate (Inherited from <strong>CIM_ManagedSystemElement</strong>)</td>
<td>For more information about the <strong>CIM_ManagedSystemElement</strong> class, see the Windows Management Instrumentation documentation at <a href="https://go.microsoft.com/fwlink/?linkid=20245">https://go.microsoft.com/fwlink/?LinkID=20245</a>.</td>
</tr>
<tr class="even">
<td><a href="msbts-hostinstance-isdisabled-property-wmi.md">IsDisabled</a></td>
<td>Enables or disables a host instance.</td>
</tr>
<tr class="odd">
<td><a href="msbts-hostinstance-logon-property-wmi.md">Logon</a></td>
<td>Contains the logon information that this BizTalk host instance is using.</td>
</tr>
<tr class="even">
<td><a href="msbts-hostinstance-mgmtdbnameoverride-property-wmi.md">MgmtDbNameOverride</a></td>
<td>Overrides the initial catalog part of the BizTalk Management database connect string, and represents the database name. This property was not implemented for BizTalk Server and is reserved for future use.</td>
</tr>
<tr class="odd">
<td><a href="msbts-hostinstance-mgmtdbserveroverride-property-wmi.md">MgmtDbServerOverride</a></td>
<td>Overrides the data source part of the BizTalk Management database connect string. This property was not implemented for BizTalk Server and is reserved for future use.</td>
</tr>
<tr class="even">
<td><a href="msbts-hostinstance-name-property-wmi.md">Name</a></td>
<td>Contains the name of the host instance.</td>
</tr>
<tr class="odd">
<td><a href="msbts-hostinstance-ntgroupname-property-wmi.md">NTGroupName</a></td>
<td>Contains the name of the Microsoft Windows NT group.</td>
</tr>
<tr class="even">
<td><a href="msbts-hostinstance-runningserver-property-wmi.md">RunningServer</a></td>
<td>Contains the name of the server on which the host instance runs.</td>
</tr>
<tr class="odd">
<td><a href="msbts-hostinstance-servicestate-property-wmi.md">ServiceState</a></td>
<td>Contains the state of the host instance.</td>
</tr>
<tr class="even">
<td>Status (Inherited from <strong>CIM_ManagedSystemElement</strong>)</td>
<td>For more information about the <strong>CIM_ManagedSystemElement</strong> class, see the Windows Management Instrumentation documentation at <a href="https://go.microsoft.com/fwlink/?linkid=20245">https://go.microsoft.com/fwlink/?LinkID=20245</a>.</td>
</tr>
<tr class="odd">
<td><a href="msbts-hostinstance-uniqueid-property-wmi.md">UniqueID</a></td>
<td>Contains the unique ID of the host instance.</td>
</tr>
</tbody>
</table>


**MSBTS\_HostInstance** defines the following methods:

<table>
<thead>
<tr class="header">
<th>Method</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><a href="msbts-hostinstance-getstate-method-wmi.md">GetState</a></td>
<td>Retrieves the state of the given instance of the BizTalk host.</td>
</tr>
<tr class="even">
<td><a href="msbts-hostinstance-install-method.md">Install</a></td>
<td>Installs a service for the given instance of the BizTalk host.</td>
</tr>
<tr class="odd">
<td><a href="msbts-hostinstance-start-method-wmi.md">Start</a></td>
<td>Starts the given instance of the BizTalk host.</td>
</tr>
<tr class="even">
<td><a href="msbts-hostinstance-stop-method-wmi.md">Stop</a></td>
<td>Stops the given instance of the BizTalk host.</td>
</tr>
<tr class="odd">
<td><a href="msbts-hostinstance-uninstall-method-wmi.md">Uninstall</a></td>
<td>Uninstalls a service for the given instance of the BizTalk host.</td>
</tr>
</tbody>
</table>


## Remarks

For more information about the minimum security user rights required to administer a Host instance, see [Minimum Security User Rights](https://msdn.microsoft.com/library/aa559845\(v=bts.80\)).


> [!NOTE]
> <P>Always specify the name of the local server when using WMI. When you enumerate host instances, both local and remote instances will be returned. You can then call start, stop and other methods.</P>



For samples illustrating the **MSBTS\_HostInstance** class, see [WMI Script Samples](wmi-script-samples.md).

## Requirements

**Header:** Declared in BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.
