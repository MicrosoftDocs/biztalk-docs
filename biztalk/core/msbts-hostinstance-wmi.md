---
title: "MSBTS_HostInstance (WMI) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6bb4aa2b-84b4-4213-b711-eb2fb82e5748
caps.latest.revision: 13
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MSBTS_HostInstance (WMI)
Represents a single instance of a BizTalk Host.  
  
## Declaration  
  
```  
class MSBTS_HostInstance : MSBTS_Service  
```  
  
## Members  
 **MSBTS_HostInstance** defines the following properties:  
  
|Property|Description|  
|--------------|-----------------|  
|[MSBTS_HostInstance.ClusterInstanceType Property (WMI)](../core/msbts-hostinstance-clusterinstancetype-property-wmi.md)|This property tells whether the BizTalk Host Instance NT service is clustered.|  
|Caption (Inherited from **CIM_ManagedSystemElement**)|For more information about the **CIM_ManagedSystemElement** class, see the Windows Management Instrumentation documentation at [http://go.microsoft.com/fwlink/?LinkID=20245](http://go.microsoft.com/fwlink/?LinkID=20245).|  
|[ConfigurationState](../core/msbts-hostinstance-configurationstate-property-wmi.md)|Contains the installation state for given instance of the BizTalk host.|  
|Description (Inherited from **CIM_ManagedSystemElement**)|For more information about the **CIM_ManagedSystemElement** class, see the Windows Management Instrumentation documentation at [http://go.microsoft.com/fwlink/?LinkID=20245](http://go.microsoft.com/fwlink/?LinkID=20245).|  
|[HostName](../core/msbts-hostinstance-hostname-property-wmi.md)|Contains the name of the BizTalk host to which this BizTalk host instance belongs.|  
|[HostType](../core/msbts-hostinstance-hosttype-property-wmi.md)|Indicates which runtime model the instances of the BizTalk host will be running in.|  
|InstallDate (Inherited from **CIM_ManagedSystemElement**)|For more information about the **CIM_ManagedSystemElement** class, see the Windows Management Instrumentation documentation at [http://go.microsoft.com/fwlink/?LinkID=20245](http://go.microsoft.com/fwlink/?LinkID=20245).|  
|[IsDisabled](../core/msbts-hostinstance-isdisabled-property-wmi.md)|Enables or disables a host instance.|  
|[Logon](../core/msbts-hostinstance-logon-property-wmi.md)|Contains the logon information that this BizTalk host instance is using.|  
|[MgmtDbNameOverride](../core/msbts-hostinstance-mgmtdbnameoverride-property-wmi.md)|Overrides the initial catalog part of the BizTalk Management database connect string, and represents the database name. This property was not implemented for [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] and is reserved for future use.|  
|[MgmtDbServerOverride](../core/msbts-hostinstance-mgmtdbserveroverride-property-wmi.md)|Overrides the data source part of the BizTalk Management database connect string. This property was not implemented for [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] and is reserved for future use.|  
|[Name](../core/msbts-hostinstance-name-property-wmi.md)|Contains the name of the host instance.|  
|[NTGroupName](../core/msbts-hostinstance-ntgroupname-property-wmi.md)|Contains the name of the Microsoft Windows NT group.|  
|[RunningServer](../core/msbts-hostinstance-runningserver-property-wmi.md)|Contains the name of the server on which the host instance runs.|  
|[ServiceState](../core/msbts-hostinstance-servicestate-property-wmi.md)|Contains the state of the host instance.|  
|Status (Inherited from **CIM_ManagedSystemElement**)|For more information about the **CIM_ManagedSystemElement** class, see the Windows Management Instrumentation documentation at [http://go.microsoft.com/fwlink/?LinkID=20245](http://go.microsoft.com/fwlink/?LinkID=20245).|  
|[UniqueID](../core/msbts-hostinstance-uniqueid-property-wmi.md)|Contains the unique ID of the host instance.|  
  
 **MSBTS_HostInstance** defines the following methods:  
  
|Method|Description|  
|------------|-----------------|  
|[GetState](../core/msbts-hostinstance-getstate-method-wmi.md)|Retrieves the state of the given instance of the BizTalk host.|  
|[Install](../core/msbts-hostinstance-install-method.md)|Installs a service for the given instance of the BizTalk host.|  
|[Start](../core/msbts-hostinstance-start-method-wmi.md)|Starts the given instance of the BizTalk host.|  
|[Stop](../core/msbts-hostinstance-stop-method-wmi.md)|Stops the given instance of the BizTalk host.|  
|[Uninstall](../core/msbts-hostinstance-uninstall-method-wmi.md)|Uninstalls a service for the given instance of the BizTalk host.|  
  
## Remarks  
 For more information about the minimum security user rights required to administer a Host instance, see [Minimum Security User Rights](../core/minimum-security-user-rights.md).  
  
> [!NOTE]
>  Always specify the name of the local server when using WMI. When you enumerate host instances, both local and remote instances will be returned. You can then call start, stop and other methods.  
  
 For samples illustrating the **MSBTS_HostInstance** class, see [WMI Script Samples](../core/wmi-script-samples.md).  
  
## Requirements  
 **Header:** Declared in BTSWMISchemaXP.mof.  
  
 **Namespace:** Included in \root\MicrosoftBizTalkServer.