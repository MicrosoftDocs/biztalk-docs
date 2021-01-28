---
description: "Learn more about: MSBTS_AdapterSetting (WMI)"
title: MSBTS_AdapterSetting (WMI)
TOCTitle: MSBTS_AdapterSetting (WMI)
ms:assetid: 4b775cb4-b8a8-40a4-9aa8-2363620d306d
ms:mtpsurl: https://msdn.microsoft.com/library/Aa560016(v=BTS.80)
ms:contentKeyID: 51527862
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# MSBTS\_AdapterSetting (WMI)

 

Registers new adapters with Microsoft® BizTalk® Server.

## Declaration

```C#
class MSBTS_AdapterSetting : MSBTS_Setting  
```

## Members

**MSBTS\_AdapterSetting** defines the following properties:

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
<td>For more information about the <strong>CIM_Setting</strong> class, see the Windows Management Instrumentation documentation at <a href="https://go.microsoft.com/fwlink/?linkid=20246">https://go.microsoft.com/fwlink/?LinkID=20246</a>.</td>
</tr>
<tr class="even">
<td><a href="msbts-adaptersetting-comment-property-wmi.md">Comment</a></td>
<td>Gets or sets user comments.</td>
</tr>
<tr class="odd">
<td><a href="msbts-adaptersetting-constraints-property-wmi.md">Constraints</a></td>
<td>Gets a bitmap with the constraints of the adapter.</td>
</tr>
<tr class="even">
<td><a href="msbts-adaptersetting-defaultinboundcfg-property-wmi.md">DefaultInboundCfg</a></td>
<td>Gets a default inbound configuration for the adapter.</td>
</tr>
<tr class="odd">
<td><a href="msbts-adaptersetting-defaultoutboundcfg-property-wmi.md">DefaultOutboundCfg</a></td>
<td>Gets a default outbound configuration for the adapter.</td>
</tr>
<tr class="even">
<td>Description (Inherited from <strong>CIM_Setting</strong>)</td>
<td>For more information about the <strong>CIM_Setting</strong> class, see the Windows Management Instrumentation documentation at <a href="https://go.microsoft.com/fwlink/?linkid=20246">https://go.microsoft.com/fwlink/?LinkID=20246</a>.</td>
</tr>
<tr class="odd">
<td><a href="msbts-adaptersetting-mgmtclsid-property-wmi.md">MgmtCLSID</a></td>
<td>Gets the class ID (CLSID) of the COM component responsible for managing this adapter.</td>
</tr>
<tr class="even">
<td><a href="msbts-adaptersetting-mgmtdbnameoverride-property-wmi.md">MgmtDbNameOverride</a></td>
<td>Overrides the initial catalog part of the BizTalk Management database connect string, and represents the database name. This property was not implemented for BizTalk Server and is reserved for future use.</td>
</tr>
<tr class="odd">
<td><a href="msbts-adaptersetting-mgmtdbserveroverride-property-wmi.md">MgmtDbServerOverride</a></td>
<td>Overrides the data source part of the BizTalk Management database connect string. This property was not implemented for BizTalk Server and is reserved for future use.</td>
</tr>
<tr class="even">
<td><a href="msbts-adaptersetting-name-property-wmi.md">Name</a></td>
<td>Gets the name of the adapter.</td>
</tr>
<tr class="odd">
<td>SettingID (Inherited from <strong>CIM_Setting</strong>)</td>
<td>For more information about the <strong>CIM_Setting</strong> class, see the Windows Management Instrumentation documentation at <a href="https://go.microsoft.com/fwlink/?linkid=20246">https://go.microsoft.com/fwlink/?LinkID=20246</a>.</td>
</tr>
</tbody>
</table>


## Remarks

Creating or deleting instances of this class registers and un-registers adapters from BizTalk Server. Enumerating instances of this class returns all the registered BizTalk adapters. Microsoft BizTalk Server includes several native adapters such as FILE, FTP, HTTP, BizTalk Message Queuing, SMTP, SOAP, and SQL. You can develop custom adapters and register them using this class. For more information about native adapters, see [Using Adapters](https://msdn.microsoft.com/library/aa578103\(v=bts.80\)). For more information about creating custom adapters, see [Developing Adapters Using the Adapter Framework](https://msdn.microsoft.com/library/aa559841\(v=bts.80\)).

For more information about the minimum security user rights required to administer an adapter, see [Minimum Security User Rights](https://msdn.microsoft.com/library/aa559845\(v=bts.80\)).

## Requirements

**Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.
