---
description: "Learn more about: Mapping (Mappings Node)"
title: "Mapping (Mappings Node)"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: concept-article
---
# Mapping (Mappings Node)
The Mapping node of a binding file describes the mapping between a party port and role port type operation for the enlisted party.  
  
## Nodes in the Mapping node  
 The following table lists the properties that can be set for this node of a binding file:  
  
|**Name**|**Node Type**|**Data Type**|**Description**|**Restrictions**|**Comments**|  
|--------------|-------------------|-------------------|---------------------|----------------------|------------------|  
|PortTypeName|Attribute|xs:string|Specifies the name of the port type.|Not required|Default value: empty|  
|OperationName|Attribute|xs:string|Specifies the operation belonging to this port type.|Not required|Default value: empty|  
|[SendPortRef](../core/sendportref-mapping-node.md)|Record|SendPortRef (ComplexType)|Container node for the list of send ports associated with a mapping.|Not required|Default value: none|
