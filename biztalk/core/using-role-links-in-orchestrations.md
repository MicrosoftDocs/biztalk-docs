---
title: "Using Role Links in Orchestrations | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "role links"
  - "roles, links"
  - "roles"
  - "roles, about roles"
  - "role links, about role links"
  - "role links, properties"
  - "role links, initializing"
ms.assetid: 0cf85544-12c9-4541-8925-61a6e946cce0
caps.latest.revision: 20
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Using Role Links in Orchestrations
Role links are a form of abstraction for the interactions between your orchestration and your trading partners. Role links enable you to dynamically choose which trading partner to interact with based on trading partner resolution, message content, or the results of a database lookup while maintaining your overall business process intact.  
  
 For example, in a business-to-business scenario, there are multiple buyers, a single supplier, and multiple shipping agencies for the supplier. When a buyer sends a purchase order to the supplier, the supplier knows through party resolution which buyer is sending the purchase order and can apply the appropriate discount. Moreover, based on the goods ordered, the supplier determines at run time which shipping agency will be in charge of the delivery. Although each shipping agency may have its own transport protocol, the supplier can use the same business process at run time to handle all the shipping agencies and determine which agency to interact with. At a later stage, if a shipping agency updates its transport protocol—for example, from FTP to HTTP—the supplier only needs to use BizTalk Explorer or the BizTalk Server Administration console to update the send port associated with that particular shipping agency. The supplier does not need to change its business process, which resides in the orchestration.  
  
## Roles  
 There are two roles in an orchestration:  
  
-   An "implements" role to receive and process messages. This role is also known as the provider.  
  
-   A "uses" role to send messages. This role is also known as the consumer.  
  
## Role Links  
 A role link can include either a consumer or a provider role, or one of each. A consumer role consumes the services provided by the provider role. When you define a role link with one or both of these roles, it is assumed that the complementary role is being fulfilled by the partner with whom you are linking.  
  
 A role link has a **SourceParty** property, a **DestinationParty** property, and an initiating role. An initiating role is the role on which the first communication occurs, and which therefore initiates the role link by setting the value of the **DestinationParty** property.  
  
 If the initiating role is a consumer for sending messages, you explicitly set the **DestinationParty** property (once and only once) in your orchestration. To do so, you set the value of the **DestinationParty** in the **Expression** shape, as in the following example, where ConfirmOrder is the name of a role link, and PartnerName and OrganizationName are parameters of a party:  
  
```  
ConfirmOrder(Microsoft.XLANGs.BaseTypes.DestinationParty) = new Microsoft.XLANGs.BaseTypes.Party("PartnerName", "OrganizationName");  
```  
  
 If the initiating role is a provider for receiving messages, the **DestinationParty** property is initialized automatically by the receiver. The **DestinationParty** is set to the provider itself. The **SourceParty** property is read-only, and is supplied through a trusted pipeline component to resolve the party name based on the security identifier (SID) of the sender or on a certificate associated with the party. The host running the pipeline component must be marked as **Authentication Trusted**. You can get the value of the **SourceParty** in the **Expression** shape by using the following sample code:  
  
 `PartyName = Buyer_Supplier(Microsoft.XLANGs.BaseTypes.SourceParty);`  
  
## Role Link Types  
 A role link is an instance of a role link type, which consists of either one or two roles. When working with a role link type, consider the following:  
  
-   You can refer only once to any given port type within a single role link type.  
  
-   Because a role link type definition includes port types, the scope of a port type must encompass that of any role link type that uses it.  
  
-   When working with Business Activity Services (BAS), the structured parameter schema must be defined in the same BizTalk assembly as the role link type it is associated with. Because the schema is associated with the role link type and not with the individual roles that make up that role link type, if the parties that play the different roles share the assembly containing the role link type, both parties will see the same structured parameter schemas. If the two parties use the same role link type but must have different parameter schemas, a different assembly should be created for each party. The role link type should be duplicated in each assembly.  
  
## In This Section  
  
-   [How to Create Role Links in Orchestrations](../core/how-to-create-role-links-in-orchestrations.md)  
  
-   [How to Use the Role Link Shape](../core/how-to-use-the-role-link-shape.md)  
  
-   [How to Use the Role Link Wizard](../core/how-to-use-the-role-link-wizard.md)  
  
## See Also  
 [How to Configure the Party Resolution Pipeline Component](../core/how-to-configure-the-party-resolution-pipeline-component.md)   
 [Using Ports in Orchestrations](../core/using-ports-in-orchestrations.md)