---
description: "Learn more about: MSBTS_HostSetting (WMI)"
title: MSBTS_HostSetting (WMI)
TOCTitle: MSBTS_HostSetting (WMI)
ms:assetid: 59e7065d-178d-4d74-8a3e-77cb0068e89f
ms:mtpsurl: https://msdn.microsoft.com/library/Aa560307(v=BTS.80)
ms:contentKeyID: 51528236
ms.date: 08/30/2017
mtps_version: v=BTS.80
ms.topic: concept-article
---

# MSBTS\_HostSetting (WMI)

 

Creates a Microsoft BizTalk Server host setting.

## Declaration

```C#
class MSBTS_HostSetting : MSBTS_Setting  
```

## Members

**MSBTS\_AppTypeSetting** defines the following properties/methods:

<table>
<thead>
<tr class="header">
<th>Property</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><a href="msbts-hostsetting-authtrusted-property-wmi.md">AuthTrusted</a></td>
<td>Indicates whether a BizTalk host can be trusted to collect authentication information.</td>
</tr>
<tr class="even">
<td>Caption (Inherited from <strong>CIM_Setting</strong>)</td>
<td>For more information about the <strong>CIM_Setting</strong> class, see the Windows Management Instrumentation documentation at <a href="/windows/win32/cimwin32prov/cim-setting">https://go.microsoft.com/fwlink/?LinkId=83193</a>.</td>
</tr>
<tr class="odd">
<td><a href="msbts-hostsetting-clusterresourcegroupname-property-wmi.md">MSBTS_HostSetting.ClusterResourceGroupName Property (WMI)</a></td>
<td>When the host instances of this host are clustered, this property contains the cluster resource group name set by the Administrator.</td>
</tr>
<tr class="even">
<td><a href="msbts-hostsetting-dbqueuesizethreshold-property-wmi.md">MSBTS_HostSetting.DBQueueSizeThreshold Property (WMI)</a></td>
<td>Maximum number of items in the Database.</td>
</tr>
<tr class="odd">
<td><a href="msbts-hostsetting-dbsessionthreshold-property-wmi.md">MSBTS_HostSetting.DBSessionThreshold Property (WMI)</a></td>
<td>Maximum number of DB Sessions (per CPU) allowed before throttling begins.</td>
</tr>
<tr class="even">
<td><a href="msbts-hostsetting-decryptcertcomment-property-wmi.md">DecryptCertComment</a></td>
<td>Represents a comment field that allows you to associate a friendly name with a decryption certificate.</td>
</tr>
<tr class="odd">
<td><a href="msbts-hostsetting-decryptcertthumbprint-property-wmi.md">DecryptCertThumbprint</a></td>
<td>Contains the thumbprint of the decryption certificate.</td>
</tr>
<tr class="even">
<td><a href="msbts-hostsetting-deliveryqueuesize-property-wmi.md">MSBTS_HostSetting.DeliveryQueueSize Property (WMI)</a></td>
<td>Size of the in-memory Queue that the host maintains as a temporary placeholder for delivering messages.</td>
</tr>
<tr class="odd">
<td>Description (Inherited from <strong>CIM_Setting</strong>)</td>
<td>For more information about the <strong>CIM_Setting</strong> class, see the Windows Management Instrumentation documentation at <a href="/windows/win32/cimwin32prov/cim-setting">https://go.microsoft.com/fwlink/?LinkId=83193</a>.</td>
</tr>
<tr class="even">
<td><a href="msbts-hostsetting-globalmemorythreshold-property-wmi.md">MSBTS_HostSetting.GlobalMemoryThreshold Property (WMI)</a></td>
<td>Maximum System-wide Virtual Memory (in percent) usage allowed before throttling begins.</td>
</tr>
<tr class="odd">
<td><a href="msbts-hostsetting-hosttracking-property-wmi.md">HostTracking</a></td>
<td>Indicates whether instances of this BizTalk Host will host the tracking sub service.</td>
</tr>
<tr class="even">
<td><a href="msbts-hostsetting-hosttype-property-wmi.md">HostType</a></td>
<td>Indicates which runtime model the instances of the BizTalk Host will be running in.</td>
</tr>
<tr class="odd">
<td><a href="msbts-hostsetting-inflightmessagethreshold-property-wmi.md">MSBTS_HostSetting.InflightMessageThreshold Property (WMI)</a></td>
<td>Maximum number of in-memory in-flight messages allowed before throttling Message Delivery begins.</td>
</tr>
<tr class="even">
<td><a href="msbts-hostsetting-isdefault-property-wmi.md">IsDefault</a></td>
<td>Indicates whether the BizTalk Host represented by this WMI instance is the default BizTalk Host in the BizTalk group.</td>
</tr>
<tr class="odd">
<td><a href="msbts-hostsetting-ishost32bitonly-property-wmi.md">MSBTS_HostSetting.IsHost32BitOnly Property (WMI)</a></td>
<td>This property indicates whether the host instance process should be created as 32-bit on both 32-bit and 64-bit servers.</td>
</tr>
<tr class="even">
<td><a href="msbts-hostsetting-lastusedlogon-property-wmi.md">LastUsedLogon</a></td>
<td>Contains a default logon for the BizTalk Host instance creation user interface.</td>
</tr>
<tr class="odd">
<td><a href="msbts-hostsetting-messagedeliverysamplespacesize-property-wmi.md">MSBTS_HostSetting.MessageDeliverySampleSpaceSize Property (WMI)</a></td>
<td>This property indicates the number of samples that are used for determining the rate of the Message Delivery to all Service Classes of the Host</td>
</tr>
<tr class="even">
<td><a href="msbts-hostsetting-messagedeliverysamplespacewindow-wmi.md">MSBTS_HostSetting.MessageDeliverySampleSpaceWindow (WMI)</a></td>
<td>Time-window (in milliseconds) beyond which samples will be deemed invalid for consideration.</td>
</tr>
<tr class="odd">
<td><a href="msbts-hostsetting-messagedeliveryoverdrivefactor-property-wmi.md">MSBTS_HostSetting.MessageDeliveryOverdriveFactor Property (WMI)</a></td>
<td>Percent factor by which the system will overdrive the Input rate for Message Delivery Throttling.</td>
</tr>
<tr class="even">
<td><a href="msbts-hostsetting-messagedeliverymaximumdelay-property-wmi.md">MSBTS_HostSetting.MessageDeliveryMaximumDelay Property (WMI)</a></td>
<td>Maximum Delay (in milliseconds) imposed for Message Delivery Throttling. Zero indicates disable Message Delivery Throttling.</td>
</tr>
<tr class="odd">
<td><a href="msbts-hostsetting-messagepublishsamplespacesize-property-wmi.md">MSBTS_HostSetting.MessagePublishSampleSpaceSize Property (WMI)</a></td>
<td>Number of samples that are used for determining the rate of the Message Publishing by the Service Classes.</td>
</tr>
<tr class="even">
<td><a href="msbts-hostsetting-messagepublishsamplespacewindow-property-wmi.md">MSBTS_HostSetting.MessagePublishSampleSpaceWindow Property (WMI)</a></td>
<td>Time-window (in milliseconds) beyond which samples will be deemed invalid for consideration.</td>
</tr>
<tr class="odd">
<td><a href="msbts-hostsetting-messagepublishoverdrivefactor-property-wmi.md">MSBTS_HostSetting.MessagePublishOverdriveFactor Property (WMI)</a></td>
<td>Percent Factor by which the system will overdrive the Input rate.</td>
</tr>
<tr class="even">
<td><a href="msbts-hostsetting-messagepublishmaximumdelay-property-wmi.md">MSBTS_HostSetting.MessagePublishMaximumDelay Property (WMI)</a></td>
<td>Maximum Delay (in milliseconds) imposed for Message Publishing Throttling. Zero indicates disable Message Publishing Throttling.</td>
</tr>
<tr class="odd">
<td><a href="msbts-hostsetting-mgmtdbnameoverride-property-wmi.md">MgmtDbNameOverride</a></td>
<td>Overrides the initial catalog part of the BizTalk Management database connect string, and represents the database name. This property was not implemented for BizTalk Server and is reserved for future use.</td>
</tr>
<tr class="even">
<td><a href="msbts-hostsetting-mgmtdbserveroverride-property-wmi.md">MgmtDbServerOverride</a></td>
<td>Overrides the data source part of the BizTalk Management database connect string. This property was not implemented for BizTalk Server and is reserved for future use.</td>
</tr>
<tr class="odd">
<td><a href="msbts-hostsetting-name-property-wmi.md">Name</a></td>
<td>Contains the name of the BizTalk host.</td>
</tr>
<tr class="even">
<td><a href="msbts-hostsetting-ntgroupname-property-wmi.md">NTGroupName</a></td>
<td>Contains the name of the Windows NT group.</td>
</tr>
<tr class="odd">
<td>SettingID (Inherited from <strong>CIM_Setting</strong>)</td>
<td>For more information about the <strong>CIM_Setting</strong> class, see the Windows Management Instrumentation documentation at <a href="/windows/win32/cimwin32prov/cim-setting">https://go.microsoft.com/fwlink/?LinkId=83193</a>.</td>
</tr>
<tr class="even">
<td><a href="msbts-hostsetting-threadpoolsize-property-wmi.md">MSBTS_HostSetting.ThreadPoolSize Property (WMI)</a></td>
<td>Maximum number of messaging engine threads per CPU.</td>
</tr>
<tr class="odd">
<td><a href="msbts-hostsetting-threadthreshold-property-wmi.md">MSBTS_HostSetting.ThreadThreshold Property (WMI)</a></td>
<td>Maximum number of threads in the process (per CPU) allowed before throttling begins.</td>
</tr>
<tr class="even">
<td><a href="msbts-hostsetting-processmemorythreshold-property-wmi.md">MSBTS_HostSetting.ProcessMemoryThreshold Property (WMI)</a></td>
<td>Maximum Process Memory (in percent) allowed before throttling begins.</td>
</tr>
</tbody>
</table>


## Remarks

For sample code using the MSBTS\_HostSetting class, see [Creating, Updating, and Deleting a Host Instance Using WMI](creating-updating-and-deleting-a-host-instance-using-wmi.md).

## Requirements

**Header:** Declared in BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.
