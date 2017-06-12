---
title: "MSBTS_DeploymentService (WMI) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b2ff0753-edef-494c-980a-b5071faf23b2
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MSBTS_DeploymentService (WMI)
Encapsulates BizTalk assemblies for deployment or undeployment and bindings export or import.  
  
## Declaration  
  
```  
class MSBTS_DeploymentService : MSBTS_Setting  
```  
  
## Members  
 **MSBTS_DeploymentService** defines the following properties:  
  
|Property|Description|  
|--------------|-----------------|  
|Caption (Inherited from **CIM_Setting**)|For more information about the **CIM_Setting** class, see the Windows Management Instrumentation documentation at [http://go.microsoft.com/fwlink/?LinkID=20246](http://go.microsoft.com/fwlink/?LinkID=20246).|  
|Description (Inherited from **CIM_Setting**)|For more information about the **CIM_Setting** class, see the Windows Management Instrumentation documentation at [http://go.microsoft.com/fwlink/?LinkID=20246](http://go.microsoft.com/fwlink/?LinkID=20246).|  
|[MgmtDbNameOverride](../core/msbts-deploymentservice-mgmtdbnameoverride-property-wmi.md)|Overrides the initial catalog part of the BizTalk Management database connect string, and represents the database name. This property was not implemented for [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] and is reserved for future use.|  
|[MgmtDbServerOverride](../core/msbts-deploymentservice-mgmtdbserveroverride-property-wmi.md)|Overrides the data source part of the BizTalk Management database connect string. This property was not implemented for [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] and is reserved for future use.|  
|SettingID (Inherited from **CIM_Setting**)|For more information about the **CIM_Setting** class, see the Windows Management Instrumentation documentation at [http://go.microsoft.com/fwlink/?LinkID=20246](http://go.microsoft.com/fwlink/?LinkID=20246).|  
  
 **MSBTS_DeploymentService** defines the following methods:  
  
|Method|Description|  
|------------|-----------------|  
|[Deploy](../core/msbts-deploymentservice-deploy-method-wmi.md)|Deploys the assembly into the target database.|  
|[Export](../core/msbts-deploymentservice-export-method-wmi.md)|Exports the binding file from the target database.|  
|[Import](../core/msbts-deploymentservice-import-method-wmi.md)|Imports the binding file into the target database.|  
|[Remove](../core/msbts-deploymentservice-remove-method-wmi.md)|Removes the assembly from the target database.|  
  
## Requirements  
 **Header:** Declared in BTSWMISchemaXP.mof.  
  
 **Namespace:** Included in \root\MicrosoftBizTalkServer.