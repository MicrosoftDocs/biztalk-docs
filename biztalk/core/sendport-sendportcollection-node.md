---
title: "SendPort (SendPortCollection Node) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "SendPort node [binding file]"
ms.assetid: 5cf7a6f9-9240-48b9-b196-8838afd4f41e
caps.latest.revision: 15
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# SendPort (SendPortCollection Node)
The SendPort node of a binding file contains specific information about a send port that is exported with the binding file.  
  
## Nodes in the SendPort node  
 The following table lists the properties that can be set for this node of a binding file:  
  
|**Name**|**Node Type**|**Data Type**|**Description**|**Restrictions**|**Comments**|  
|--------------|-------------------|-------------------|---------------------|----------------------|------------------|  
|Name|Attribute|xs:string|Specifies the name of the send port.|Not required|Default value: empty|  
|IsStatic|Attribute|xs:boolean|Specifies whether the send port is static or dynamic.|Required|Default value: none|  
|IsTwoWay|Attribute|xs:boolean|Specifies whether the send port is one way or is solicit-response (two way).|Required|Default value: none<br /><br /> Possible values are documented in [MSBTS_SendPort.IsTwoWay Property (WMI)](../core/msbts-sendport-istwoway-property-wmi.md)|  
|BindingOption|Attribute|xs:int|Specifies the type of binding for the orchestration port.|Required|Default value: none<br /><br /> Possible values are documented in the [Microsoft.BizTalk.ExplorerOM.BindingType](http://msdn.microsoft.com/library/microsoft.biztalk.explorerom.bindingtype.aspx) enumeration.|  
|Description|Element|xs:string|Specifies a description for the send port.|Required|Default value: empty|  
|[TransmitPipeline (SendPort Node)](../core/transmitpipeline-sendport-node.md)|Record|PipelineRef (ComplexType)|Specifies the send pipeline associated with the send port.|Not required|Default value: none|  
|SendPipelineData|Element|xs:string|Specifies the custom configuration specific to this instance of the usage of the pipeline.|Not required|Default value: empty.|  
|[PrimaryTransport](../core/primarytransport-sendport-node.md)|Record|TransportInfo (ComplexType)|Specifies information about the primary transport that the send port is configured to use.|Not required|Default value: none|  
|[SecondaryTransport](../core/secondarytransport-sendport-node.md)|Record|TransportInfo (ComplexType)|Specifies information about the secondary transport that the send port is configured to use.|Not required|Default value: none|  
|[EncryptionCert](../core/encryptioncert-sendport-node.md)|Record|CertificateInfo (ComplexType)|Specifies information about the encryption certificate used with the send port.|Not required|Default value: none|  
|[ReceivePipeline](../core/receivepipeline-sendport-node.md)|Record|PipelineRef (ComplexType)|Specifies information about any receive pipelines used with the send port.|Not required|Default value: none|  
|ReceivePipelineData|Element|xs:string|Specifies the custom configuration specific to this instance of the usage of the pipeline.|Required|Default value: empty|  
|Tracking|Element|xs:int|Specifies the level of document tracking for the send port|Required|Default value: none<br /><br /> Possible values are documented in the [Microsoft.BizTalk.ExplorerOM.TrackingTypes](http://msdn.microsoft.com/library/microsoft.biztalk.explorerom.trackingtypes.aspx) enumeration.|  
|Filter|Element|xs:string|Specifies the name of the optional filter expression used on this send port.|Required|Default value: empty<br /><br /> Possible values are documented in [MSBTS_SendPort.Filter Property (WMI)](../core/msbts-sendport-filter-property-wmi.md)|  
|[Transforms (SendPort Node)](../core/transforms-sendport-node.md)|Record|ArrayOfTransform (ComplexType)|Specifies the collection of outbound transforms of a one way send port.|Not required|Default value: none|  
|[InboundTransforms](../core/inboundtransforms-sendport-node.md)|Record|ArrayOfTransform (ComplexType)|Specifies the collection of inbound transforms of a two-way send port.|Not required|Default value: none|  
|OrderedDelivery|Element|xs:boolean|Specifies whether or not the send port orders the delivery of messages.|Required|Default value: none<br /><br /> Possible values are documented in [MSBTS_SendPort.OrderedDelivery Property (WMI)](../core/msbts-sendport-ordereddelivery-property-wmi.md)|  
|Priority|Element|xs:int|Specifies the priority of the send port.|Required|Default value: 5<br /><br /> Possible values are documented in [MSBTS_SendPort.Priority Property (WMI)](../core/msbts-sendport-priority-property-wmi.md)|  
|StopSendingOnFailure|Element|xs:boolean|Specifies whether or not the send port stops sending messages on a failure.|Required|Default value: none<br /><br /> Possible values are documented in [MSBTS_SendPort.StopSendingOnFailure Property (WMI)](../core/msbts-sendport-stopsendingonfailure-property-wmi.md)|  
|RouteFailedMessage|Element|xs:boolean|Specifies whether or not failed messages are routed to failed message subscribers.|Required|Default value: none<br /><br /> Possible values are documented in [MSBTS_SendPort.RouteFailedMessage Property (WMI)](../core/msbts-sendport-routefailedmessage-property-wmi.md)|  
|ApplicationName|Element|xs:string|Specifies the name of the application associated with the send port.|Required|Default value: empty<br /><br /> Possible values are documented in [ISSOMapping.ApplicationName Property](../core/issomapping-applicationname-property.md).|