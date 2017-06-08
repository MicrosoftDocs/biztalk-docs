---
title: "MSBTS_ReceivePort (WMI) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8500b91b-60be-4a09-a711-b8c840016289
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MSBTS_ReceivePort (WMI)
Represents an individual receive port defined by BizTalk Server.  
  
## Declaration  
  
```  
class MSBTS_ReceivePort : MSBTS_Setting  
```  
  
## Members  
 **MSBTS_ReceivePort** defines the following properties:  
  
|Property|Description|  
|--------------|-----------------|  
|Caption (Inherited from **CIM_Setting**)|For more information about the **CIM_Setting** class, see the Windows Management Instrumentation documentation at [http://go.microsoft.com/fwlink/p/?LinkID=20246](http://go.microsoft.com/fwlink/p/?LinkID=20246).|  
|Description (Inherited from **CIM_Setting**)|For more information about the **CIM_Setting** class, see the Windows Management Instrumentation documentation at [http://go.microsoft.com/fwlink/p/?LinkID=20246](http://go.microsoft.com/fwlink/p/?LinkID=20246).|  
|[InboundTransforms](../core/msbts-receiveport-inboundtransforms-property-wmi.md)|Contains a string representation of the maps to apply per inbound document.|  
|[IsTwoWay](../core/msbts-receiveport-istwoway-property-wmi.md)|Indicates whether this port is a one way or two way port.|  
|[MgmtDbNameOverride](../core/msbts-receiveport-mgmtdbnameoverride-property-wmi.md)|Overrides the initial catalog part of the BizTalk Management database connect string, and represents the database name. This property was not implemented for [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] and is reserved for future use.|  
|[MgmtDbServerOverride](../core/msbts-receiveport-mgmtdbserveroverride-property-wmi.md)|Overrides the data source part of the BizTalk Management database connect string. This property was not implemented for [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] and is reserved for future use.|  
|[Name](../core/msbts-receiveport-name-property-wmi.md)|Contains the name of the receive port.|  
|[OutboundTransforms](../core/msbts-receiveport-outboundtransforms-property-wmi.md)|Contains a string representation of the maps to apply per outbound document.|  
|[PrimaryReceiveLocation](../core/msbts-receiveport-primaryreceivelocation-property-wmi.md)|Contains the name of the primary receive location for the port.|  
|[SendPipeline](../core/msbts-receiveport-sendpipeline-property-wmi.md)|Contains a name of the send pipeline for the port.|  
|SettingID (Inherited from **CIM_Setting**)|For more information about the **CIM_Setting** class, see the Windows Management Instrumentation documentation at [http://go.microsoft.com/fwlink/p/?LinkID=20246](http://go.microsoft.com/fwlink/p/?LinkID=20246).|  
|[Tracking](../core/msbts-receiveport-tracking-property-wmi.md)|Contains the tracking configuration for the port.|  
|[MSBTS_ReceivePort.RouteFailedMessage Property (WMI)](../core/msbts-receiveport-routefailedmessage-property-wmi.md)|This property controls whether failed messages have to be routed to failed message subscribers.|  
  
## Remarks  
 This class wraps the managed **Microsoft.BizTalk.ExplorerOM.ReceivePort** class. 
  
## Requirements  
 **Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.  
  
 **Namespace:** Included in \root\MicrosoftBizTalkServer.