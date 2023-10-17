---
description: "Learn more about: How to Use the Role Link Wizard"
title: "How to Use the Role Link Wizard | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "links [roles]"
  - "Role Link Wizard [Orchestration Designer]"
  - "roles, links"
  - "Orchestration Designer, Role Link Wizard"
  - "role links, Role Link Wizard [Orchestration Designer]"
  - "links [roles], about links"
ms.assetid: ddc33d87-c08d-4193-9483-4644ef302853
caps.latest.revision: 11
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Use the Role Link Wizard
The Role Link Wizard enables you to create a new role link or modify an existing one. You can use it to set or view the name, type, and access restriction of the role link, as well as the implements role and the uses role that compose the role link type. To understand how role links work, see [Using Role Links in Orchestrations](../core/using-role-links-in-orchestrations.md).  
  
 **Role link name**: The role link name is filled in for you and is either the current name of an existing role link that you are configuring, or an automatically generated name if you are creating a new role link. In either case you can modify the name.  
  
 **Role link type**: You can select an existing role link type, or create a new one. Whether you are configuring a new or existing role link type, you can specify how your orchestration participates in the service.  
  
> [!NOTE]
>  We recommend that you create the role link type and associated port type prior to create the role link so that you can use an existing role link type for defining your role link. For more information, see [How to Create Role Links in Orchestrations](../core/how-to-create-role-links-in-orchestrations.md).  
  
 **Role link usage**: If you create a new role link type, both the implements and uses roles are automatically created for you. You can select the role that reflects how your orchestration participates in the service. After you have completed the steps in the wizard, you can rename the role identifiers or remove a role to better match your implementation. A role link type must contain one of either role type or one of each role type. When you click **OK**, unconfigured roles are created corresponding to each name. You can also select port types for the roles in the Types window.  
  
> [!NOTE]
>  If you invoke the Port Configuration Wizard to create a port type for your role link type, and want to select a previously defined port type, ensure that the access restrictions of the port type do not conflict with the access restrictions of the role link type.  
  
## See Also  
 [Using Role Links in Orchestrations](../core/using-role-links-in-orchestrations.md)
