---
title: "Port (Ports Node) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Port node [binding file]"
ms.assetid: 6c9a3e5f-0b3c-40f8-9a8d-5a83bd559021
caps.latest.revision: 12
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Port (Ports Node)
The port node of a binding file contains specific information about a port or distribution list that is bound to a service that is exported with the binding file.  
  
> [!NOTE]
>  A distribution list is referred to as a send port group in the BizTalk Server Administration Console.  
  
## Nodes in the Port node  
 The following table lists the properties that can be set for this node of a binding file:  
  
|**Name**|**Node Type**|**Data Type**|**Description**|**Restrictions**|**Comments**|  
|--------------|-------------------|-------------------|---------------------|----------------------|------------------|  
|Name|Attribute|xs:string|Specifies the name of the port.|Not required|Default value: empty|  
|Modifier|Attribute|xs:int|Specifies the type modifier for the port.|Required|Default value: none<br /><br /> Possible values include those available in the [Microsoft.BizTalk.ExplorerOM.PortModifier](http://msdn.microsoft.com/library/microsoft.biztalk.explorerom.portmodifier.aspx) enumeration.|  
|BindingOption|Attribute|xs:int|Defines the type of binding for the port.|Required|Default value: none<br /><br /> Possible values include those available in the [Microsoft.BizTalk.ExplorerOM.BindingType](http://msdn.microsoft.com/library/microsoft.biztalk.explorerom.bindingtype.aspx) enumeration.|  
|[SendPortRef](../core/sendportref-port-node.md)|Record|SendPortRef (ComplexType)|Container node for send ports that is referenced by a service.|Not required|Default value: empty|  
|[DistributionListRef](../core/distributionlistref-port-node.md)|Record|DistributionListRef (ComplexType)|Container node for distribution lists referenced by a service.|Not required|Default value: empty|  
|[ReceivePortRef](../core/receiveportref-port-node.md)|Record|ReceivePortRef (ComplexType)|Container node for receive ports referenced by a service.|Not required|Default value: empty|