---
title: "Role (Roles Node) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Role node [binding file]"
ms.assetid: dfe2a579-7090-4d85-87e5-d627598c4ee8
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Role (Roles Node)
The Role node of the Roles node of a binding file specifies information about a role that is bound to a service that is exported with the binding file.  
  
## Nodes in the Role node  
 The following table lists the properties that can be set for this node of a binding file:  
  
|**Name**|**Node Type**|**Data Type**|**Description**|**Restrictions**|**Comments**|  
|--------------|-------------------|-------------------|---------------------|----------------------|------------------|  
|Name|Attribute|xs:string|Specifies the name of the role.|Not required|Default value: empty|  
|RoleLinkTypeName|Attribute|xs:string|Specifies the name of the role link type associated with the role|Not required|Default value: empty|  
|RoleType|Attribute|RoleRefType (SimpleType)|Specifies the role type associated with the role.|Required|Default value: none<br /><br /> Possible values include:<br /><br /> -   Unknown<br />-   Implements<br />-   Uses|  
|[Enlisted Parties](../core/enlisted-parties-role-node.md)|Record|ArrayOfEnlistedParty (ComplexType)|Container node for the enlisted parties bound to this role.|Not required|Default value: none|