---
description: "Learn more about: Step 4D: Test a Valid Instance for the FileAct Store and Forward (Pull) Scenario"
title: "Step 4D: Test a Valid Instance for the FileAct Store and Forward (Pull) Scenario"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Step 4D: Test a Valid Instance for the FileAct Store and Forward (Pull) Scenario
Before you begin this step, you must complete [Step 4C: Create a Test Instance for the FileAct Store and Forward (Pull) Scenario](../../adapters-and-accelerators/fileact-interact/step-4c-create-a-test-instance-for-fileact-store-and-forward-pull-scenario.md).  
  
### To test a valid instance  
  
1.  Drop the file PutReqSimple.xml into **C:\SWIFTAdapterTutorial\Fileact\FileRequestDropSnF**.  
  
2.  Verify that after a moment, the PutReqSimple.xml file disappears from the folder.  
  
3.  Drop the file fileactcquirequeue.xml into **C:\SWIFTAdapterTutorial\FileAct\PullRequest**.  
  
4.  Verify that the Sample_Put.txt file is transferred from **C:\SWIFTAdapterTutorial\Fileact\ClientLocation** to **C:\SWIFTAdapterTutorial\Fileact\ServerLocation**, and that responses appear in **C:\SWIFTAdapterTutorial\PullResponse**.  
  
## See Also  
 [Step 4A: Start the SWIFTNet Service for the FileAct Store and Forward (Pull) Scenario](../../adapters-and-accelerators/fileact-interact/step-4a-start-swiftnet-service-for-fileact-store-and-forward-pull-scenario.md)   
 [Step 4B: Start the Send Ports and Receive Ports for the FileAct Store and Forward (Pull) Scenario](../../adapters-and-accelerators/fileact-interact/step-4b-start-send-and-receive-ports-for-fileact-store-and-forward-scenario.md)   
 [Step 4C: Create a Test Instance for the FileAct Store and Forward (Pull) Scenario](../../adapters-and-accelerators/fileact-interact/step-4c-create-a-test-instance-for-fileact-store-and-forward-pull-scenario.md)
