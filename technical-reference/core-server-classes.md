---
description: "Learn more about: Core Server Classes"
title: Core Server Classes
TOCTitle: Core Server Classes
ms:assetid: 4e1f87e1-6c20-459b-89d9-b478c7353a8d
ms:mtpsurl: https://msdn.microsoft.com/library/Aa560069(v=BTS.80)
ms:contentKeyID: 51527928
ms.date: 08/30/2017
mtps_version: v=BTS.80
ms.topic: reference
---

# Core Server Classes

 

The Windows Management Instrumentation (WMI) classes in this table are used to manage the core objects associated with BizTalk Server, such as servers, queues, groups, and message handlers.

To view core server class and member information in CIM Studio, see [Viewing the WMI Core Server Classes in CIM Studio](viewing-the-wmi-core-server-classes-in-cim-studio.md). You can also view the MOF file and the member descriptions in a text editor, however the descriptions are easier to read in CIM Studio.

WMI Samples are available in the Examples section and in the SDK and in this section. For more information, see [WMI Script Samples](wmi-script-samples.md) and [Admin\\WMI (BizTalk Server Samples Folder)](https://msdn.microsoft.com/library/aa559638\(v=bts.80\)).


> [!WARNING]
> <P>If your BizTalk Configuration database is using a non-binary, case-sensitive collation then you must enter parameter values for object names and other key values in the correct case. For example, if a Send Port is configured with the name "SendPort" and you are using a non-binary, case-sensitive collation, you must enter "SendPort" as the name when working with WMI or calls will fail.</P>



<table>
<thead>
<tr class="header">
<th>Class</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><a href="msbts-adaptersetting-wmi.md">MSBTS_AdapterSetting</a></td>
<td>Registers new adapters with Microsoft® BizTalk® Server.</td>
</tr>
<tr class="even">
<td><a href="msbts-btsobject-wmi.md">MSBTS_BTSObject</a></td>
<td>This type or member supports the BizTalk Server infrastructure and is not intended to be used directly from your code.</td>
</tr>
<tr class="odd">
<td><a href="msbts-deploymentservice-wmi.md">MSBTS_DeploymentService</a></td>
<td>Encapsulates BizTalk assemblies for deployment or undeployment and bindings export or import.</td>
</tr>
<tr class="even">
<td><a href="msbts-groupsetting-wmi.md">MSBTS_GroupSetting</a></td>
<td>Represents a logical grouping of BizTalk Servers.</td>
</tr>
<tr class="odd">
<td><a href="msbts-host-wmi.md">MSBTS_Host</a></td>
<td>Represents a BizTalk Server Host.</td>
</tr>
<tr class="even">
<td><a href="msbts-hostinstance-wmi.md">MSBTS_HostInstance</a></td>
<td>Represents a single instance of a BizTalk Host.</td>
</tr>
<tr class="odd">
<td><a href="msbts-hostinstancesetting-wmi.md">MSBTS_HostInstanceSetting</a></td>
<td>Updates the <a href="msbts-hostinstancesetting-isdisabled-property-wmi.md">IsDisabled</a> property when a host is in the stopped state.</td>
</tr>
<tr class="even">
<td><a href="msbts-hostqueue-wmi.md">MSBTS_HostQueue</a></td>
<td>Represents an application.</td>
</tr>
<tr class="odd">
<td><a href="msbts-hostsetting-wmi.md">MSBTS_HostSetting</a></td>
<td>Creates a BizTalk Server Host setting.</td>
</tr>
<tr class="even">
<td><a href="msbts-messageinstance-wmi.md">MSBTS_MessageInstance</a></td>
<td>Represents a message instance.</td>
</tr>
<tr class="odd">
<td><a href="msbts-messageinstancesuspendedevent-wmi.md">MSBTS_MessageInstanceSuspendedEvent</a></td>
<td>Represents a suspended event for a BizTalk Message Queuing (MSMQT) message instance.</td>
</tr>
<tr class="even">
<td><a href="msbts-msgboxsetting-wmi.md">MSBTS_MsgBoxSetting</a></td>
<td>Represents a single MessageBox setting in the BizTalk Server group.</td>
</tr>
<tr class="odd">
<td><a href="msbts-orchestration-wmi.md">MSBTS_Orchestration</a></td>
<td>Represents an instance of an orchestration that belongs to the installed module.</td>
</tr>
<tr class="even">
<td><a href="msbts-receivehandler-wmi.md">MSBTS_ReceiveHandler</a></td>
<td>Represents an individual receive handler defined by BizTalk Server.</td>
</tr>
<tr class="odd">
<td><a href="msbts-receivelocation-wmi.md">MSBTS_ReceiveLocation</a></td>
<td>Represents an individual receive location defined by BizTalk Server.</td>
</tr>
<tr class="even">
<td><a href="msbts-receivelocationorchestration-wmi.md">MSBTS_ReceiveLocationOrchestration</a></td>
<td>Represents all possible combinations of receive locations and orchestrations.</td>
</tr>
<tr class="odd">
<td><a href="msbts-receiveport-wmi.md">MSBTS_ReceivePort</a></td>
<td>Represents an individual receive port defined by BizTalk Server.</td>
</tr>
<tr class="even">
<td><a href="msbts-sendhandler-wmi.md">MSBTS_SendHandler</a></td>
<td>Represents an individual send handler defined by BizTalk Server.</td>
</tr>
<tr class="odd">
<td><a href="msbts-sendhandler2-wmi.md">MSBTS_SendHandler2</a></td>
<td>Represents an extended individual send handler defined by BizTalk Server.</td>
</tr>
<tr class="even">
<td><a href="msbts-sendport-wmi.md">MSBTS_SendPort</a></td>
<td>Represents an individual send port defined by BizTalk Server.</td>
</tr>
<tr class="odd">
<td><a href="msbts-sendportgroup-wmi.md">MSBTS_SendPortGroup</a></td>
<td>Represents group of send ports defined by the BizTalk Server.</td>
</tr>
<tr class="even">
<td><a href="msbts-sendportgroup2sendport-wmi.md">MSBTS_SendPortGroup2SendPort (WMI)</a></td>
<td>Represents an extended group of send ports defined by the BizTalk Server.</td>
</tr>
<tr class="odd">
<td><a href="msbts-server-wmi.md">MSBTS_Server</a></td>
<td>Represents computers within a group that have BizTalk Servers installed.</td>
</tr>
<tr class="even">
<td><a href="msbts-serverhost-wmi.md">MSBTS_ServerHost</a></td>
<td>Reflects mappings between BizTalk servers and BizTalk Hosts.</td>
</tr>
<tr class="odd">
<td><a href="msbts-serversetting-wmi.md">MSBTS_ServerSetting</a></td>
<td>Represents specific computers within the BizTalk group that have BizTalk Servers installed. Instances of this class are intended to be created and deleted internally through BizTalk Server only. Do not create or delete instance of this class explicitly through WMI.</td>
</tr>
<tr class="even">
<td><a href="msbts-service-wmi.md">MSBTS_Service</a></td>
<td>This type or member supports the BizTalk Server infrastructure and is not intended to be used directly from your code.</td>
</tr>
<tr class="odd">
<td><a href="msbts-serviceinstance-wmi.md">MSBTS_ServiceInstance</a></td>
<td>Provides an instance of a service, with start and stop functionality.</td>
</tr>
<tr class="even">
<td><a href="msbts-serviceinstancesuspendedevent-wmi.md">MSBTS_ServiceInstanceSuspendedEvent</a></td>
<td>Represents a suspended event for a service instance.</td>
</tr>
<tr class="odd">
<td><a href="msbts-setting-wmi.md">MSBTS_Setting</a></td>
<td>This type or member supports the BizTalk Server infrastructure and is not intended to be used directly from your code.</td>
</tr>
<tr class="even">
<td><a href="msbts-trackedmessageinstance-wmi.md">MSBTS_TrackedMessageInstance</a></td>
<td>Represents a message instance.</td>
</tr>
<tr class="odd">
<td><a href="msbts-trackedmessageinstance2-wmi.md">MSBTS_TrackedMessageInstance2 (WMI)</a></td>
<td>Represents an updated message instance.</td>
</tr>
</tbody>
</table>


**Remarks**

For more information about the minimum security user rights required to administer items using WMI, see [Minimum Security User Rights](https://msdn.microsoft.com/library/aa559845\(v=bts.80\)).

