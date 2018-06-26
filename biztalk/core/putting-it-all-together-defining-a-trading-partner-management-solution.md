---
title: "Putting it all Together: Defining a Trading Partner Management Solution | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4219312a-c4b5-45f3-b77b-d5cc4f1a1ca4
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Putting it all Together: Defining a Trading Partner Management Solution
Now that we have understood about the different types of components in building a TPM solution, let us understand the flow of a typical TPM solution and how the different building blocks work together. This section also lists some best practices for modeling a TPM solution.  
  
 A typical flow for creating a TPM solution would include the following:  
  
1. Create partners representing all the organizations involved in a business trade. For example, if there are two business organizations involved in a business trade, you must create a trading partner for each of them. For instructions on how to create trading partners, see [Configuring General Party Properties](../core/configuring-general-party-properties.md) or [Configuring General Party Properties (AS2)](../core/configuring-general-party-properties-as2.md)  
  
2. For each business division within an organization, create a profile within the partner representing the business division. For example, if an organization has “Purchase” and “Supplies” business divisions, each of these divisions must be represented as a business profile in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Also, you must create the business profiles not just for the partner representing your organization but also the partner with which you trade. For instructions on how to create business profiles, see [Configuring Business Profile Properties](../core/configuring-business-profile-properties.md).  
  
3. For each business profile, define the B2B protocol settings that include the message encoding setting and the message protocol settings. These settings define how the B2B messages are encoded and transported between two business profiles.  
  
   > [!NOTE]
   >  Specifying protocol settings is optional at this stage. You can directly add the protocol settings as part of the trading partner agreement.  
  
4. Create Trading Partner Agreements (TPA) between the business profiles that define the encoding and/or messaging protocols the two business profiles agree to use while exchanging messages. For instructions on how to create agreements, see [Configuring X12-Specific Agreement Properties](../core/configuring-x12-specific-agreement-properties.md), [Configuring EDIFACT-Specific Agreement Properties](../core/configuring-edifact-specific-agreement-properties.md), or [Configuring AS2 Agreement Properties](../core/configuring-as2-agreement-properties.md).  
  
   By performing the above set of tasks you would have created TPM solution to exchange B2B messages with your trading partner.  
  
## Where do I Start?  
 You can start by going through the following sections:  
  
-   X12-specific tutorial at [Tutorial 2: EDI Interface Developer Tutorial](../core/tutorial-2-edi-interface-developer-tutorial.md).  
  
-   AS2-specific tutorial at [Tutorial 3: AS2 Tutorial](../core/tutorial-3-as2-tutorial.md).  
  
-   X12- and EDIFACT-specific walkthroughs under [Developing and Configuring BizTalk Server EDI Solutions](../core/developing-and-configuring-biztalk-server-edi-solutions.md).  
  
-   AS2-specific walkthroughs under [Developing and Configuring BizTalk Server AS2 Solutions](../core/developing-and-configuring-biztalk-server-as2-solutions.md).  
  
-   Create parties, profiles, and agreements for X12 and EDIFACT messaging by following instructions at [Configuring EDI Properties](../core/configuring-edi-properties.md).  
  
-   Create parties, profiles, and agreements for AS2 messaging by following instructions at [Configuring AS2 Properties](../core/configuring-as2-properties.md).  
  
## See Also  
 [Building Blocks of a Trading Partner Management Solution](../core/building-blocks-of-a-trading-partner-management-solution.md)