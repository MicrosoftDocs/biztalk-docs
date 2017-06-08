---
title: "MSBTS_SendHandler (WMI) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e7bdf055-500c-47ea-8392-0798e2e9a9e0
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MSBTS_SendHandler (WMI)
Represents an individual send handler defined by the BizTalk Server.  
  
> [!NOTE]
>  This class cannot be used to create multiple send handlers; to create multiple send handlers, use [MSBTS_SendHandler2 (WMI)](../core/msbts-sendhandler2-wmi.md).  
  
## Declaration  
  
```  
class MSBTS_SendHandler : MSBTS_Setting  
```  
  
## Members  
 **MSBTS_SendHandler** defines the following properties:  
  
|Property|Description|  
|--------------|-----------------|  
|[AdapterName](../core/msbts-sendhandler-adaptername-property-wmi.md)|Contains the name of the adapter used.|  
|Caption (Inherited from **CIM_Setting**)|For more information about the **CIM_Setting** class, see the Windows Management Instrumentation documentation at [http://go.microsoft.com/fwlink/?LinkID=20246](http://go.microsoft.com/fwlink/?LinkID=20246).|  
|[CustomCfg](../core/msbts-sendhandler-customcfg-property-wmi.md)|Contains the protocol-specific configuration in XML format.|  
|Description (Inherited from **CIM_Setting**)|For more information about the **CIM_Setting** class, see the Windows Management Instrumentation documentation at [http://go.microsoft.com/fwlink/?LinkID=20246](http://go.microsoft.com/fwlink/?LinkID=20246).|  
|[HostName](../core/msbts-sendhandler-hostname-property-wmi.md)|Contains the name of the host this send handler.|  
|[MgmtDbNameOverride](../core/msbts-sendhandler-mgmtdbnameoverride-property-wmi.md)|Overrides the initial catalog part of the BizTalk Management database connect string, and represents the database name. This property was not implemented for [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] and is reserved for future use.|  
|[MgmtDbServerOverride](../core/msbts-sendhandler-mgmtdbserveroverride-property-wmi.md)|Overrides the data source part of the BizTalk Management database connect string. This property was not implemented for [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] and is reserved for future use.|  
|SettingID (Inherited from **CIM_Setting**)|For more information about the **CIM_Setting** class, see the Windows Management Instrumentation documentation at [http://go.microsoft.com/fwlink/?LinkID=20246](http://go.microsoft.com/fwlink/?LinkID=20246).|  
  
## Requirements  
 **Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.  
  
 **Namespace:** Included in \root\MicrosoftBizTalkServer.