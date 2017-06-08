---
title: "MSBTS_ServerHost (WMI) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 81e42b3b-c75f-47ae-837a-a38ef2304f56
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MSBTS_ServerHost (WMI)
Reflects the mapping between BizTalk servers and BizTalk Hosts.  
  
## Syntax  
  
```  
  
class MSBTS_ServerHost : MSBTS_BTSObject  
```  
  
## Members  
 **MSBTS_ServerHost** defines the following properties:  
  
|Property|Description|  
|--------------|-----------------|  
|Caption (Inherited from **CIM_ManagedSystemElement**)|For more information about the **CIM_ManagedSystemElement** class, see the Windows Management Instrumentation documentation at [http://go.microsoft.com/fwlink/?LinkID=20245](http://go.microsoft.com/fwlink/?LinkID=20245).|  
|Description (Inherited from **CIM_ManagedSystemElement**)|For more information about the **CIM_ManagedSystemElement** class, see the Windows Management Instrumentation documentation at [http://go.microsoft.com/fwlink/?LinkID=20245](http://go.microsoft.com/fwlink/?LinkID=20245).|  
|[HostName](../core/msbts-serverhost-hostname-property-wmi.md)|Contains the name of the host.|  
|InstallDate (Inherited from **CIM_ManagedSystemElement**)|For more information about the **CIM_ManagedSystemElement** class, see the Windows Management Instrumentation documentation at [http://go.microsoft.com/fwlink/?LinkID=20245](http://go.microsoft.com/fwlink/?LinkID=20245).|  
|[IsMapped](../core/msbts-serverhost-ismapped-property-wmi.md)|Indicates whether the specified server works with the specified MessageBox.|  
|[MgmtDbNameOverride](../core/msbts-serverhost-mgmtdbnameoverride-property-wmi.md)|Overrides the initial catalog part of the BizTalk Management database connect string, and represents the database name. This property was not implemented for [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] and is reserved for future use.|  
|[MgmtDbServerOverride](../core/msbts-serverhost-mgmtdbserveroverride-property-wmi.md)|Overrides the data source part of the BizTalk Management database connect string. This property was not implemented for [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] and is reserved for future use.|  
|Name (Inherited from **CIM_ManagedSystemElement**)|For more information about the **CIM_ManagedSystemElement** class, see the Windows Management Instrumentation documentation at [http://go.microsoft.com/fwlink/?LinkID=20245](http://go.microsoft.com/fwlink/?LinkID=20245).|  
|[ServerName](../core/msbts-serverhost-servername-property-wmi.md)|Contains the name of the server.|  
|Status (Inherited from **CIM_ManagedSystemElement**)|For more information about the **CIM_ManagedSystemElement** class, see the Windows Management Instrumentation documentation at [http://go.microsoft.com/fwlink/?LinkID=20245](http://go.microsoft.com/fwlink/?LinkID=20245).|  
  
 **MSBTS_ServerAppType** defines the following methods:  
  
|Method|Description|  
|------------|-----------------|  
|[ForceUnmap](../core/msbts-serverhost-forceunmap-method-wmi.md)|Unmaps the server from the MessageBox even whether or if not all applications cannot be uninstalled.|  
|[Map](../core/msbts-serverhost-map-method-wmi.md)|Maps the server to the MessageBox without installing applications.|  
|[Unmap](../core/msbts-serverhost-unmap-method-wmi.md)|Unmaps the server from the MessageBox.|  
  
## Remarks  
 There is one instance of this Windows Management Instrumentation (WMI )class per every server/host combination in the BizTalk group. Instances of this class are created and deleted automatically.  
  
 For samples illustrating the **MSBTS_ServerHost** class, see [WMI Script Samples](../core/wmi-script-samples.md).  
  
## Requirements  
 **Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.  
  
 **Namespace:** Included in \root\MicrosoftBizTalkServer.