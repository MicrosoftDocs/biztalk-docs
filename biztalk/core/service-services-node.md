---
title: "Service (Services Node) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Service node [binding file]"
ms.assetid: 19e977b4-55bd-453f-9053-5590b9553b07
caps.latest.revision: 11
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Service (Services Node)
The Service node of a binding file contains information about a service exported with the binding file. The service node also contains nodes that describe the ports and roles associated with the service and a node that describes the host associated with the service.  
  
## Nodes in the Service node  
 The following table lists the properties that can be set for this node of a binding file:  
  
|**Name**|**Node Type**|**Data Type**|**Description**|**Restrictions**|**Comments**|  
|--------------|-------------------|-------------------|---------------------|----------------------|------------------|  
|Name|Attribute|xs:string|Specifies the name of the service.|Required|Default value: empty|  
|State|Attribute|ServiceRefState (SimpleType)|Specifies the state of the service.|Required|Default value: Default<br /><br /> Possible values include:<br /><br /> -   Default<br />-   Unenlisted<br />-   Enlisted<br />-   Started|  
|TrackingOption|Attribute|OrchestrationTrackingTypes (SimpleType)|Specifies the message tracking options for the service.|Required|Default value: none<br /><br /> Possible values include those available in the [Microsoft.BizTalk.ExplorerOM.OrchestrationTrackingTypes](http://msdn.microsoft.com/library/microsoft.biztalk.explorerom.orchestrationtrackingtypes.aspx) enumeration.|  
|Description|Attribute|xs:string|Specifies a description for the service.|Not required|Default value: empty|  
|[Ports](../core/ports-service-node.md)|Record|ArrayOfServicePortRef (ComplexType)|Container node for the ports bound to the service.|Not required|Default value: none|  
|[Roles](../core/roles-service-node.md)|Record|ArrayOfRoleRef (ComplexType)|Container node for the roles bound to the service.|Not required|Default value: none|  
|[Host](../core/host-service-node.md)|Record|HostRef (ComplexType)|Container node for the host bound to the service.|Required|Default value: none|