---
title: "Step 4B: Start the Send Ports and Receive Ports for the InterAct Store and Forward Scenario | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c7b0ecd4-ea08-4567-80bd-14f465ba4867
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Step 4B: Start the Send Ports and Receive Ports for the InterAct Store and Forward Scenario
Before you begin this step, you must complete [Step 4A: Start the SWIFTNet Service for the InterAct Store and Forward Scenario](../../adapters-and-accelerators/fileact-interact/step-4a-start-the-swiftnet-service-for-the-interact-store-and-forward-scenario.md).  
  
### To start the send ports and receive ports  
  
1.  Start **BizTalk Server Administration**.  
  
2.  In the console tree, expand the BizTalk group, and then expand the BizTalk application where you created the send ports.  
  
3.  For each of the following send ports, right-click the send port, and then click **Start**:  
  
    -   **Tutorial_IA_SendResponseToReceiver**  
  
    -   **Tutorial_IA_SendResponseToSender**  
  
    -   **Tutorial_IA_SendRequest_SnF**  
  
4.  In the console tree, expand the BizTalk group, and then expand the BizTalk application where you created the receive locations.  
  
5.  For each of the following receive locations, right-click the receive location, and then click **Enable**:  
  
    -   **Tutorial_IA_InputRequest_SnF**  
  
    -   **Tutorial_IA_HandleRequestOneWay_SnF**  
  
## See Also  
 [Step 4: Test the InterAct Store and Forward End-to-End Scenario](../../adapters-and-accelerators/fileact-interact/step-4-test-the-interact-store-and-forward-end-to-end-scenario.md)   
 [Step 4A: Start the SWIFTNet Service for the InterAct Store and Forward Scenario](../../adapters-and-accelerators/fileact-interact/step-4a-start-the-swiftnet-service-for-the-interact-store-and-forward-scenario.md)   
 [Step 4C: Create a Test Instance for the InterAct Store and Forward Scenario](../../adapters-and-accelerators/fileact-interact/step-4c-create-a-test-instance-for-the-interact-store-and-forward-scenario.md)   
 [Step 4D: Test a Valid Instance for the InterAct Store and Forward Scenario](../../adapters-and-accelerators/fileact-interact/step-4d-test-a-valid-instance-for-the-interact-store-and-forward-scenario.md)