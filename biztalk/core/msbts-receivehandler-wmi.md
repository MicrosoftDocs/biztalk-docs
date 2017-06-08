---
title: "MSBTS_ReceiveHandler (WMI) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1c04de0e-b85d-4e1a-ad18-bd625f05e025
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MSBTS_ReceiveHandler (WMI)
Represents an individual receive handler defined by Microsoft BizTalk Server.  
  
## Declaration  
  
```  
class MSBTS_ReceiveHandler : MSBTS_Setting  
```  
  
## Members  
 **MSBTS_ReceiveHandler** defines the following properties:  
  
|Property|Description|  
|--------------|-----------------|  
|[AdapterName](../core/msbts-receivehandler-adaptername-property-wmi.md)|Contains the name of the adapter.|  
|Caption (Inherited from **CIM_Setting**)|For more information about the **CIM_Setting** class, see the Windows Management Instrumentation documentation at [http://go.microsoft.com/fwlink/?LinkID=20246](http://go.microsoft.com/fwlink/?LinkID=20246).|  
|[CustomCfg](../core/msbts-receivehandler-customcfg-property-wmi.md)|Contains the adapter-specific configuration in XML format.|  
|Description (Inherited from **CIM_Setting**)|For more information about the **CIM_Setting** class, see the Windows Management Instrumentation documentation at [http://go.microsoft.com/fwlink/?LinkID=20246](http://go.microsoft.com/fwlink/?LinkID=20246).|  
|[HostName](../core/msbts-receivehandler-hostname-property-wmi.md)|Contains the name of the BizTalk Host for this adapter.|  
|[HostNameToSwitchTo](../core/msbts-receivehandler-hostnametoswitchto-property-wmi.md)|Contains the name of the BizTalk Host that this adapter handler should switch to.|  
|[MgmtDbNameOverride](../core/msbts-receivehandler-mgmtdbnameoverride-property-wmi.md)|Overrides the initial catalog part of the BizTalk Management database connect string, and represents the database name. This property was not implemented for [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] and is reserved for future use.|  
|[MgmtDbServerOverride](../core/msbts-receivehandler-mgmtdbserveroverride-property-wmi.md)|Overrides the data source part of the BizTalk Management database connect string. This property was not implemented for [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] and is reserved for future use.|  
|SettingID (Inherited from **CIM_Setting**)|For more information about the **CIM_Setting** class, see the Windows Management Instrumentation documentation at [http://go.microsoft.com/fwlink/?LinkID=20246](http://go.microsoft.com/fwlink/?LinkID=20246).|  
  
## Remarks  
 For more information about the minimum security user rights required to administer a receive handler, see [Minimum Security User Rights](../core/minimum-security-user-rights.md).  
  
 For samples illustrating the **MSBTS_ReceiveHandler** class, see [WMI Script Samples](../core/wmi-script-samples.md).  
  
## Requirements  
 **Header:** Declared in BTSWMISchemaXP.mof.  
  
 **Namespace:** Included in \root\MicrosoftBizTalkServer.