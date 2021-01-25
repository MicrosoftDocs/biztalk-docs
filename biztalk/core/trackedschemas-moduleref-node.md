---
description: "Learn more about: TrackedSchemas (ModuleRef Node)"
title: "TrackedSchemas (ModuleRef Node) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "TrackedSchemas node [binding file]"
ms.assetid: a2b99fbf-df6b-4a94-97b8-ac5eb819604f
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# TrackedSchemas (ModuleRef Node)
The TrackedSchemas node of a binding file is the parent node for all of the Schema nodes which describe the schemas bound to the service that is exported with the binding file.  
  
## Nodes in the TrackedSchemas node  
 The following table lists the properties that can be set for this node of a binding file:  
  
|**Name**|**Node Type**|**Data Type**|**Description**|**Restrictions**|**Comments**|  
|--------------|-------------------|-------------------|---------------------|----------------------|------------------|  
|[Schema](../core/schema-trackedschemas-node.md)|Record|ArrayOfSchema (ComplexType)|Container node for the schemas that are bound to the service that is exported with the binding file.|Not required|Default value: none|
