---
description: "Learn more about: ModuleRefCollection Node"
title: "ModuleRefCollection Node | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ModuleRefCollection node [binding file]"
ms.assetid: fa8593bf-6548-4615-9f98-1e0eadde9aa4
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# ModuleRefCollection Node
The ModuleRefCollection section of a binding file is the parent node for all of the ModuleRef nodes which contain specific information about .NET assemblies exported with the binding file.  
  
## Entries in the ModuleRefCollection section  
 The following table lists the properties that can be set for the nodes in this section of a binding file:  
  
|**Name**|**Node Type**|**Data Type**|**Description**|**Restrictions**|**Comments**|  
|--------------|-------------------|-------------------|---------------------|----------------------|------------------|  
|[ModuleRef](../core/moduleref-modulerefcollection-node.md)|Record|ModuleRef (ComplexType)|Container node for a .NET assembly module exported with the binding file.|Not required|Default value: None|
