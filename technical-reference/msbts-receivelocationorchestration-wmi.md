---
description: "Learn more about: MSBTS_ReceiveLocationOrchestration (WMI)"
title: MSBTS_ReceiveLocationOrchestration (WMI)
TOCTitle: MSBTS_ReceiveLocationOrchestration (WMI)
ms:assetid: 0835f43a-25ce-431d-b4ba-a1f7105d9047
ms:mtpsurl: https://msdn.microsoft.com/library/Aa547083(v=BTS.80)
ms:contentKeyID: 51526057
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# MSBTS\_ReceiveLocationOrchestration (WMI)

 

Represents all possible combinations of receive locations and orchestrations.

## Declaration

```C#
class MSBTS_ReceiveLocationOrchestration : MSBTS_Setting  
```

## Members

**MSBTS\_ReceiveLocationOrchestration** defines the following properties:

<table>
<thead>
<tr class="header">
<th>Property</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><a href="msbts-receivelocationorchestration-adaptername-property-wmi.md">AdapterName</a></td>
<td>Contains the name of the adapter used by the given instance of the receive location.</td>
</tr>
<tr class="even">
<td>Caption (Inherited from <strong>CIM_Setting</strong>)</td>
<td>For more information about the <strong>CIM_Setting</strong> class, see the Windows Management Instrumentation documentation at <a href="/windows/win32/cimwin32prov/cim-setting">https://go.microsoft.com/fwlink/?LinkID=20246</a>.</td>
</tr>
<tr class="odd">
<td>Description (Inherited from <strong>CIM_Setting</strong>)</td>
<td>For more information about the <strong>CIM_Setting</strong> class, see the Windows Management Instrumentation documentation at <a href="/windows/win32/cimwin32prov/cim-setting">https://go.microsoft.com/fwlink/?LinkID=20246</a>.</td>
</tr>
<tr class="even">
<td><a href="msbts-receivelocationorchestration-inboundtransporturl-property-wmi.md">InboundTransportUrl</a></td>
<td>Contains the URL provided by the transport component, based on the specific adapter configuration.</td>
</tr>
<tr class="odd">
<td><a href="msbts-receivelocationorchestration-isdisabled-property-wmi.md">IsDisabled</a></td>
<td>Enables or disables a receive location.</td>
</tr>
<tr class="even">
<td><a href="msbts-receivelocationorchestration-isprimary-property-wmi.md">IsPrimary</a></td>
<td>Specifies a primary receive location to use for correlation.</td>
</tr>
<tr class="odd">
<td><a href="msbts-receivelocationorchestration-mgmtdbnameoverride-property-wmi.md">MgmtDbNameOverride</a></td>
<td>Overrides the initial catalog part of the BizTalk Management database connect string, and represents the database name. This property was not implemented for BizTalk Server and is reserved for future use.</td>
</tr>
<tr class="even">
<td><a href="msbts-receivelocationorchestration-mgmtdbserveroverride-property-wmi.md">MgmtDbServerOverride</a></td>
<td>Overrides the data source part of the BizTalk Management database connect string. This property was not implemented for BizTalk Server and is reserved for future use.</td>
</tr>
<tr class="odd">
<td><a href="msbts-receivelocationorchestration-orchestrationassemblyculture-property-wmi.md">OrchestrationAssemblyCulture</a></td>
<td>Contains the culture of the Microsoft® .NET-based assembly with which this orchestration belongs.</td>
</tr>
<tr class="even">
<td><a href="msbts-receivelocationorchestration-orchestrationassemblyname-property-wmi.md">OrchestrationAssemblyName</a></td>
<td>Contains the name of the Microsoft® .NET-based assembly to which this orchestration belongs.</td>
</tr>
<tr class="odd">
<td><a href="msbts-receivelocationorchestration-orchestrationassemblypublickeytoken-property-wmi.md">OrchestrationAssemblyPublicKeyToken</a></td>
<td>Contains the public key token of the Microsoft® .NET-based assembly with which this orchestration belongs.</td>
</tr>
<tr class="even">
<td><a href="msbts-receivelocationorchestration-orchestrationassemblyversion-property-wmi.md">OrchestrationAssemblyVersion</a></td>
<td>Contains the version of the Microsoft® .NET-based assembly with which this orchestration belongs.</td>
</tr>
<tr class="odd">
<td><a href="msbts-receivelocationorchestration-orchestrationhostname-property-wmi.md">OrchestrationHostName</a></td>
<td>Contains the name of the BizTalk host with which this orchestration is enlisted.</td>
</tr>
<tr class="even">
<td><a href="msbts-receivelocationorchestration-orchestrationname-property-wmi.md">OrchestrationName</a></td>
<td>Contains the host name with which this orchestration is enlisted.</td>
</tr>
<tr class="odd">
<td><a href="msbts-receivelocationorchestration-orchestrationstatus-property-wmi.md">OrchestrationStatus</a></td>
<td>Indicates the status of the orchestration.</td>
</tr>
<tr class="even">
<td><a href="msbts-receivelocationorchestration-pipelinename-property-wmi.md">PipelineName</a></td>
<td>Represents the name of the pipeline that will process the document before it is submitted to the MessageBox.</td>
</tr>
<tr class="odd">
<td><a href="msbts-receivelocationorchestration-receivehostname-property-wmi.md">ReceiveHostName</a></td>
<td>Contains the name of the BizTalk Host for the receive handler hosting the given instance of the receive location.</td>
</tr>
<tr class="even">
<td><a href="msbts-receivelocationorchestration-receivelocationname-property-wmi.md">ReceiveLocationName</a></td>
<td>Contains the name of the receive location.</td>
</tr>
<tr class="odd">
<td><a href="msbts-receivelocationorchestration-receiveportname-property-wmi.md">ReceivePortName</a></td>
<td>Contains the name of receive port used by the given instance of the receive location.</td>
</tr>
<tr class="even">
<td>SettingID (Inherited from <strong>CIM_Setting</strong>)</td>
<td>For more information about the <strong>CIM_Setting</strong> class, see the Windows Management Instrumentation documentation at <a href="/windows/win32/cimwin32prov/cim-setting">https://go.microsoft.com/fwlink/?LinkID=20246</a>.</td>
</tr>
</tbody>
</table>


## Requirements

**Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.