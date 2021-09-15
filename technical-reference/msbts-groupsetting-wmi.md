---
description: "Learn more about: MSBTS_GroupSetting (WMI)"
title: MSBTS_GroupSetting (WMI)
TOCTitle: MSBTS_GroupSetting (WMI)
ms:assetid: bb440da1-b650-4345-80d5-949bcc774b5f
ms:mtpsurl: https://msdn.microsoft.com/library/Aa578341(v=BTS.80)
ms:contentKeyID: 51530817
ms.date: 09/13/2021
mtps_version: v=BTS.80
---

# MSBTS\_GroupSetting (WMI)

 

Represents a logical grouping of Microsoft® BizTalk® Servers.

## Declaration

class MSBTS\_GroupSetting : MSBTS\_Setting

## Members

**MSBTS\_GroupSetting** defines the following properties:

| Property | Description |
| --- | --- |
| [AllowTrackingSettingsImport](msbts-groupsetting-allowtrackingsettingsimport-property-wmi.md) | Gets or sets whether tracking settings will be imported while importing binding files. Available starting with BizTalk Server 2020. |
| AnalyticsEnabled | Enables or disables analytics for the BizTalk group. For more information, see [Update the BizTalk group settings](/biztalk/core/how-to-modify-group-settings). |
| AnalyticsTargetProviderConfig | This property is used to configure the analytics target when analytics is enabled. For more information, see [Update the BizTalk group settings](/biztalk/core/how-to-modify-group-settings). |
| AnalyticsTargetProviderId | This property is used to configure the analytics target when analytics is enabled. For more information, see [Update the BizTalk group settings](/biztalk/core/how-to-modify-group-settings). |
| [AuditingEnabled](msbts-groupsetting-auditingenabled-property-wmi.md) | Enables or disables auditing for the BizTalk group. Available starting with BizTalk Server 2020. |
| [BamDBName](msbts-groupsetting-bamdbname-property-wmi.md) | Gets or sets the name of the BAM SQL database. |
| [BamDBServerName](msbts-groupsetting-bamdbservername-property-wmi.md) | Gets or sets the name of the SQL server where BAM database is located. |
| [BizTalkAdministratorGroup](msbts-groupsetting-biztalkadministratorgroup-property-wmi.md) | Gets the name of the BizTalk Administrator Windows Group. |
| [BizTalkB2BOperatorGroup](msbts-groupsetting-biztalkb2boperatorgroup-property-wmi.md) | Gets the name of the BizTalk B2B Operators Windows Group. |
| [BizTalkOperatorGroup](msbts-groupsetting-biztalkoperatorgroup-property-wmi.md) | Gets the name of the BizTalk Operators Windows Group. |
| [BizTalkReadOnlyUserGroup](msbts-groupsetting-biztalkreadonlyusergroup-property-wmi.md) | Gets the name of the BizTalk ReadOnly User Windows Group. |
| Caption (Inherited from **CIM_Setting**) | For more information, see [CIM_Setting class (CIMWin32 WMI Providers)](/windows/win32/cimwin32prov/cim-setting). |
| [ConfigurationCacheRefreshInterval](msbts-groupsetting-configurationcacherefreshinterval-property-wmi.md) | Gets or sets how often BizTalk Server refreshes the cache of the messaging configuration objects, in seconds. |
| Description (Inherited from **CIM_Setting**) | For more information, see [CIM_Setting class (CIMWin32 WMI Providers)](/windows/win32/cimwin32prov/cim-setting). |
| [GlobalTrackingOption](msbts-groupsetting-globaltrackingoption-property-wmi.md) | Gets the level of tracking that the BizTalk server should perform. |
| [LMSFragmentSize](msbts-groupsetting-lmsfragmentsize-property-wmi.md) | Gets or sets the fragment size, in bytes, for large message support. |
| [LMSThreshold](msbts-groupsetting-lmsthreshold-property-wmi.md) | Gets the threshold size, in bytes, for large message support. |
| [MajorVersion](msbts-groupsetting-majorversion-property-wmi.md) | Gets the major version number of the BizTalk Server installed. For internal use only. |
| [MaxAuditEntries](msbts-groupsetting-maxauditentries-property-wmi.md) | Gets or sets the maximum number of entries in  audit log table when **AuditingEnabled** is set to TRUE. Available starting with BizTalk Server 2020. |
| [MgmtDbName](msbts-groupsetting-mgmtdbname-property-wmi.md) | Gets the database name of the initial catalog part of the BizTalk Management database connection string. |
| [MgmtDbServerName](msbts-groupsetting-mgmtdbservername-property-wmi.md) | Gets the data source part of the BizTalk Management database connection string. |
| [MinorVersion](msbts-groupsetting-minorversion-property-wmi.md) | Gets the minor version number of the installed BizTalk Management server. This member supports the BizTalk Server infrastructure, and isn't intended to be used directly from your code. |
| [Name](msbts-groupsetting-name-property-wmi.md) | Gets the name of the group. |
| [PerfCounterCacheRefreshInterval](msbts-groupsetting-perfcountercacherefreshinterval-property-wmi.md) | Gets or sets the interval at which performance counters are refreshed, in seconds. |
| [ReceiverFaultToleranceEnabled](msbts-groupsetting-receiverfaulttoleranceenabled-property-wmi.md) | Enables or disables receive location fault tolerance. Available starting with BizTalk Server 2020. |
| [ReceiverFaultToleranceRetryInterval](msbts-groupsetting-receiverfaulttoleranceretryinterval-property-wmi.md) | Gets or sets how often the server attempts to recover receive location from failures when **ReceiverFaultToleranceEnabled** is set to TRUE. Available starting with BizTalk Server 2020. |
| [RuleEngineDBName](msbts-groupsetting-ruleenginedbname-property-wmi.md) | Gets or sets the name of the RuleEngine SQL Server database. |
| [RuleEngineDBServerName](msbts-groupsetting-ruleenginedbservername-property-wmi.md) | Gets or sets the name of the SQL server where RuleEngine database is located. |
| SettingID (Inherited from **CIM_Setting**) | For more information, see [CIM_Setting class (CIMWin32 WMI Providers)](/windows/win32/cimwin32prov/cim-setting). |
| [SignCertComment](msbts-groupsetting-signcertcomment-property-wmi.md) | Gets or sets a comment field that can be use to associate some friendly name with a signing certificate. |
| [SignCertThumbprint](msbts-groupsetting-signcertthumbprint-property-wmi.md) | Gets or sets the thumbprint of the signing certificate used to sign outbound documents sent by any host in the group. |
| [SSOServerName](msbts-groupsetting-ssoservername-property-wmi.md) | Gets the name of the machine where Single Sign On (SSO) server resides on. |
| [SubscriptionDBName](msbts-groupsetting-subscriptiondbname-property-wmi.md) | Gets the name of the master subscription SQL database. |
| [SubscriptionDBServerName](msbts-groupsetting-subscriptiondbservername-property-wmi.md) | Gets the name of the server running Microsoft SQL Server where the master subscription database is located. |
| [TrackingAnalysisDBName](msbts-groupsetting-trackinganalysisdbname-property-wmi.md) | Gets or sets the name of the tracking SQL analysis database. This property is deprecated. |
| [TrackingAnalysisDBServerName](msbts-groupsetting-trackinganalysisdbservername-property-wmi.md) | Contains the name of the tracking SQL analysis server. This property is deprecated. |
| [TrackingDBName](msbts-groupsetting-trackingdbname-property-wmi.md) | Gets the name of the tracking SQL database. |
| [TrackingDBServerName](msbts-groupsetting-trackingdbservername-property-wmi.md) | Gets the name of the server running SQL Server where the tracking database is located. |

**MSBTS\_GroupSetting** defines the following methods:

| Method | Description |
| --- | --- |
| [RegisterLocalServer](msbts-groupsetting-registerlocalserver-method-wmi.md) | Sets up the Windows NT registry of the local computer to point to this organization. |
| [UnRegisterLocalServer](msbts-groupsetting-unregisterlocalserver-method-wmi.md) | Removes the local Windows NT registry keys that store organization information. |

## Remarks

**GroupSetting** is the management abstraction for global BizTalk Server properties.

## Requirements

**Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.

**Namespace:** Included in `\\root\\MicrosoftBizTalkServer`.
