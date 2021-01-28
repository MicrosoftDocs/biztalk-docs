---
description: "Learn more about: MSBTS_GroupSetting (WMI)"
title: MSBTS_GroupSetting (WMI)
TOCTitle: MSBTS_GroupSetting (WMI)
ms:assetid: bb440da1-b650-4345-80d5-949bcc774b5f
ms:mtpsurl: https://msdn.microsoft.com/library/Aa578341(v=BTS.80)
ms:contentKeyID: 51530817
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# MSBTS\_GroupSetting (WMI)

 

Represents a logical grouping of Microsoft® BizTalk® Servers.

## Declaration

class MSBTS\_GroupSetting : MSBTS\_Setting

## Members

**MSBTS\_GroupSetting** defines the following properties:

<table>
<thead>
<tr class="header">
<th>Property</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><a href="msbts-groupsetting-bamdbname-property-wmi.md">BamDBName</a></td>
<td>Gets or sets the name of the BAM SQL database.</td>
</tr>
<tr class="even">
<td><a href="msbts-groupsetting-bamdbservername-property-wmi.md">BamDBServerName</a></td>
<td>Gets or sets the name of the SQL server where BAM database is located.</td>
</tr>
<tr class="odd">
<td><a href="msbts-groupsetting-biztalkadministratorgroup-property-wmi.md">BizTalkAdministratorGroup</a></td>
<td>Gets the name of the BizTalk Administrator Microsoft® Windows NT® Group.</td>
</tr>
<tr class="even">
<td>Caption (Inherited from <strong>CIM_Setting</strong>)</td>
<td>For more information about the <strong>CIM_Setting</strong> class, see the Windows Management Instrumentation documentation at <a href="https://go.microsoft.com/fwlink/?linkid=83193">https://go.microsoft.com/fwlink/?LinkID=83193</a>.</td>
</tr>
<tr class="odd">
<td><a href="msbts-groupsetting-biztalkoperatorgroup-property-wmi.md">MSBTS_GroupSetting.BizTalkOperatorGroup Property (WMI)</a></td>
<td>This property is the name of the BizTalk Operators Windows Group.</td>
</tr>
<tr class="even">
<td><a href="msbts-groupsetting-configurationcacherefreshinterval-property-wmi.md">ConfigurationCacheRefreshInterval</a></td>
<td>Gets or sets how often BizTalk Server refreshes the cache of the messaging configuration objects, in seconds.</td>
</tr>
<tr class="odd">
<td>Description (Inherited from <strong>CIM_Setting</strong>)</td>
<td>For more information about the <strong>CIM_Setting</strong> class, see the Windows Management Instrumentation documentation at <a href="https://go.microsoft.com/fwlink/?linkid=83193">https://go.microsoft.com/fwlink/?LinkID=83193</a>.</td>
</tr>
<tr class="even">
<td><a href="msbts-groupsetting-globaltrackingoption-property-wmi.md">GlobalTrackingOption</a></td>
<td>Gets the level of tracking that the BizTalk server should perform.</td>
</tr>
<tr class="odd">
<td><a href="msbts-groupsetting-lmsfragmentsize-property-wmi.md">LMSFragmentSize</a></td>
<td>Gets or sets the fragment size, in bytes, for large message support.</td>
</tr>
<tr class="even">
<td><a href="msbts-groupsetting-lmsthreshold-property-wmi.md">LMSThreshold</a></td>
<td>Gets the threshold size, in bytes, for large message support.</td>
</tr>
<tr class="odd">
<td><a href="msbts-groupsetting-majorversion-property-wmi.md">MajorVersion</a></td>
<td>Gets the major version number of the BizTalk Server installed. For internal use only.</td>
</tr>
<tr class="even">
<td><a href="msbts-groupsetting-mgmtdbname-property-wmi.md">MgmtDbName</a></td>
<td>Gets the database name of the initial catalog part of the BizTalk Management database connection string.</td>
</tr>
<tr class="odd">
<td><a href="msbts-groupsetting-mgmtdbservername-property-wmi.md">MgmtDbServerName</a></td>
<td>Gets the data source part of the BizTalk Management database connection string.</td>
</tr>
<tr class="even">
<td><a href="msbts-groupsetting-minorversion-property-wmi.md">MinorVersion</a></td>
<td>Gets the minor version number of the installed BizTalk Management server. This member supports the BizTalk Server infrastructure and is not intended to be used directly from your code.</td>
</tr>
<tr class="odd">
<td><a href="msbts-groupsetting-name-property-wmi.md">Name</a></td>
<td>Gets the name of the group.</td>
</tr>
<tr class="even">
<td><a href="msbts-groupsetting-ruleenginedbname-property-wmi.md">RuleEngineDBName</a></td>
<td>Gets or sets the name of the RuleEngine SQL Server database.</td>
</tr>
<tr class="odd">
<td><a href="msbts-groupsetting-ruleenginedbservername-property-wmi.md">RuleEngineDBServerName</a></td>
<td>Gets or sets the name of the SQL server where RuleEngine database is located.</td>
</tr>
<tr class="even">
<td>SettingID (Inherited from <strong>CIM_Setting</strong>)</td>
<td>For more information about the <strong>CIM_Setting</strong> class, see the Windows Management Instrumentation documentation at <a href="https://go.microsoft.com/fwlink/?linkid=83193">https://go.microsoft.com/fwlink/?LinkID=83193</a>.</td>
</tr>
<tr class="odd">
<td><a href="msbts-groupsetting-signcertcomment-property-wmi.md">SignCertComment</a></td>
<td>Gets or sets a comment field that can be use to associate some friendly name with a signing certificate.</td>
</tr>
<tr class="even">
<td><a href="msbts-groupsetting-signcertthumbprint-property-wmi.md">SignCertThumbprint</a></td>
<td>Gets or sets the thumbprint of the signing certificate used to sign outbound documents sent by any host in the group.</td>
</tr>
<tr class="odd">
<td><a href="msbts-groupsetting-ssoservername-property-wmi.md">SSOServerName</a></td>
<td>Gets the name of the machine where Single Sign On (SSO) server resides on.</td>
</tr>
<tr class="even">
<td><a href="msbts-groupsetting-subscriptiondbname-property-wmi.md">SubscriptionDBName</a></td>
<td>Gets the name of the master subscription SQL database.</td>
</tr>
<tr class="odd">
<td><a href="msbts-groupsetting-subscriptiondbservername-property-wmi.md">SubscriptionDBServerName</a></td>
<td>Gets the name of the server running Microsoft® SQL Server™ where the master subscription database is located.</td>
</tr>
<tr class="even">
<td><a href="msbts-groupsetting-trackinganalysisdbname-property-wmi.md">TrackingAnalysisDBName</a></td>
<td><strong>Warning:</strong> This property has been deprecated in BizTalk Server.<br />
<br />
Gets or sets the name of the tracking SQL analysis database.</td>
</tr>
<tr class="odd">
<td><a href="msbts-groupsetting-trackinganalysisdbservername-property-wmi.md">TrackingAnalysisDBServerName</a></td>
<td><strong>Warning:</strong> This property has been deprecated in BizTalk Server.<br />
<br />
Contains the name of the tracking SQL analysis server.</td>
</tr>
<tr class="even">
<td><a href="msbts-groupsetting-trackingdbname-property-wmi.md">TrackingDBName</a></td>
<td>Gets the name of the tracking SQL database.</td>
</tr>
<tr class="odd">
<td><a href="msbts-groupsetting-trackingdbservername-property-wmi.md">TrackingDBServerName</a></td>
<td>Gets the name of the server running SQL Server where the tracking database is located.</td>
</tr>
</tbody>
</table>


**MSBTS\_GroupSetting** defines the following methods:

<table>
<thead>
<tr class="header">
<th>Method</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><a href="msbts-groupsetting-registerlocalserver-method-wmi.md">RegisterLocalServer</a></td>
<td>Sets up the Windows NT registry of the local computer to point to this organization.</td>
</tr>
<tr class="even">
<td><a href="msbts-groupsetting-unregisterlocalserver-method-wmi.md">UnRegisterLocalServer</a></td>
<td>Removes the local Windows NT registry keys that store organization information.</td>
</tr>
</tbody>
</table>


## Remarks

**GroupSetting** is the management abstraction for global BizTalk Server properties.

## Requirements

**Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.

**Namespace:** Included in \\root\\MicrosoftBizTalkServer.
