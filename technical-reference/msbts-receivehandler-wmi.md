---
title: MSBTS_ReceiveHandler (WMI)
TOCTitle: MSBTS_ReceiveHandler (WMI)
ms:assetid: 1c04de0e-b85d-4e1a-ad18-bd625f05e025
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa559071(v=BTS.80)
ms:contentKeyID: 51526580
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# MSBTS\_ReceiveHandler (WMI)

 

Represents an individual receive handler defined by Microsoft BizTalk Server.

## Declaration

```C#
class MSBTS_ReceiveHandler : MSBTS_Setting  
```

## Members

**MSBTS\_ReceiveHandler** defines the following properties:

<table>
<thead>
<tr class="header">
<th>Property</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><a href="msbts-receivehandler-adaptername-property-wmi.md">AdapterName</a></td>
<td>Contains the name of the adapter.</td>
</tr>
<tr class="even">
<td>Caption (Inherited from <strong>CIM_Setting</strong>)</td>
<td>For more information about the <strong>CIM_Setting</strong> class, see the Windows Management Instrumentation documentation at <a href="http://go.microsoft.com/fwlink/?linkid=20246">http://go.microsoft.com/fwlink/?LinkID=20246</a>.</td>
</tr>
<tr class="odd">
<td><a href="msbts-receivehandler-customcfg-property-wmi.md">CustomCfg</a></td>
<td>Contains the adapter-specific configuration in XML format.</td>
</tr>
<tr class="even">
<td>Description (Inherited from <strong>CIM_Setting</strong>)</td>
<td>For more information about the <strong>CIM_Setting</strong> class, see the Windows Management Instrumentation documentation at <a href="http://go.microsoft.com/fwlink/?linkid=20246">http://go.microsoft.com/fwlink/?LinkID=20246</a>.</td>
</tr>
<tr class="odd">
<td><a href="msbts-receivehandler-hostname-property-wmi.md">HostName</a></td>
<td>Contains the name of the BizTalk Host for this adapter.</td>
</tr>
<tr class="even">
<td><a href="msbts-receivehandler-hostnametoswitchto-property-wmi.md">HostNameToSwitchTo</a></td>
<td>Contains the name of the BizTalk Host that this adapter handler should switch to.</td>
</tr>
<tr class="odd">
<td><a href="msbts-receivehandler-mgmtdbnameoverride-property-wmi.md">MgmtDbNameOverride</a></td>
<td>Overrides the initial catalog part of the BizTalk Management database connect string, and represents the database name. This property was not implemented for BizTalk Server and is reserved for future use.</td>
</tr>
<tr class="even">
<td><a href="msbts-receivehandler-mgmtdbserveroverride-property-wmi.md">MgmtDbServerOverride</a></td>
<td>Overrides the data source part of the BizTalk Management database connect string. This property was not implemented for BizTalk Server and is reserved for future use.</td>
</tr>
<tr class="odd">
<td>SettingID (Inherited from <strong>CIM_Setting</strong>)</td>
<td>For more information about the <strong>CIM_Setting</strong> class, see the Windows Management Instrumentation documentation at <a href="http://go.microsoft.com/fwlink/?linkid=20246">http://go.microsoft.com/fwlink/?LinkID=20246</a>.</td>
</tr>
</tbody>
</table>


## Remarks

For more information about the minimum security user rights required to administer a receive handler, see [Minimum Security User Rights](https://msdn.microsoft.com/library/aa559845\(v=bts.80\)).

For samples illustrating the **MSBTS\_ReceiveHandler** class, see [WMI Script Samples](wmi-script-samples.md).

## Requirements

**Header:** Declared in BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

