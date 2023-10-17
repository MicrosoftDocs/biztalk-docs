---
description: "Learn more about: Ports (Service Node)"
title: "Ports (Service Node) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Ports node [binding file]"
ms.assetid: 498d4310-4e9e-4e74-bc3d-5cbf1319c4ff
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Ports (Service Node)
The Ports node of a binding file is the parent node for all of the Port nodes which contain specific information about ports bound to a service that is exported with the binding file.  
  
## Node in the Ports node  
 The following table lists the properties that can be set for this node of a binding file:  
  
|**Name**|**Node Type**|**Data Type**|**Description**|**Restrictions**|**Comments**|  
|--------------|-------------------|-------------------|---------------------|----------------------|------------------|  
|[Port](../core/port-ports-node.md)|Record|ServicePortRef (ComplexType)|Specifies information about a port that is bound to a service that is exported with the binding file.|Not required|Default value: none|
