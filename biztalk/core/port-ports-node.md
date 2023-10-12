---
description: "Learn more about: Port (Ports Node)"
title: "Port (Ports Node)"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
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
|Modifier|Attribute|xs:int|Specifies the type modifier for the port.|Required|Default value: none<br /><br /> Possible values include those available in the [Microsoft.BizTalk.ExplorerOM.PortModifier](/dotnet/api/microsoft.biztalk.explorerom.portmodifier/) enumeration.|  
|BindingOption|Attribute|xs:int|Defines the type of binding for the port.|Required|Default value: none<br /><br /> Possible values include those available in the [Microsoft.BizTalk.ExplorerOM.BindingType](/dotnet/api/microsoft.biztalk.explorerom.bindingtype) enumeration.|  
|[SendPortRef](../core/sendportref-port-node.md)|Record|SendPortRef (ComplexType)|Container node for send ports that is referenced by a service.|Not required|Default value: empty|  
|[DistributionListRef](../core/distributionlistref-port-node.md)|Record|DistributionListRef (ComplexType)|Container node for distribution lists referenced by a service.|Not required|Default value: empty|  
|[ReceivePortRef](../core/receiveportref-port-node.md)|Record|ReceivePortRef (ComplexType)|Container node for receive ports referenced by a service.|Not required|Default value: empty|
