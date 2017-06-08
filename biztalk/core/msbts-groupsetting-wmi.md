---
title: "MSBTS_GroupSetting (WMI) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: bb440da1-b650-4345-80d5-949bcc774b5f
caps.latest.revision: 12
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MSBTS_GroupSetting (WMI)
Represents a logical grouping of Microsoft® BizTalk® Servers.  
  
## Declaration  
 class MSBTS_GroupSetting : MSBTS_Setting  
  
## Members  
 **MSBTS_GroupSetting** defines the following properties:  
  
|Property|Description|  
|--------------|-----------------|  
|[BamDBName](../core/msbts-groupsetting-bamdbname-property-wmi.md)|Gets or sets the name of the BAM SQL database.|  
|[BamDBServerName](../core/msbts-groupsetting-bamdbservername-property-wmi.md)|Gets or sets the name of the SQL server where BAM database is located.|  
|[BizTalkAdministratorGroup](../core/msbts-groupsetting-biztalkadministratorgroup-property-wmi.md)|Gets the name of the BizTalk Administrator Microsoft® Windows NT® Group.|  
|Caption (Inherited from **CIM_Setting**)|For more information about the **CIM_Setting** class, see the Windows Management Instrumentation documentation at [http://go.microsoft.com/fwlink/?LinkID=83193](http://go.microsoft.com/fwlink/?LinkID=83193).|  
|[MSBTS_GroupSetting.BizTalkOperatorGroup Property (WMI)](../core/msbts-groupsetting-biztalkoperatorgroup-property-wmi.md)|This property is the name of the BizTalk Operators Windows Group.|  
|[ConfigurationCacheRefreshInterval](../core/msbts-groupsetting-configurationcacherefreshinterval-property-wmi.md)|Gets or sets how often BizTalk Server refreshes the cache of the messaging configuration objects, in seconds.|  
|Description (Inherited from **CIM_Setting**)|For more information about the **CIM_Setting** class, see the Windows Management Instrumentation documentation at [http://go.microsoft.com/fwlink/?LinkID=83193](http://go.microsoft.com/fwlink/?LinkID=83193).|  
|[GlobalTrackingOption](../core/msbts-groupsetting-globaltrackingoption-property-wmi.md)|Gets the level of tracking that the BizTalk server should perform.|  
|[LMSFragmentSize](../core/msbts-groupsetting-lmsfragmentsize-property-wmi.md)|Gets or sets the fragment size, in bytes, for large message support.|  
|[LMSThreshold](../core/msbts-groupsetting-lmsthreshold-property-wmi.md)|Gets the threshold size, in bytes, for large message support.|  
|[MajorVersion](../core/msbts-groupsetting-majorversion-property-wmi.md)|Gets the major version number of the BizTalk Server installed. For internal use only.|  
|[MgmtDbName](../core/msbts-groupsetting-mgmtdbname-property-wmi.md)|Gets the database name of the initial catalog part of the BizTalk Management database connection string.|  
|[MgmtDbServerName](../core/msbts-groupsetting-mgmtdbservername-property-wmi.md)|Gets the data source part of the BizTalk Management database connection string.|  
|[MinorVersion](../core/msbts-groupsetting-minorversion-property-wmi.md)|Gets the minor version number of the installed BizTalk Management server. This member supports the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] infrastructure and is not intended to be used directly from your code.|  
|[Name](../core/msbts-groupsetting-name-property-wmi.md)|Gets the name of the group.|  
|[RuleEngineDBName](../core/msbts-groupsetting-ruleenginedbname-property-wmi.md)|Gets or sets the name of the RuleEngine SQL Server database.|  
|[RuleEngineDBServerName](../core/msbts-groupsetting-ruleenginedbservername-property-wmi.md)|Gets or sets the name of the SQL server where RuleEngine database is located.|  
|SettingID (Inherited from **CIM_Setting**)|For more information about the **CIM_Setting** class, see the Windows Management Instrumentation documentation at [http://go.microsoft.com/fwlink/?LinkID=83193](http://go.microsoft.com/fwlink/?LinkID=83193).|  
|[SignCertComment](../core/msbts-groupsetting-signcertcomment-property-wmi.md)|Gets or sets a comment field that can be use to associate some friendly name with a signing certificate.|  
|[SignCertThumbprint](../core/msbts-groupsetting-signcertthumbprint-property-wmi.md)|Gets or sets the thumbprint of the signing certificate used to sign outbound documents sent by any host in the group.|  
|[SSOServerName](../core/msbts-groupsetting-ssoservername-property-wmi.md)|Gets the name of the machine where Single Sign On (SSO) server resides on.|  
|[SubscriptionDBName](../core/msbts-groupsetting-subscriptiondbname-property-wmi.md)|Gets the name of the master subscription SQL database.|  
|[SubscriptionDBServerName](../core/msbts-groupsetting-subscriptiondbservername-property-wmi.md)|Gets the name of the server running Microsoft® SQL Server™ where the master subscription database is located.|  
|[TrackingAnalysisDBName](../core/msbts-groupsetting-trackinganalysisdbname-property-wmi.md)|**Warning:**  This property has been deprecated in [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]. <br /><br /> Gets or sets the name of the tracking SQL analysis database.|  
|[TrackingAnalysisDBServerName](../core/msbts-groupsetting-trackinganalysisdbservername-property-wmi.md)|**Warning:**  This property has been deprecated in [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]. <br /><br /> Contains the name of the tracking SQL analysis server.|  
|[TrackingDBName](../core/msbts-groupsetting-trackingdbname-property-wmi.md)|Gets the name of the tracking SQL database.|  
|[TrackingDBServerName](../core/msbts-groupsetting-trackingdbservername-property-wmi.md)|Gets the name of the server running SQL Server where the tracking database is located.|  
  
 **MSBTS_GroupSetting** defines the following methods:  
  
|Method|Description|  
|------------|-----------------|  
|[RegisterLocalServer](../core/msbts-groupsetting-registerlocalserver-method-wmi.md)|Sets up the Windows NT registry of the local computer to point to this organization.|  
|[UnRegisterLocalServer](../core/msbts-groupsetting-unregisterlocalserver-method-wmi.md)|Removes the local Windows NT registry keys that store organization information.|  
  
## Remarks  
 **GroupSetting** is the management abstraction for global BizTalk Server properties.  
  
## Requirements  
 **Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.  
  
 **Namespace:** Included in \root\MicrosoftBizTalkServer.