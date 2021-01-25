---
description: "Learn more about: ModuleRef (ModuleRefCollection Node)"
title: "ModuleRef (ModuleRefCollection Node) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ModuleRef node [binding file]"
ms.assetid: 61787779-33bd-499a-a5c1-c1e0bd306b48
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# ModuleRef (ModuleRefCollection Node)
The ModuleRef node of a binding file contains specific information about a .NET assembly that was exported with the binding file. A ModuleRef node can include but is not limited to descriptions of assemblies that contain custom code, schemas, and orchestrations.  
  
## Nodes in the ModuleRef node  
 The following table lists the properties that can be set for this node of a binding file:  
  
|**Name**|**Node Type**|**Data Type**|**Description**|**Restrictions**|**Comments**|  
|--------------|-------------------|-------------------|---------------------|----------------------|------------------|  
|[Services](../core/services-moduleref-node.md)|Record|ArrayOfServiceRef (ComplexType)|Container node for services associated with this .NET assembly.|Not required|Default value: none|  
|[TrackedSchemas (ModuleRef Node)](../core/trackedschemas-moduleref-node.md)|Record|ArrayOfSchema (ComplexType)|Container node for schemas associated with this .NET assembly|Not required|Default value: none|
