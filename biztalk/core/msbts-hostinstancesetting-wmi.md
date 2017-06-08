---
title: "MSBTS_HostInstanceSetting (WMI) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a3adb52f-f106-4221-8794-01ed32c50605
caps.latest.revision: 11
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MSBTS_HostInstanceSetting (WMI)
Updates the **IsDisabled** property when a host is in the stopped state.  
  
## Declaration  
  
```  
class MSBTS_HostInstanceSetting : MSBTS_Setting  
```  
  
## Members  
 **MSBTS_HostInstanceSetting** defines the following properties:  
  
|Property|Description|  
|--------------|-----------------|  
|Caption (Inherited from **CIM_Setting**)|For more information about the **CIM_Setting** class, see the Windows Management Instrumentation documentation at [http://go.microsoft.com/fwlink/?LinkID=20246](http://go.microsoft.com/fwlink/?LinkID=20246).|  
|[ConfigurationState](../core/msbts-hostinstancesetting-configurationstate-property-wmi.md)|Contains the installation state for given instance of the BizTalk host.|  
|Description (Inherited from **CIM_Setting**)|For more information about the **CIM_Setting** class, see the Windows Management Instrumentation documentation at [http://go.microsoft.com/fwlink/?LinkID=20246](http://go.microsoft.com/fwlink/?LinkID=20246).|  
|[HostName](../core/msbts-hostinstancesetting-hostname-property-wmi.md)|Contains the name of the BizTalk host to which this BizTalk host instance belongs.|  
|[HostType](../core/msbts-hostinstancesetting-hosttype-property-wmi.md)|Indicates which runtime model the instances of the BizTalk host will be running in.|  
|[IsDisabled](../core/msbts-hostinstancesetting-isdisabled-property-wmi.md)|Enables or disables a host instance.|  
|[Logon](../core/msbts-hostinstancesetting-logon-property-wmi.md)|Contains the logon information that this BizTalk host instance is using.|  
|[MgmtDbNameOverride](../core/msbts-hostinstancesetting-mgmtdbnameoverride-property-wmi.md)|Overrides the initial catalog part of the BizTalk Management database connect string, and represents the database name. This property was not implemented for [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] and is reserved for future use.|  
|[MgmtDbServerOverride](../core/msbts-hostinstancesetting-mgmtdbserveroverride-property-wmi.md)|Overrides the data source part of the BizTalk Management database connect string. This property was not implemented for [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] and is reserved for future use.|  
|[Name](../core/msbts-hostinstancesetting-name-property-wmi.md)|Contains the name of the host instance.|  
|[NTGroupName](../core/msbts-hostinstancesetting-ntgroupname-property-wmi.md)|Contains the name of the Microsoft® Windows NT® group.|  
|[RunningServer](../core/msbts-hostinstancesetting-runningserver-property-wmi.md)|Contains the name of the server on which the host instance runs.|  
|SettingID (Inherited from **CIM_Setting**)|For more information about the **CIM_Setting** class, see the Windows Management Instrumentation documentation at [http://go.microsoft.com/fwlink/?LinkID=20246](http://go.microsoft.com/fwlink/?LinkID=20246).|  
  
## Remarks  
 This class should only be used to update the [IsDisabled](../core/msbts-hostinstance-isdisabled-property-wmi.md) property for a host in the stopped state, which can also be done by [MSBTS_HostInstance](../core/msbts-hostinstance-wmi.md).  
  
## Requirements  
 **Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.  
  
 **Namespace:** Included in \root\MicrosoftBizTalkServer.