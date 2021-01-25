---
description: "Learn more about: PrimaryTransport (SendPort Node)"
title: "PrimaryTransport (SendPort Node) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "PrimaryTransport node [binding file]"
ms.assetid: 22b68d27-f280-4272-84b8-8a50f230228a
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# PrimaryTransport (SendPort Node)
The PrimaryTransport node of the SendPort node of a binding file provides specific information about the primary transport that is bound to a send port exported with the binding file.  
  
## Nodes in the PrimaryTransport node  
 The following table lists the properties that can be set for this node of a binding file:  
  
|**Name**|**Node Type**|**Data Type**|**Description**|**Restrictions**|**Comments**|  
|--------------|-------------------|-------------------|---------------------|----------------------|------------------|  
|Address|Element|xs:string|Specifies the address (or URI) of the transport.|Not required|Default value: empty|  
|[TransportType (PrimaryTransport Node)](../core/transporttype-primarytransport-node.md)|Record|ProtocolType (ComplexType)|Specifies the transport type, which is also the name of the adapter used for this transport.|Not required|Default value: none|  
|TransportTypeData|Element|xs:string|Specifies configuration information specific to the adapter.|Not required|Default value: empty<br /><br /> See [Configuration Properties for Integrated BizTalk Adapters](../core/configuration-properties-for-integrated-biztalk-adapters.md) for adapter specific information about the properties that can be stored in this string.|  
|RetryCount|Element|xs:int|Specifies the retry count for the adapter used with the transport.|Required|Default value: none|  
|RetryInterval|Element|xs:int|Specifies the retry interval in minutes for the adapter used with the transport.|Required|Default value: none|  
|ServiceWindowEnabled|Element|xs:boolean|Specifies whether the service window is enabled for the adapter used with the transport.|Required|Default value: none<br /><br /> Set to **true** if service window is enabled, otherwise set to **false**.|  
|FromTime|Element|xs:dateTime|Specifies the start time for the service window.|Required|Default value: none|  
|ToTime|Element|xs:dateTime|Specifies the end time for the service window.|Required|Default value: none|  
|Primary|Element|xs:boolean|Specifies whether the adapter used with the transport is primary.|Required|Default value: none<br /><br /> Set to **true** if the adapter used with the transport is primary, otherwise set to **false**.|  
|OrderedDelivery|Element|xs:boolean|Specifies whether or not the adapter used with the transport should send messages in an ordered manner.|Required|Default value: none<br /><br /> Set to **true** if the transport is to send messages in order, otherwise set to **false**.|  
|DeliveryNotification|Element|xs:int|Specifies whether or not the adapter used with the transport should return a delivery notification indicating if the transmission was successful.|Required|Default value: none<br /><br /> Set to **true** for delivery notifications, otherwise set to **false**.|  
|[SendHandler](../core/sendhandler-primarytransport-node.md)|Record|SendHandlerRef (ComplexType)|Specifies the send handler for the adapter used with the transport.|Required|Default value: none|
