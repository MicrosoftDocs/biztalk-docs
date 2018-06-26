---
title: "Prerequisites for the RosettaNet Double Action tutorial in BizTalk Server | Microsoft Docs"
description: Prerequisites to step through the Double Action tutorial for the RosettaNet accelerator (BTARN) in BizTalk Server
ms.custom: ""
ms.date: "08/09/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1ce8a122-cd16-450a-84bd-bb6beee7af40
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Prepare for the Double Action tutorial

## Prerequisites
Before starting the tutorial:
  
- Do a full installation of BizTalk Server and [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] on two computers. For more information, see [Install and configure](install-configure-biztalk-accelerator-for-rosettanet.md).  
  
  > [!IMPORTANT]
  >  Be sure that you fully configure the RosettaNet accelerator, including starting the BTARN orchestrations. See [Install and configure](install-configure-biztalk-accelerator-for-rosettanet.md).
  
- This tutorial simulates a real-world scenario by using two computers instead of a single computer with a loopback agreement. Whenever this tutorial uses computer names, it uses a placeholder. Replace that placeholder with the actual computer name you chose. For example, if the computer that is running your Contoso solution is named **Contoso**, replace any occurrences in the tutorial of \\\\<contoso<strong>_</strong>*computer*\> with that computer name.  
  
- This tutorial promotes secure communication through certificates between Contoso and Fabrikam. You must generate any certificates you require, and install them on their respective computers.  
  
## Next steps 
  
-   [Step 1: Creating a Certification Authority](../../adapters-and-accelerators/accelerator-rosettanet/step-1-creating-a-certification-authority.md)  
  
-   [Step 2: Creating Public and Private Certificates](../../adapters-and-accelerators/accelerator-rosettanet/step-2-creating-public-and-private-certificates.md)  
  
-   [Step 3: Importing Public and Private Certificates](../../adapters-and-accelerators/accelerator-rosettanet/step-3-importing-public-and-private-certificates.md)  
  
-   [Step 4: Enabling Secure Sockets Layer in IIS](../../adapters-and-accelerators/accelerator-rosettanet/step-4-enabling-secure-sockets-layer-in-iis.md)