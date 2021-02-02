---
description: "Learn more about: Step 3B: Bind the orchestration with dynamic send port for FileAct Store and Forward (Pull) Scenario"
title: "Step 3B: Bind the orchestration with dynamic send port for FileAct Store and Forward (Pull) Scenario | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: bb973066-8797-4f51-a89e-3845f2811605
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Step 3B: Bind the orchestration with dynamic send port for FileAct Store and Forward (Pull) Scenario
Before you begin this step, you must complete [Step 3A: Create an orchestration for dynamic send port for FileAct Store and Forward (Pull) Scenario](../../adapters-and-accelerators/fileact-interact/step-3a-create-orchestration-for-dynamic-send-port-fileact-store-and-forward.md).  
  
### To add a FILE Receive location  
  
1.  Start **BizTalk Server Administration**.  
  
2.  In the BizTalk Server Administration Console, in the left pane, expand BizTalk Server Administration, expand **BizTalk Group**, expand **Platform Settings**, and then click **Host Instances**. Verify that the status for the **BizTalkServerApplication** host instance and FileActhost instance is **running**. If not, right-click the host instances, and click **Start**.  
  
3.  In the left pane, expand Applications, and then expand BizTalk Application 1. Click Orchestrations.  
  
4.  Right-click **DynamicSendOrchestration** and click **Properties**.  
  
5.  In the **Orchestration Properties** dialog box, in the left pane, click **Bindings** and do the following:  
  
    |**Use this**|**To do this**|  
    |------------------|--------------------|  
    |**Host**|From the drop-down list, select **BizTalkServer Application**.|  
    |**Dynamic Pull**|From the drop-down list, select **Tutorial_FA_DynamicSendPort**.|  
    |**SendPullResponseToSender**|From the drop-down list, select **Tutorial_FA_SendPullResponsetoReceiver**.|  
  
## See Also  
 [Step 3A: Create an orchestration for dynamic send port for FileAct Store and Forward (Pull) Scenario](../../adapters-and-accelerators/fileact-interact/step-3a-create-orchestration-for-dynamic-send-port-fileact-store-and-forward.md)
