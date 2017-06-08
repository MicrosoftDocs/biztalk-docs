---
title: "Preparing for the Private Process Tutorial | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server-2013"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "private process tutorial, pre-requisites"
ms.assetid: 89631ce3-f5af-4d30-b22f-6d20f595295f
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Preparing for the Private Process Tutorial
Before you start this tutorial, you must do the following:  
  
-   Perform a full installation of [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)] and [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] on two computers. For more information, see installation instructions.  
  
    > [!IMPORTANT]
    >  You must make sure that you perform the additional configuration for [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]. This includes adding the [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] virtual directories (including btarnhttpreceive) to the Microsoft Windows® SharePoint™ Services managed path exclusion list and starting the [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] orchestrations. For more information, see "Additional Configuration of Microsoft BizTalk Accelerator for RosettaNet" of the installation guide.  
  
-   This tutorial simulates a real-world scenario by using two computers instead of a single computer with a loop-back agreement. Whenever this tutorial uses computer names, it uses a placeholder as the computer name. You have to replace that placeholder with the actual computer name you chose. For example, if the computer that is running your Contoso solution is named **Contoso**, replace any occurrences in the tutorial of \\\\<contoso**_***computer*> with that computer name.  
  
 This tutorial promotes secure communication through certificates between Contoso and Fabrikam. You must generate any certificates you require and install them on the respective computers.  
  
## In This Section  
  
-   [Restoring the Contoso Database](../../adapters-and-accelerators/accelerator-rosettanet/restoring-the-contoso-database.md)  
  
-   [Generating and Enabling Certificates](../../adapters-and-accelerators/accelerator-rosettanet/generating-and-enabling-certificates.md)