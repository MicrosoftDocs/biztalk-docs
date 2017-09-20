---
title: "SendHandler (PrimaryTransport Node) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "SendHandler node [binding file]"
ms.assetid: c0b200ee-ecbc-4708-a2c8-c37cd6cd0060
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# SendHandler (PrimaryTransport Node)
The SendHandler node of the PrimaryTransport node of a binding file contains specific information about the send handler associated with a transport that is exported with the binding file.  
  
## Nodes in the SendHandler node  
 The following table lists the properties that can be set for this node of a binding file:  
  
|**Name**|**Node Type**|**Data Type**|**Description**|**Restrictions**|**Comments**|  
|--------------|-------------------|-------------------|---------------------|----------------------|------------------|  
|Name|Attribute|xs:string|Specifies the name of the send handler associated with the transport.|Not required|Default value: empty|  
|HostTrusted|Attribute|xs:boolean|Specifies whether the host associated with the send handler is trusted.|Required|Default value: none<br /><br /> Set to **true** if host is trusted, otherwise set to **false**.|  
|[TransportType](../core/transporttype.md)|Record|ProtocolType (ComplexType)|Specifies the transport type, which is also the name of the adapter used with this send handler.|Required|Default value: none|