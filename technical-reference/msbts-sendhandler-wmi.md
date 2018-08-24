---
title: MSBTS_SendHandler (WMI)
TOCTitle: MSBTS_SendHandler (WMI)
ms:assetid: e7bdf055-500c-47ea-8392-0798e2e9a9e0
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa561662(v=BTS.80)
ms:contentKeyID: 51533060
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# MSBTS\_SendHandler (WMI)

 

Represents an individual send handler defined by the BizTalk Server.


> [!NOTE]
> <P>This class cannot be used to create multiple send handlers; to create multiple send handlers, use <A href="msbts-sendhandler2-wmi.md">MSBTS_SendHandler2 (WMI)</A>.</P>



## Declaration

``` 
class MSBTS_SendHandler : MSBTS_Setting  
```

## Members

**MSBTS\_SendHandler** defines the following properties:

<table>
<thead>
<tr class="header">
<th>Property</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><a href="msbts-sendhandler-adaptername-property-wmi.md">AdapterName</a></td>
<td>Contains the name of the adapter used.</td>
</tr>
<tr class="even">
<td>Caption (Inherited from <strong>CIM_Setting</strong>)</td>
<td>For more information about the <strong>CIM_Setting</strong> class, see the Windows Management Instrumentation documentation at <a href="http://go.microsoft.com/fwlink/?linkid=20246">http://go.microsoft.com/fwlink/?LinkID=20246</a>.</td>
</tr>
<tr class="odd">
<td><a href="msbts-sendhandler-customcfg-property-wmi.md">CustomCfg</a></td>
<td>Contains the protocol-specific configuration in XML format.</td>
</tr>
<tr class="even">
<td>Description (Inherited from <strong>CIM_Setting</strong>)</td>
<td>For more information about the <strong>CIM_Setting</strong> class, see the Windows Management Instrumentation documentation at <a href="http://go.microsoft.com/fwlink/?linkid=20246">http://go.microsoft.com/fwlink/?LinkID=20246</a>.</td>
</tr>
<tr class="odd">
<td><a href="msbts-sendhandler-hostname-property-wmi.md">HostName</a></td>
<td>Contains the name of the host this send handler.</td>
</tr>
<tr class="even">
<td><a href="msbts-sendhandler-mgmtdbnameoverride-property-wmi.md">MgmtDbNameOverride</a></td>
<td>Overrides the initial catalog part of the BizTalk Management database connect string, and represents the database name. This property was not implemented for BizTalk Server and is reserved for future use.</td>
</tr>
<tr class="odd">
<td><a href="msbts-sendhandler-mgmtdbserveroverride-property-wmi.md">MgmtDbServerOverride</a></td>
<td>Overrides the data source part of the BizTalk Management database connect string. This property was not implemented for BizTalk Server and is reserved for future use.</td>
</tr>
<tr class="even">
<td>SettingID (Inherited from <strong>CIM_Setting</strong>)</td>
<td>For more information about the <strong>CIM_Setting</strong> class, see the Windows Management Instrumentation documentation at <a href="http://go.microsoft.com/fwlink/?linkid=20246">http://go.microsoft.com/fwlink/?LinkID=20246</a>.</td>
</tr>
</tbody>
</table>


## Requirements

**Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

