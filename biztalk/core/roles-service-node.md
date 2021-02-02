---
description: "Learn more about: Roles (Service Node)"
title: "Roles (Service Node) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Roles node [binding file]"
ms.assetid: 847755c9-1697-41a0-b870-f9e795a1a2a6
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Roles (Service Node)
The Roles node of a binding file is the parent node for all of the Role nodes which provide specific information about each role bound to a service that is exported with the binding file.  
  
## Nodes in the Roles node  
 The following table lists the properties that can be set for this node of a binding file:  
  
|**Name**|**Node Type**|**Data Type**|**Description**|**Restrictions**|**Comments**|  
|--------------|-------------------|-------------------|---------------------|----------------------|------------------|  
|[Role](../core/role-roles-node.md)|Record|RoleRef (ComplexType)|Specifies information about a role that is bound to a service that is exported with the binding file.|Not required|Default value: none|
