---
description: "Learn more about: Enlisted Party (Enlisted Parties Node)"
title: "Enlisted Party (Enlisted Parties Node)"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Enlisted Party (Enlisted Parties Node)
The Enlisted Party node of a binding file contains specific information about an enlisted party associated with a role that is exported with the binding file.  
  
## Nodes in the Enlisted Party node  
 The following table lists the properties that can be set for this node of a binding file:  
  
|**Name**|**Node Type**|**Data Type**|**Description**|**Restrictions**|**Comments**|  
|--------------|-------------------|-------------------|---------------------|----------------------|------------------|  
|Name|Attribute|xs:string|Specifies the name of the enlisted party|Not required|Default value: empty|  
|[Mappings](../core/mappings-enlisted-party-node.md)|Record|ArrayOfEnlistedPartyMapping (ComplexType)|Container node for the mappings between party ports and role port type operations.|Not required|Default value: none|
