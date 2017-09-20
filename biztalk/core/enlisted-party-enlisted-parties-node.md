---
title: "Enlisted Party (Enlisted Parties Node) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Enlisted Parties node [binding file]"
ms.assetid: 2ff7b563-17c5-48e9-b33e-62c821188448
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Enlisted Party (Enlisted Parties Node)
The Enlisted Party node of a binding file contains specific information about an enlisted party associated with a role that is exported with the binding file.  
  
## Nodes in the Enlisted Party node  
 The following table lists the properties that can be set for this node of a binding file:  
  
|**Name**|**Node Type**|**Data Type**|**Description**|**Restrictions**|**Comments**|  
|--------------|-------------------|-------------------|---------------------|----------------------|------------------|  
|Name|Attribute|xs:string|Specifies the name of the enlisted party|Not required|Default value: empty|  
|[Mappings](../core/mappings-enlisted-party-node.md)|Record|ArrayOfEnlistedPartyMapping (ComplexType)|Container node for the mappings between party ports and role port type operations.|Not required|Default value: none|