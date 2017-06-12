---
title: "MSBTS_Orchestration (WMI) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7811deb6-775f-4b9d-9587-d61c5b65a5ce
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MSBTS_Orchestration (WMI)
Represents an instance of an orchestration that belongs to the installed module.  
  
## Declaration  
  
```  
class MSBTS_Orchestration : MSBTS_Service  
```  
  
## Members  
 **MSBTS_Orchestration** defines the following properties:  
  
|Property|Description|  
|--------------|-----------------|  
|[AssemblyCulture](../core/msbts-orchestration-assemblyculture-property-wmi.md)|Contains the culture of the .NET assembly to which this orchestration belongs.|  
|[AssemblyName](../core/msbts-orchestration-assemblyname-property-wmi.md)|Contains the name of the Microsoft .NET-based assembly to which the orchestration belongs.|  
|[AssemblyPublicKeyToken](../core/msbts-orchestration-assemblypublickeytoken-property-wmi.md)|Contains the public key token of the .NET assembly to which this orchestration belongs.|  
|[AssemblyVersion](../core/msbts-orchestration-assemblyversion-property-wmi.md)|Contains the version of the .NET assembly to which this orchestration belongs.|  
|Caption (Inherited from **CIM_ManagedSystemElement**)|For more information about the **CIM_ManagedSystemElement** class, see the Windows Management Instrumentation documentation at [http://go.microsoft.com/fwlink/?LinkID=20245](http://go.microsoft.com/fwlink/?LinkID=20245).|  
|Description (Inherited from **CIM_ManagedSystemElement**)|For more information about the **CIM_ManagedSystemElement** class, see the Windows Management Instrumentation documentation at [http://go.microsoft.com/fwlink/?LinkID=20245](http://go.microsoft.com/fwlink/?LinkID=20245).|  
|[HostName](../core/msbts-orchestration-hostname-property-wmi.md)|Contains the name of the BizTalk Host with which this orchestration is enlisted.|  
|[MgmtDbNameOverride](../core/msbts-orchestration-mgmtdbnameoverride-property-wmi.md)|Overrides the initial catalog part of the BizTalk Management database connect string, and represents the database name. This property was not implemented for [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] and is reserved for future use.|  
|InstallDate (Inherited from **CIM_ManagedSystemElement**)|For more information about the **CIM_ManagedSystemElement** class, see the Windows Management Instrumentation documentation at [http://go.microsoft.com/fwlink/?LinkID=20245](http://go.microsoft.com/fwlink/?LinkID=20245).|  
|[MgmtDbServerOverride](../core/msbts-orchestration-mgmtdbserveroverride-property-wmi.md)|Overrides the data source part of the BizTalk Management database connect string. This property was not implemented for [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] and is reserved for future use.|  
|[Name](../core/msbts-orchestration-name-property-wmi.md)|Contains the name of the orchestration.|  
|[OrchestrationStatus](../core/msbts-orchestration-orchestrationstatus-property-wmi.md)|Indicates the status of the orchestration.|  
|Status (Inherited from **CIM_ManagedSystemElement**)|For more information about the **CIM_ManagedSystemElement** class, see the Windows Management Instrumentation documentation at [http://go.microsoft.com/fwlink/?LinkID=20245](http://go.microsoft.com/fwlink/?LinkID=20245).|  
  
 **MSBTS_Orchestration** defines the following methods:  
  
|Method|Description|  
|------------|-----------------|  
|[Enlist](../core/msbts-orchestration-enlist-method-wmi.md)|Enlists the orchestration by creating its activation subscription.|  
|[QueryDependencyInfo](../core/msbts-orchestration-querydependencyinfo-method-wmi.md)|Retrieves information about services that this service depends on through either a **CALL** or **START** relationship.|  
|[QueryInstanceInfo](../core/msbts-orchestration-queryinstanceinfo-method-wmi.md)|Retrieves information about instances of the orchestration in various states.|  
|[Start](../core/msbts-orchestration-start-method-wmi.md)|Starts the orchestration by enabling its activation subscription.|  
|[Stop](../core/msbts-orchestration-stop-method-wmi.md)|Stops the orchestration by disabling its activation subscription.|  
|[Unenlist](../core/msbts-orchestration-unenlist-method-wmi.md)|Terminates all instances of the orchestration and removes its activation subscription.|  
  
## Requirements  
 **Header:** Declared in BTSWMISchemaXP.mof.  
  
 **Namespace:** Included in \root\MicrosoftBizTalkServer.