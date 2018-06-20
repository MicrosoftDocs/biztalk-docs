---
title: "Step 3: Edit the Partner Interface Process | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "modifying, PIPs"
  - "PIPs, modifying"
  - "loopback tutorial, modifying PIPs"
ms.assetid: 4d03c598-8ed4-4135-9748-ede101997fd0
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Step 3: Edit the Partner Interface Process
In this step, you edit the Partner Interface Process (PIP) configuration settings to disable secure transport if you do not have a Secure Sockets Layer (SSL) certificate configured in [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® Internet Information Services (IIS). Because the loopback scenario does not support signing for both incoming and outgoing messages, you must change the default settings to continue with the tutorial. You modify the STD_0C1_R01.02 PIP.  
  
### To edit the STD_0C1_R01.02 PIP  
  
1. In the **[!INCLUDE[BTARN_CurrentVersion_abbrev](../../includes/btarn-currentversion-abbrev-md.md)]** Management Console, expand **BizTalk \<version\> Accelerator for RosettaNet**, click **Process Configuration Settings**, right-click **STD_0C1_R01.02**, and then click **Properties**.  
  
2. In the STD_0C1_R01.02Properties dialog box, on the **Activity** tab, set the **Is Secure Transport Required** option to `False`. Perform this step only if you do not have a SSL certificate on your IIS Web server.  
  
3. Set the **Non-Repudiation Required** to `False`, set **Is Authorization Required** to `False`, set **Non-Repudiation of Origin and Content** to `False`, and then click **OK**.  
  
    This disables non-repudiation and the use of certificates for signing messages.  
  
## See Also  
 [Step 4: Create a Trade Agreement](../../adapters-and-accelerators/accelerator-rosettanet/step-4-create-a-trade-agreement.md)   
 [Authorization and Non-Repudiation Properties](../../adapters-and-accelerators/accelerator-rosettanet/authorization-and-non-repudiation-properties.md)