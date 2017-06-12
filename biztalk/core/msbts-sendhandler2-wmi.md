---
title: "MSBTS_SendHandler2 (WMI) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 732a03ae-c699-45cc-be92-06cf9cac7ce1
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MSBTS_SendHandler2 (WMI)
Represents an individual send handler defined by the BizTalk Server.  
  
## Declaration  
 class MSBTS_SendHandler2 : MSBTS_Setting  
  
## Members  
  
|Property Name|Description|  
|-------------------|-----------------|  
|[MSBTS_SendHandler2.AdapterName Property (WMI)](../core/msbts-sendhandler2-adaptername-property-wmi.md)|This property contains the name of the adapter used by the given instance.|  
|[MSBTS_SendHandler2.CustomCfg Property (WMI)](../core/msbts-sendhandler2-customcfg-property-wmi.md)|This property contains adapter-specific configuration in XML format.|  
|[MSBTS_SendHandler2.HostName Property (WMI)](../core/msbts-sendhandler2-hostname-property-wmi.md)|This property contains the name of the BizTalk Host for this transport handler.|  
|[MSBTS_SendHandler2.HostNameToSwitchTo Property (WMI)](../core/msbts-sendhandler2-hostnametoswitchto-property-wmi.md)|This property contains the name of the BizTalk Host that this transport handler should switch to.|  
|[MSBTS_SendHandler2.IsDefault Property (WMI)](../core/msbts-sendhandler2-isdefault-property-wmi.md)|This property indicates whether the send handler is the default one for this adapter type.|  
|[MSBTS_SendHandler2.MgmtDbNameOverride Property (WMI)](../core/msbts-sendhandler2-mgmtdbnameoverride-property-wmi.md)|This optional property can be used to override the initial catalog part of the BizTalk Messaging Management database connect string, and represents the database name.|  
|[MSBTS_SendHandler2.MgmtDbServerOverride Property (WMI)](../core/msbts-sendhandler2-mgmtdbserveroverride-property-wmi.md)|This optional property can be used to override the data source part of the BizTalk Messaging Management database connect string.|  
  
## Requirements  
 **Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.  
  
 **Namespace:** Included in \root\MicrosoftBizTalkServer.