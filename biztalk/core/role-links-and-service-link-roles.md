---
description: "Learn more about: Role Links and Service Link Roles"
title: "Role Links and Service Link Roles | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "deleting, orchestrations"
  - "service link roles"
  - "role links"
  - "roles, orchestrations"
  - "roles"
  - "roles, about roles"
  - "service link roles, about service link roles"
  - "orchestrations, roles"
  - "role links, about role links"
  - "orchestrations, deleting"
ms.assetid: 23b4ca34-a1a5-44d4-a50d-661277681c72
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Role Links and Service Link Roles
A *role* is a collection of port types that either uses a service or implements a service. A role represents the type of interaction that a party can have with one or many orchestrations. Roles provide flexibility and ease of management as the number of parties increase. For example, an orchestration might use the role of a Shipper. The Shipper would have one or two parties associated with it. When the orchestration decides which shipping company to use to ship an item, it compares the prices of the parties in the Shipper role.  
  
 A *role link type* is a property that characterizes the relationship between two services or orchestrations. It defines the part played by each of the services in the relationship and specifies the port types provided by each role.  
  
 A party, or organizational unit, represents an entity outside of BizTalk Server that interacts with an orchestration. In BizTalk Server, each organization with which you exchange messages is represented by a party. You can define how the party interacts by enlisting it in a role.  
  
 You can deploy or remove a role link type when it is associated with an orchestration.  
  
## Orchestrations and Roles  
 When you deploy an orchestration that uses a role link type, the Configuration database saves the role. Because a role can be used by more than one orchestration, the Management database saves only one copy of the role link type.  
  
 If your BizTalk project contains two role link types in separate orchestration (.odx) files that have the same name and namespace, your BizTalk project does not compile.  
  
### Orchestration Removals that use Roles  
 Because a role link type can be used by more than one orchestration, when you undeploy an assembly that contains an orchestration that uses a role, the Management database removes the role only if no other orchestrations are using the role.  
  
 Additionally, the Management database removes a role only if there are no parties enlisted with it. Just as you cannot overwrite a role that has parties enlisted with it, you cannot remove a role that has parties enlisted with it.  
  
## See Also  
 [Using Role Links in Orchestrations](../core/using-role-links-in-orchestrations.md)   
 [Artifacts](../core/artifacts.md)
