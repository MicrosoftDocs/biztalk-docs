---
title: "Trading Partner Agreements | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "trading partners, agreements"
  - "agreements, trading partners"
ms.assetid: 846466d2-db39-42ba-8be1-ecca83a55a02
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Trading Partner Agreements
[!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] processes message exchange with a partner by a trading partner agreement (TPA). The TPA defines the specifics of message processing and validation between the two partners. It defines how those partners implement the relevant Partner Interface Process (PIP), which specifies the message content for all implementations of a specific message type. The TPA also defines specifics of how the partners exchange messages over the Internet.  
  
## Trading Partner Agreement Contents  
 Each trading partner agreement includes the following information:  
  
- The identities of the trading partners  
  
- The public process, as defined by the RosettaNet Implementation Framework (RNIF) version—each TPA references a single public process to initiate or respond to PIP actions  
  
- The process configuration profile, the [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] implementation of the PIP  
  
- ASPX settings, including the action, signal, and synchronous URLs  
  
- Protocols for encoding and encryption  
  
- Custom properties  
  
  To create a trading partner agreement, you must use the [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] Management Console to create a process configuration. You typically base this configuration on a RosettaNet PIP, but you can also base it on a custom schema. You must also use the console to create a home organization and a partner. [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] does not support message exchange between unknown parties. After you create the configuration and the organization, you can then use the Management Console to create a partner agreement.  
  
### Process Configuration  
 These settings determine how [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] processes message content. They specify the RosettaNet PIP, and indicate how [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] will implement the PIP. To do this, they provide specific values for the behavioral settings that the PIP specifies, for example, time-out and retry values. Therefore, two different sets of partners, or the same set of partners, can implement the same PIP in two different ways.  
  
 These settings also specify the standard (RosettaNet or CIDX), and general aspects of the home organization and partner roles. You can also create a process configuration for non-RosettaNet content. To do this, you must create a schema for that content, and then create the configuration based on that schema. For non-RosettaNet content, you must enter values for the Message standard, Standard version, and Payload Binding ID settings on the **General** tab in the **Process Configuration Settings** dialog box. You can only transport non-RosettaNet content by using RNIF 2.0.  
  
 For more information about setting these properties, see [How to Create or Edit a Process Configuration](../../adapters-and-accelerators/accelerator-rosettanet/how-to-create-or-edit-a-process-configuration.md).  
  
### Home Organization  
 These settings define the home organization that will initiate messages. The settings include a Global Business Identifier (GBI), which is the DUNS number that is the unique identifier of the business, and contact information that is required in some transactions. For more information about setting these properties, see [Creating or Editing a Home Organization](../../adapters-and-accelerators/accelerator-rosettanet/creating-or-editing-a-home-organization.md).  
  
### Partner Organization  
 These settings define the partner that will receive and respond to messages. [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] validates that each incoming RNIF message originated from a valid party who has an agreement with the home organization. If not, [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] will fail to authenticate and not process the message. For more information about setting these properties, see [Creating or Editing a Partner](../../adapters-and-accelerators/accelerator-rosettanet/creating-or-editing-a-partner.md).  
  
### Agreements (Trading Partner Agreement Variables)  
 The agreement specifies all aspects of the trading partner relationship. It specifies the display code of the process configuration settings, as defined in the [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] Management Console. It also specifies the RNIF version, port URLs, protocol settings (encoding and encryption), and other variables. For more information about setting these properties, see [Creating or Editing an Agreement](../../adapters-and-accelerators/accelerator-rosettanet/creating-or-editing-an-agreement.md).  
  
 For more information about the management console, see [Manage configuration, certificates, databases, and security](manage-configuration-certificates-databases-security.md). You can also gain read-only programmatic access to these settings through the classes and interfaces in the Microsoft.Solutions.BTARN.ConfigurationManager Namespace in the Developer Reference.  
  
## See Also  
 [What BizTalk Accelerator for RosettaNet Adds to BizTalk Server](../../adapters-and-accelerators/accelerator-rosettanet/what-biztalk-accelerator-for-rosettanet-adds-to-biztalk-server.md)   
 [RNIF Pipelines](../../adapters-and-accelerators/accelerator-rosettanet/rnif-pipelines.md)   
 [How to Create or Edit a Process Configuration](../../adapters-and-accelerators/accelerator-rosettanet/how-to-create-or-edit-a-process-configuration.md)   
 [Creating or Editing a Home Organization](../../adapters-and-accelerators/accelerator-rosettanet/creating-or-editing-a-home-organization.md)   
 [Creating or Editing a Partner](../../adapters-and-accelerators/accelerator-rosettanet/creating-or-editing-a-partner.md)   
 [Creating or Editing an Agreement](../../adapters-and-accelerators/accelerator-rosettanet/creating-or-editing-an-agreement.md)