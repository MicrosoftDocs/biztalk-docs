---
title: "MSBTS_HostQueue (WMI) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 25a01b53-4759-4914-a742-df065b90c3e6
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MSBTS_HostQueue (WMI)
Represents an application.  
  
## Syntax  
  
```  
  
class MSBTS_HostQueue : MSBTS_BTSObject  
```  
  
## Members  
 **MSBTS_HostQueue** defines the following properties:  
  
|Property|Description|  
|--------------|-----------------|  
|Caption (Inherited from **CIM_ManagedSystemElement**)|For more information about the **CIM_ManagedSystemElement** class, see the Windows Management Instrumentation documentation at [http://go.microsoft.com/fwlink/?LinkID=20245](http://go.microsoft.com/fwlink/?LinkID=20245).|  
|Description (Inherited from **CIM_ManagedSystemElement**)|For more information about the **CIM_ManagedSystemElement** class, see the Windows Management Instrumentation documentation at [http://go.microsoft.com/fwlink/?LinkID=20245](http://go.microsoft.com/fwlink/?LinkID=20245).|  
|[HostName](../core/msbts-hostqueue-hostname-property-wmi.md)|Contains the name of the host that corresponds to the queue.|  
|InstallDate (Inherited from **CIM_ManagedSystemElement**)|For more information about the **CIM_ManagedSystemElement** class, see the Windows Management Instrumentation documentation at [http://go.microsoft.com/fwlink/?LinkID=20245](http://go.microsoft.com/fwlink/?LinkID=20245).|  
|[MgmtDbNameOverride](../core/msbts-hostqueue-mgmtdbnameoverride-property-wmi.md)|Overrides the initial catalog part of the BizTalk Management database connect string, and represents the database name. This property was not implemented for [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] and is reserved for future use.|  
|[MgmtDbServerOverride](../core/msbts-hostqueue-mgmtdbserveroverride-property-wmi.md)|Overrides the data source part of the BizTalk Management database connect string. This property was not implemented for [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] and is reserved for future use.|  
|Name (Inherited from **CIM_ManagedSystemElement**)|For more information about the **CIM_ManagedSystemElement** class, see the Windows Management Instrumentation documentation at [http://go.microsoft.com/fwlink/?LinkID=20245](http://go.microsoft.com/fwlink/?LinkID=20245).|  
|Status (Inherited from **CIM_ManagedSystemElement**)|For more information about the **CIM_ManagedSystemElement** class, see the Windows Management Instrumentation documentation at [http://go.microsoft.com/fwlink/?LinkID=20245](http://go.microsoft.com/fwlink/?LinkID=20245).|  
  
 **MSBTS_HostQueue** defines the following methods:  
  
|Property|Description|  
|--------------|-----------------|  
|[ResumeServiceInstancesByID](../core/msbts-hostqueue-resumeserviceinstancesbyid-method-wmi.md)|Resubmits service instances by ID.|  
|[SuspendServiceInstancesByID](../core/msbts-hostqueue-suspendserviceinstancesbyid-method-wmi.md)|Moves service instances to the suspended queue by ID.|  
|[TerminateServiceInstancesByID](../core/msbts-hostqueue-terminateserviceinstancesbyid-method-wmi.md)|Terminates service instances by ID.|  
  
## Requirements  
 **Header:** Declared in BTSWMISchemaXP.mof.  
  
 **Namespace:** Included in \root\MicrosoftBizTalkServer.