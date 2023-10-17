---
description: "Learn more about: TrackedSchemas (ModuleRef Node)"
title: "TrackedSchemas (ModuleRef Node)"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# TrackedSchemas (ModuleRef Node)
The TrackedSchemas node of a binding file is the parent node for all of the Schema nodes which describe the schemas bound to the service that is exported with the binding file.  
  
## Nodes in the TrackedSchemas node  
 The following table lists the properties that can be set for this node of a binding file:  
  
|**Name**|**Node Type**|**Data Type**|**Description**|**Restrictions**|**Comments**|  
|--------------|-------------------|-------------------|---------------------|----------------------|------------------|  
|[Schema](../core/schema-trackedschemas-node.md)|Record|ArrayOfSchema (ComplexType)|Container node for the schemas that are bound to the service that is exported with the binding file.|Not required|Default value: none|
