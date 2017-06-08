---
title: "MSBTS_AdapterSetting (WMI) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4b775cb4-b8a8-40a4-9aa8-2363620d306d
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MSBTS_AdapterSetting (WMI)
Registers new adapters with Microsoft® BizTalk® Server.  
  
## Declaration  
  
```  
class MSBTS_AdapterSetting : MSBTS_Setting  
```  
  
## Members  
 **MSBTS_AdapterSetting** defines the following properties:  
  
|Property|Description|  
|--------------|-----------------|  
|Caption (Inherited from **CIM_Setting**)|For more information about the **CIM_Setting** class, see the Windows Management Instrumentation documentation at [http://go.microsoft.com/fwlink/?LinkID=20246](http://go.microsoft.com/fwlink/?LinkID=20246).|  
|[Comment](../core/msbts-adaptersetting-comment-property-wmi.md)|Gets or sets user comments.|  
|[Constraints](../core/msbts-adaptersetting-constraints-property-wmi.md)|Gets a bitmap with the constraints of the adapter.|  
|[DefaultInboundCfg](../core/msbts-adaptersetting-defaultinboundcfg-property-wmi.md)|Gets a default inbound configuration for the adapter.|  
|[DefaultOutboundCfg](../core/msbts-adaptersetting-defaultoutboundcfg-property-wmi.md)|Gets a default outbound configuration for the adapter.|  
|Description (Inherited from **CIM_Setting**)|For more information about the **CIM_Setting** class, see the Windows Management Instrumentation documentation at [http://go.microsoft.com/fwlink/?LinkID=20246](http://go.microsoft.com/fwlink/?LinkID=20246).|  
|[MgmtCLSID](../core/msbts-adaptersetting-mgmtclsid-property-wmi.md)|Gets the class ID (CLSID) of the COM component responsible for managing this adapter.|  
|[MgmtDbNameOverride](../core/msbts-adaptersetting-mgmtdbnameoverride-property-wmi.md)|Overrides the initial catalog part of the BizTalk Management database connect string, and represents the database name. This property was not implemented for [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] and is reserved for future use.|  
|[MgmtDbServerOverride](../core/msbts-adaptersetting-mgmtdbserveroverride-property-wmi.md)|Overrides the data source part of the BizTalk Management database connect string. This property was not implemented for [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] and is reserved for future use.|  
|[Name](../core/msbts-adaptersetting-name-property-wmi.md)|Gets the name of the adapter.|  
|SettingID (Inherited from **CIM_Setting**)|For more information about the **CIM_Setting** class, see the Windows Management Instrumentation documentation at [http://go.microsoft.com/fwlink/?LinkID=20246](http://go.microsoft.com/fwlink/?LinkID=20246).|  
  
## Remarks  
 Creating or deleting instances of this class registers and un-registers adapters from BizTalk Server. Enumerating instances of this class returns all the registered BizTalk adapters. Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] includes several native adapters such as FILE, FTP, HTTP, BizTalk Message Queuing, SMTP, SOAP, and SQL. You can develop custom adapters and register them using this class. For more information about native adapters, see [Using Adapters](../core/using-adapters.md). For more information about creating custom adapters, see [Developing Adapters Using the Adapter Framework](../core/developing-custom-adapters.md).  
  
 For more information about the minimum security user rights required to administer an adapter, see [Minimum Security User Rights](../core/minimum-security-user-rights.md).  
  
## Requirements  
 **Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.  
  
 **Namespace:** Included in \root\MicrosoftBizTalkServer.