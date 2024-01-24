---
description: "Learn more about: ReceiveHandler (ReceiveLocation Node)"
title: "ReceiveHandler (ReceiveLocation Node)"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# ReceiveHandler (ReceiveLocation Node)
The ReceiveHandler node of the ReceiveLocation node of a binding file contains specific information about the receive handler associated with a transport that is exported with the binding file.  
  
## Nodes in the ReceiveHandler node  
 The following table lists the properties that can be set for this node of a binding file:  
  
|**Name**|**Node Type**|**Data Type**|**Description**|**Restrictions**|**Comments**|  
|--------------|-------------------|-------------------|---------------------|----------------------|------------------|  
|Name|Attribute|xs:string|Specifies the name of the receive handler associated with the transport.|Not required|Default value: empty|  
|HostTrusted|Attribute|xs:boolean|Specifies whether the host associated with the receive handler is trusted.|Required|Default value: none<br /><br /> Set to **true** if host is trusted, otherwise set to **false**.|  
|[TransportType (ReceiveHandler Node)](../core/transporttype-receivehandler-node.md)|Record|ProtocolType (ComplexType)|Specifies the transport type, which is also the name of the adapter used with this receive handler.|Required|Default value: none|
