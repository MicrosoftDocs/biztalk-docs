---
title: "MSBTS_SendPort (WMI) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3f3767e1-4590-41b2-8ee3-02eac6ea8c5c
caps.latest.revision: 14
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MSBTS_SendPort (WMI)
Represents an individual send port defined by BizTalk Server.  
  
> [!WARNING]
>  Certificates must be installed on the box for the MSBTS_SendPort class to work. The only way to create send ports without certificates is to use the [Microsoft.BizTalk.ExplorerOM](http://msdn.microsoft.com/library/microsoft.biztalk.explorerom.aspx) APIs.  
  
## Declaration  
  
```  
class MSBTS_SendPort : MSBTS_Setting  
```  
  
## Members  
 **MSBTS_SendPort** defines the following properties:  
  
|Property|Description|  
|--------------|-----------------|  
|Caption (Inherited from **CIM_Setting**)|For more information about the **CIM_Setting** class, see the Windows Management Instrumentation documentation at [http://go.microsoft.com/fwlink/?LinkID=20246](http://go.microsoft.com/fwlink/?LinkID=20246).|  
|Description (Inherited from **CIM_Setting**)|For more information about the **CIM_Setting** class, see the Windows Management Instrumentation documentation at [http://go.microsoft.com/fwlink/?LinkID=20246](http://go.microsoft.com/fwlink/?LinkID=20246).|  
|[EncryptionCert](../core/msbts-sendport-encryptioncert-property-wmi.md)|Specifies the certificate to use for outbound encryption.|  
|[Filter](../core/msbts-sendport-filter-property-wmi.md)|Contains textual representation of the filter.|  
|[InboundTransforms](../core/msbts-sendport-inboundtransforms-property-wmi.md)|Contains a string representation of the maps to apply per inbound document.|  
|[IsDynamic](../core/msbts-sendport-isdynamic-property-wmi.md)|Indicates whether this port is a dynamic or static.|  
|[IsTwoWay](../core/msbts-sendport-istwoway-property-wmi.md)|Indicates whether this port is a one way or two way port.|  
|[MgmtDbNameOverride](../core/msbts-sendport-mgmtdbnameoverride-property-wmi.md)|Overrides the initial catalog part of the BizTalk Management database connect string, and represents the database name. This property was not implemented for [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] and is reserved for future use.|  
|[MgmtDbServerOverride](../core/msbts-sendport-mgmtdbserveroverride-property-wmi.md)|Overrides the data source part of the BizTalk Management database connect string. This property was not implemented for [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] and is reserved for future use.|  
|[Name](../core/msbts-sendport-name-property-wmi.md)|Contains the name of the send port.|  
|[OutboundTransforms](../core/msbts-sendport-outboundtransforms-property-wmi.md)|Contains a string representation of the maps to apply per outbound document.|  
|[Priority](../core/msbts-sendport-priority-property-wmi.md)|Contains the priority of the send port.|  
|[PTAddress](../core/msbts-sendport-ptaddress-property-wmi.md)|Contains the URL of primary transport for the port.|  
|[PTCustomCfg](../core/msbts-sendport-ptcustomcfg-property-wmi.md)|Contains transport type data for the primary transport of the port.|  
|[PTFromTime](../core/msbts-sendport-ptfromtime-property-wmi.md)|Contains the start time of the service window of the primary transport for the port.|  
|[PTOrderedDelivery](../core/msbts-sendport-ptordereddelivery-property-wmi.md)|Determines whether the primary transport for the port supports ordered delivery.|  
|[PTRetryCount](../core/msbts-sendport-ptretrycount-property-wmi.md)|Contains the number of retries available for the primary transport of the port.|  
|[PTRetryInterval](../core/msbts-sendport-ptretryinterval-property-wmi.md)|Contains the retry interval for the primary transport of the port.|  
|[PTServiceWindowEnabled](../core/msbts-sendport-ptservicewindowenabled-property-wmi.md)|Determines whether a service window of the primary transport for the port is enabled.|  
|[PTToTime](../core/msbts-sendport-pttotime-property-wmi.md)|Contains the end time of the service window of the primary transport for the port.|  
|[PTTransportType](../core/msbts-sendport-pttransporttype-property-wmi.md)|Contains the transport type of the primary transport for the port.|  
|[ReceivePipeline](../core/msbts-sendport-receivepipeline-property-wmi.md)|Contains a name of the receive pipeline for the port.|  
|[SendPipeline](../core/msbts-sendport-sendpipeline-property-wmi.md)|Contains a name of the send pipeline for the port.|  
|SettingID (Inherited from **CIM_Setting**)|For more information about the **CIM_Setting** class, see the Windows Management Instrumentation documentation at [http://go.microsoft.com/fwlink/?LinkID=20246](http://go.microsoft.com/fwlink/?LinkID=20246).|  
|[Status](../core/msbts-sendport-status-property-wmi.md)|Displays the current status of the port.|  
|[STAddress](../core/msbts-sendport-staddress-property-wmi.md)|Contains the URL of secondary transport for the port.|  
|[STCustomCfg](../core/msbts-sendport-stcustomcfg-property-wmi.md)|Contains transport type data for the secondary transport of the port.|  
|[STFromTime](../core/msbts-sendport-stfromtime-property-wmi.md)|Contains the start time of the service window of the secondary transport for the port.|  
|[STOrderedDelivery](../core/msbts-sendport-stordereddelivery-property-wmi.md)|Determines whether the secondary transport for the port supports ordered delivery.|  
|[STRetryCount](../core/msbts-sendport-stretrycount-property-wmi.md)|Contains the number of retries available for the secondary transport of the port.|  
|[STRetryInterval](../core/msbts-sendport-stretryinterval-property-wmi.md)|Contains the retry interval for the secondary transport of the port.|  
|[STServiceWindowEnabled](../core/msbts-sendport-stservicewindowenabled-property-wmi.md)|Determines whether a service window of the secondary transport for the port is enabled.|  
|[STToTime](../core/msbts-sendport-sttotime-property-wmi.md)|Contains the end time of the service window of the secondary transport for the port.|  
|[STTransportType](../core/msbts-sendport-sttransporttype-property-wmi.md)|Contains the transport type of the secondary transport for the port.|  
|[Tracking](../core/msbts-sendport-tracking-property-wmi.md)|Contains the tracking configuration for the port.|  
|[MSBTS_SendPort.OrderedDelivery Property (WMI)](../core/msbts-sendport-ordereddelivery-property-wmi.md)|This property determines whether the port should send messages in an ordered manner.|  
|[StopSendingOnFailure](../core/msbts-sendport-stopsendingonfailure-property-wmi.md)|This property controls how EPM handles failures for order delivery enabled send port's primary transport.|  
|[MSBTS_SendPort.RouteFailedMessage Property (WMI)](../core/msbts-sendport-routefailedmessage-property-wmi.md)|This property controls whether failed messages have to be routed to failed message subscribers.|  
  
 **MSBTS_SendPort** defines the following methods:  
  
|Method|Description|  
|------------|-----------------|  
|[Enlist](../core/msbts-sendport-enlist-method-wmi.md)|Enlists the send port.|  
|[Start](../core/msbts-sendport-start-method-wmi.md)|Starts the send port.|  
|[Stop](../core/msbts-sendport-stop-method-wmi.md)|Stops the send port.|  
|[UnEnlist](../core/msbts-sendport-unenlist-method-wmi.md)|Unenlists the send port.|  
  
## Remarks  
 If a send port or receive location is updated using the BizTalk Explorer object model or a WMI script, the Receive Port Properties and Send Port Properties property pages in BizTalk Explorer will display an incorrect Address (URI). The Address (URI) used internally is the Address (URI) set by the script, so the script works as expected. To update the property pages to display the correct Address (URI), update the Address (URI) field in BizTalk Explorer with the new value.  
  
 This class wraps the managed **Microsoft.BizTalk.ExplorerOM.ReceivePort** class. For more information about this class, see **InboundTransforms**.  
  
## Requirements  
 **Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.  
  
 **Namespace:** Included in \root\MicrosoftBizTalkServer.