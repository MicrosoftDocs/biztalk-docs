---
title: "Step 5: Create a Mirror Agreement | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "creating, mirror agreements"
  - "loopback tutorial, creating mirror agreements"
  - "agreements, mirror agreements"
ms.assetid: 6aa70b1e-7d38-49f7-9d5f-f008cbe3df66
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Step 5: Create a Mirror Agreement
In this step, you use the Loopback utility to create a mirror agreement simulating the trading partner on the same computer on which you configured the home organization. The Loopback utility is a command-line tool.  
  
### To create a mirror agreement using the Loopback utility  
  
1. Click **Start**, click **Run**, type **cmd**, and then click **OK**.  
  
2. At the command prompt, move to \<*drive*\>:\Program Files (x86)\Microsoft BizTalk \<version\> Accelerator for RosettaNet\SDK. Type the following command and then press **Enter**:  
  
   ```  
   Loopback /enable HOME  
   ```  
  
3. After the command executed in step 2 has completed, type the following command in the command prompt, and then press **Enter**:  
  
   ```  
   Loopback /mirror "Trade Agreement"   
   ```  
  
   The Loopback utility automatically creates send ports for the home organization (initiator) and a mirror trade agreement for the partner organization. The partner uses the two new send ports to communicate with the home organization.  
  
> [!NOTE]
>  You must re-mirror the trade agreement whenever you update the original trade agreement.  
  
## See Also  
 [Step 6: Start Orchestrations](../../adapters-and-accelerators/accelerator-rosettanet/step-6-start-orchestrations.md)
