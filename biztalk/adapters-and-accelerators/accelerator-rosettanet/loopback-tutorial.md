---
title: "Loopback Tutorial | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server-2013"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "loopbacks, tutorial"
  - "loopback tutorial, about the loopback tutorial"
  - "loopback tutorial"
  - "tutorials, loopback tutorial"
ms.assetid: 0f69c1f1-4039-4949-8eed-127ceabbc3cc
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Loopback Tutorial
This tutorial contains detailed steps that describe how you can use [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] to simulate a process implementation between the home and partner organization on a single computer.  
  
 In a real production environment, your partner organization implementation resides on a remote computer. This tutorial uses the Loopback utility to create a mirror trading agreement to simulate the trading partner on the same computer. Using a single computer loop-back scenario works for development and test purposes. It is recommended that you do not to use the Loopback utility in a production environment.  
  
 This loopback scenario does not support signing messages, and thus does not support non-repudiation.  
  
 This scenario supports encryption of messages if you have a certification authority configured, and you have a private key for encryption available for test purposes.  
  
 In this tutorial, you create a home organization, a partner organization, a trade agreement, use the Loopback utility to create a mirror agreement, and then run a sample process to verify the loop-back scenario.  
  
## In This Section  
  
-   [Preparing for the Tutorial](../../adapters-and-accelerators/accelerator-rosettanet/preparing-for-the-tutorial.md)  
  
-   [Step 1: Create the Home Organization](../../adapters-and-accelerators/accelerator-rosettanet/step-1-create-the-home-organization.md)  
  
-   [Step 2: Create the Partner Organization](../../adapters-and-accelerators/accelerator-rosettanet/step-2-create-the-partner-organization.md)  
  
-   [Step 3: Edit the Partner Interface Process](../../adapters-and-accelerators/accelerator-rosettanet/step-3-edit-the-partner-interface-process.md)  
  
-   [Step 4: Create a Trade Agreement](../../adapters-and-accelerators/accelerator-rosettanet/step-4-create-a-trade-agreement.md)  
  
-   [Step 5: Create a Mirror Agreement](../../adapters-and-accelerators/accelerator-rosettanet/step-5-create-a-mirror-agreement.md)  
  
-   [Step 6: Start Orchestrations](../../adapters-and-accelerators/accelerator-rosettanet/step-6-start-orchestrations.md)  
  
-   [Step 7: Create a Sample LOB Message](../../adapters-and-accelerators/accelerator-rosettanet/step-7-create-a-sample-lob-message.md)  
  
-   [Step 8: View Messages in the BTARN Databases](../../adapters-and-accelerators/accelerator-rosettanet/step-8-view-messages-in-the-btarn-databases.md)