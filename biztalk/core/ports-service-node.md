---
description: "Learn more about: Ports (Service Node)"
title: "Ports (Service Node)"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Ports (Service Node)
The Ports node of a binding file is the parent node for all of the Port nodes which contain specific information about ports bound to a service that is exported with the binding file.  
  
## Node in the Ports node  
 The following table lists the properties that can be set for this node of a binding file:  
  
|**Name**|**Node Type**|**Data Type**|**Description**|**Restrictions**|**Comments**|  
|--------------|-------------------|-------------------|---------------------|----------------------|------------------|  
|[Port](../core/port-ports-node.md)|Record|ServicePortRef (ComplexType)|Specifies information about a port that is bound to a service that is exported with the binding file.|Not required|Default value: none|
