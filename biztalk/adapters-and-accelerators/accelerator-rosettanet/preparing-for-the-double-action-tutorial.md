---
title: "Preparing for the Double Action Tutorial | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server-2013"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "double action tutorial, pre-requisites"
ms.assetid: 1ce8a122-cd16-450a-84bd-bb6beee7af40
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Preparing for the Double Action Tutorial
Before you start this tutorial, you must do the following:  
  
-   Perform a full installation of [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)] and [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] on two computers. For more information, see the installation instructions.  
  
    > [!IMPORTANT]
    >  You must make sure that the additional configuration for [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] has been performed. This includes starting the BTARN orchestrations. For more information, see Additional Configuration of Microsoft BizTalk Accelerator for RosettaNet.  
  
-   This tutorial simulates a real-world scenario by using two computers instead of a single computer with a loopback agreement. Whenever this tutorial uses computer names, it uses a placeholder. You have to replace that placeholder with the actual computer name you chose. For example, if the computer that is running your Contoso solution is named **Contoso**, replace any occurrences in the tutorial of \\\\<contoso**_***computer*> with that computer name.  
  
-   This tutorial promotes secure communication through certificates between Contoso and Fabrikam. You must generate any certificates you require and install them on their respective computers.  
  
## In This Section  
  
-   [Step 1: Creating a Certification Authority](../../adapters-and-accelerators/accelerator-rosettanet/step-1-creating-a-certification-authority.md)  
  
-   [Step 2: Creating Public and Private Certificates](../../adapters-and-accelerators/accelerator-rosettanet/step-2-creating-public-and-private-certificates.md)  
  
-   [Step 3: Importing Public and Private Certificates](../../adapters-and-accelerators/accelerator-rosettanet/step-3-importing-public-and-private-certificates.md)  
  
-   [Step 4: Enabling Secure Sockets Layer in IIS](../../adapters-and-accelerators/accelerator-rosettanet/step-4-enabling-secure-sockets-layer-in-iis.md)