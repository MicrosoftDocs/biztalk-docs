---
description: "Learn more about: Step 4D: Test a Valid Instance for the InterAct Store and Forward (Pull) Scenario"
title: "Step 4D: Test a Valid Instance for the InterAct Store and Forward (Pull) Scenario | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7c2933d0-bbe3-4486-832e-5009b2d760ac
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Step 4D: Test a Valid Instance for the InterAct Store and Forward (Pull) Scenario
Before you begin this step, you must complete [Step 4C: Create a Test Instance for the InterAct Store and Forward (Pull) Scenario](../../adapters-and-accelerators/fileact-interact/step-4c-create-a-test-instance-for-interact-store-and-forward-pull-scenario.md).  
  
### To test a valid instance  
  
1.  Drop the file ExchangeReqSimple.xml into c:\SWIFTAdapterTutorial\Interact\InputRequest_SnF.  
  
2.  Verify that after a moment, the ExchangeReqSimple.xml file disappears from the folder.  
  
3.  Drop the file acquirequeue.xml into c:\SWIFTAdapterTutorial\Interact\PullRequest.  
  
4.  Browse to C:\SWIFTAdapterTutorial\Interact\PullResponse Verify that Sw:HandleRequest is in the folder.  
  
5.  Open the Sw:HandleRequest message in a text editor, such as Notepad, and verify that the payload section is the same as in the file ExchangeReqSimple.xml.  
  
## See Also  
 [Step 4A: Start the SWIFTNet Service for the InterAct Store and Forward (Pull) Scenario](../../adapters-and-accelerators/fileact-interact/step-4a-start-swiftnet-service-for-the-interact-store-and-forward-scenario.md)   
 [Step 4B: Start the Send Ports and Receive Ports for the InterAct Store and Forward (Pull) Scenario](../../adapters-and-accelerators/fileact-interact/step-4b-start-send-and-receive-ports-for-interact-store-and-forward-scenario.md)   
 [Step 4C: Create a Test Instance for the InterAct Store and Forward (Pull) Scenario](../../adapters-and-accelerators/fileact-interact/step-4c-create-a-test-instance-for-interact-store-and-forward-pull-scenario.md)
