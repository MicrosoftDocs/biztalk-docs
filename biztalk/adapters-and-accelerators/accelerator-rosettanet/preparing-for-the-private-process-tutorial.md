---
title: "Prerequisites for the RosettaNet Private Process tutorial in BizTalk Server | Microsoft Docs"
description: Prerequisites to step through the Private Process tutorial for the RosettaNet accelerator (BTARN) in BizTalk Server
caps.latest.revision: 7
author: "MandiOhlinger"
manager: "anneta"

ms.custom: ""
ms.date: "08/09/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 89631ce3-f5af-4d30-b22f-6d20f595295f
ms.author: "mandia"
---

# Prepare for the Private Process tutorial

## Prerequisites
Before starting the tutorial:
  
- Do a full installation of BizTalk Server and [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] on two computers. For more information, see [Install and configure](install-configure-biztalk-accelerator-for-rosettanet.md).  
  
  > [!IMPORTANT]
  >  Be sure that you fully configure the RosettaNet accelerator, including starting the BTARN orchestrations. See [Install and configure](install-configure-biztalk-accelerator-for-rosettanet.md). You may also have to add the [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] virtual directories (including btarnhttpreceive) to the Microsoft Windows® SharePoint™ Services managed path exclusion list. 
  
- This tutorial simulates a real-world scenario by using two computers instead of a single computer with a loop-back agreement. Whenever this tutorial uses computer names, it uses a placeholder as the computer name. Replace that placeholder with the actual computer name you chose. For example, if the computer that is running your Contoso solution is named **Contoso**, replace any occurrences in the tutorial of \\\\<contoso<strong>_</strong>*computer*\> with that computer name.  
  
  This tutorial promotes secure communication through certificates between Contoso and Fabrikam. You must generate any certificates you require, and install them on the respective computers.  
  
## Next steps
  
-   [Restoring the Contoso Database](../../adapters-and-accelerators/accelerator-rosettanet/restoring-the-contoso-database.md)  
  
-   [Generating and Enabling Certificates](../../adapters-and-accelerators/accelerator-rosettanet/generating-and-enabling-certificates.md)