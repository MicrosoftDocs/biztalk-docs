---
title: MSBTS_Host (WMI)
TOCTitle: MSBTS_Host (WMI)
ms:assetid: dd0a6c58-236b-4673-8960-c654aef6a894
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa561438(v=BTS.80)
ms:contentKeyID: 51532787
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# MSBTS\_Host (WMI)

 

Represents a Microsoft BizTalk Server Host.

## Declaration

``` 
class MSBTS_Host : MSBTS_Service  
```

## Members

**MSBTS\_Host** defines the following properties:

<table>
<thead>
<tr class="header">
<th>Property</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><a href="msbts-host-authtrusted-property-wmi.md">AuthTrusted</a></td>
<td>Indicates whether a tracking service can be trusted to collect authentication information.</td>
</tr>
<tr class="even">
<td>Caption (Inherited from <strong>CIM_ManagedSystemElement</strong>)</td>
<td>For more information about the <strong>CIM_ManagedSystemElement</strong> class, see the Windows Management Instrumentation documentation at <a href="http://go.microsoft.com/fwlink/?linkid=20245">http://go.microsoft.com/fwlink/?LinkID=20245</a>.</td>
</tr>
<tr class="odd">
<td><a href="msbts-host-decryptcertcomment-property-wmi.md">DecryptCertComment</a></td>
<td>Represents a comment field that allows you to associate a friendly name with a decryption certificate.</td>
</tr>
<tr class="even">
<td><a href="msbts-host-decryptcertthumbprint-property-wmi.md">DecryptCertThumbprint</a></td>
<td>Contains the thumbprint of the public key certificate used to decrypt inbound messages for this host.</td>
</tr>
<tr class="odd">
<td>Description (Inherited from <strong>CIM_ManagedSystemElement</strong>)</td>
<td>For more information about the <strong>CIM_ManagedSystemElement</strong> class, see the Windows Management Instrumentation documentation at <a href="http://go.microsoft.com/fwlink/?linkid=20245">http://go.microsoft.com/fwlink/?LinkID=20245</a>.</td>
</tr>
<tr class="even">
<td><a href="msbts-host-hosttracking-property-wmi.md">HostTracking</a></td>
<td>Indicates whether instances of this BizTalk Host will host the tracking sub service.</td>
</tr>
<tr class="odd">
<td><a href="msbts-host-hosttype-property-wmi.md">HostType</a></td>
<td>Indicates which runtime model the instances of the BizTalk Host will be running in.</td>
</tr>
<tr class="even">
<td>InstallDate (Inherited from <strong>CIM_ManagedSystemElement</strong>)</td>
<td>For more information about the <strong>CIM_ManagedSystemElement</strong> class, see the Windows Management Instrumentation documentation at <a href="http://go.microsoft.com/fwlink/?linkid=20245">http://go.microsoft.com/fwlink/?LinkID=20245</a>.</td>
</tr>
<tr class="odd">
<td><a href="msbts-host-isdefault-property-wmi.md">IsDefault</a></td>
<td>Indicates whether the BizTalk Host represented by this WMI instance is the default BizTalk Host in the BizTalk group.</td>
</tr>
<tr class="even">
<td><a href="msbts-host-lastusedlogon-property-wmi.md">LastUsedLogon</a></td>
<td>Contains the default logon for the BizTalk Host instance creation user interface.</td>
</tr>
<tr class="odd">
<td><a href="msbts-host-mgmtdbnameoverride-property-wmi.md">MgmtDbNameOverride</a></td>
<td>Overrides the initial catalog part of the BizTalk Management database connect string, and represents the database name. This property was not implemented for BizTalk Server and is reserved for future use.</td>
</tr>
<tr class="even">
<td><a href="msbts-host-mgmtdbserveroverride-property-wmi.md">MgmtDbServerOverride</a></td>
<td>Overrides the data source part of the BizTalk Management database connect string. This property was not implemented for BizTalk Server and is reserved for future use.</td>
</tr>
<tr class="odd">
<td><a href="msbts-host-name-property-wmi.md">Name</a></td>
<td>Contains the name of the host.</td>
</tr>
<tr class="even">
<td><a href="msbts-host-ntgroupname-property-wmi.md">NTGroupName</a></td>
<td>Contains the name of the Microsoft Windows NT group.</td>
</tr>
<tr class="odd">
<td>Status (Inherited from <strong>CIM_ManagedSystemElement</strong>)</td>
<td>For more information about the <strong>CIM_ManagedSystemElement</strong> class, see the Windows Management Instrumentation documentation at <a href="http://go.microsoft.com/fwlink/?linkid=20245">http://go.microsoft.com/fwlink/?LinkID=20245</a>.</td>
</tr>
</tbody>
</table>


**MSBTS\_Host** defines the following methods:

<table>
<thead>
<tr class="header">
<th>Method</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><a href="msbts-host-start-method-wmi.md">Start</a></td>
<td>Starts all BizTalk Host instances in the BizTalk group for the given BizTalk Host.</td>
</tr>
<tr class="even">
<td><a href="msbts-host-stop-method-wmi.md">Stop</a></td>
<td>Stops all BizTalk Host instances in the BizTalk group for the given BizTalk Host.</td>
</tr>
<tr class="odd">
<td><a href="msbts-host-cluster-method-wmi.md">MSBTS_Host.Cluster Method (WMI)</a></td>
<td>Clusters all BizTalk Host Instances of the given BizTalk Host.</td>
</tr>
<tr class="even">
<td><a href="msbts-host-getclusterresourcegroupnames-wmi.md">MSBTS_Host.GetClusterResourceGroupNames (WMI)</a></td>
<td>Returns List of cluster resource groups available.</td>
</tr>
<tr class="odd">
<td><a href="msbts-host-uncluster-method-wmi.md">MSBTS_Host.UnCluster Method (WMI)</a></td>
<td>Un-Clusters all BizTalk Host Instances of the given BizTalk Host.</td>
</tr>
</tbody>
</table>


## Remarks

For more information about the minimum security user rights required to administer a Host, see [Minimum Security User Rights](https://msdn.microsoft.com/en-us/library/aa559845\(v=bts.80\)).

## Requirements

**Header:** Declared in BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.

