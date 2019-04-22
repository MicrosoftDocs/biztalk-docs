---
title: MSBTS_HostInstanceSetting (WMI)
TOCTitle: MSBTS_HostInstanceSetting (WMI)
ms:assetid: a3adb52f-f106-4221-8794-01ed32c50605
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa577852(v=BTS.80)
ms:contentKeyID: 51530236
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# MSBTS\_HostInstanceSetting (WMI)

 

Updates the **IsDisabled** property when a host is in the stopped state.

## Declaration

```C#
class MSBTS_HostInstanceSetting : MSBTS_Setting  
```

## Members

**MSBTS\_HostInstanceSetting** defines the following properties:

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
<td>For more information about the <strong>CIM_Setting</strong> class, see the Windows Management Instrumentation documentation at <a href="http://go.microsoft.com/fwlink/?linkid=20246">http://go.microsoft.com/fwlink/?LinkID=20246</a>.</td>
</tr>
<tr class="even">
<td><a href="msbts-hostinstancesetting-configurationstate-property-wmi.md">ConfigurationState</a></td>
<td>Contains the installation state for given instance of the BizTalk host.</td>
</tr>
<tr class="odd">
<td>Description (Inherited from <strong>CIM_Setting</strong>)</td>
<td>For more information about the <strong>CIM_Setting</strong> class, see the Windows Management Instrumentation documentation at <a href="http://go.microsoft.com/fwlink/?linkid=20246">http://go.microsoft.com/fwlink/?LinkID=20246</a>.</td>
</tr>
<tr class="even">
<td><a href="msbts-hostinstancesetting-hostname-property-wmi.md">HostName</a></td>
<td>Contains the name of the BizTalk host to which this BizTalk host instance belongs.</td>
</tr>
<tr class="odd">
<td><a href="msbts-hostinstancesetting-hosttype-property-wmi.md">HostType</a></td>
<td>Indicates which runtime model the instances of the BizTalk host will be running in.</td>
</tr>
<tr class="even">
<td><a href="msbts-hostinstancesetting-isdisabled-property-wmi.md">IsDisabled</a></td>
<td>Enables or disables a host instance.</td>
</tr>
<tr class="odd">
<td><a href="msbts-hostinstancesetting-logon-property-wmi.md">Logon</a></td>
<td>Contains the logon information that this BizTalk host instance is using.</td>
</tr>
<tr class="even">
<td><a href="msbts-hostinstancesetting-mgmtdbnameoverride-property-wmi.md">MgmtDbNameOverride</a></td>
<td>Overrides the initial catalog part of the BizTalk Management database connect string, and represents the database name. This property was not implemented for BizTalk Server and is reserved for future use.</td>
</tr>
<tr class="odd">
<td><a href="msbts-hostinstancesetting-mgmtdbserveroverride-property-wmi.md">MgmtDbServerOverride</a></td>
<td>Overrides the data source part of the BizTalk Management database connect string. This property was not implemented for BizTalk Server and is reserved for future use.</td>
</tr>
<tr class="even">
<td><a href="msbts-hostinstancesetting-name-property-wmi.md">Name</a></td>
<td>Contains the name of the host instance.</td>
</tr>
<tr class="odd">
<td><a href="msbts-hostinstancesetting-ntgroupname-property-wmi.md">NTGroupName</a></td>
<td>Contains the name of the Microsoft® Windows NT® group.</td>
</tr>
<tr class="even">
<td><a href="msbts-hostinstancesetting-runningserver-property-wmi.md">RunningServer</a></td>
<td>Contains the name of the server on which the host instance runs.</td>
</tr>
<tr class="odd">
<td>SettingID (Inherited from <strong>CIM_Setting</strong>)</td>
<td>For more information about the <strong>CIM_Setting</strong> class, see the Windows Management Instrumentation documentation at <a href="http://go.microsoft.com/fwlink/?linkid=20246">http://go.microsoft.com/fwlink/?LinkID=20246</a>.</td>
</tr>
</tbody>
</table>


## Remarks

This class should only be used to update the [IsDisabled](msbts-hostinstance-isdisabled-property-wmi.md) property for a host in the stopped state, which can also be done by [MSBTS\_HostInstance](msbts-hostinstance-wmi.md).

## Requirements

**Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

