---
title: "Step 6: Start Orchestrations | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "orchestrations, starting"
  - "loopback tutorial, starting orchestratrations"
ms.assetid: f16a4a77-04fe-4e73-8517-556668174eb9
caps.latest.revision: 11
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Step 6: Start Orchestrations
In this step, you use [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] to start the orchestrations for [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)].  
  
### To start the BTARN orchestrations using Visual Studio  
  
1.  In the **BTARN** Management Console, expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Applications**, and then expand **BizTalk Application 1**.  
  
2.  Click **Send Ports**, and then start **PrivateInitiator_To_LOB** and **PrivateResponder_To_LOB** send ports.  
  
3.  Click **Receive Locations**, and then enable **LOB_To_PrivateInitiator**, **LOB_To_PrivateResponder**, **Async_Http_Receive**, and **Sync_Http_Receive** receive locations.  
  
4.  Click **Orchestrations**, and start all **BTARN orchestrations**.  
  
## See Also  
 [Step 7: Create a Sample LOB Message](../../adapters-and-accelerators/accelerator-rosettanet/step-7-create-a-sample-lob-message.md)   
 [Stopping and Starting Orchestrations, Send Ports, and Receive Locations Programmatically](../../adapters-and-accelerators/accelerator-rosettanet/code-to-stop-and-start-orchestrations-send-ports-and-receive-locations.md)