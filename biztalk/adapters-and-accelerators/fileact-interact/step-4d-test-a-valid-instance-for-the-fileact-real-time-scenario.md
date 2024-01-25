---
description: "Learn more about: Step 4D: Test a Valid Instance for the FileAct Real-Time Scenario"
title: "Step 4D: Test a Valid Instance for the FileAct Real-Time Scenario"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Step 4D: Test a Valid Instance for the FileAct Real-Time Scenario
Before you begin this step, you must complete [Step 4C: Create a Test Instance for the FileAct Real-Time Scenario](../../adapters-and-accelerators/fileact-interact/step-4c-create-a-test-instance-for-the-fileact-real-time-scenario.md).  
  
### To test a valid instance  
  
1.  Drop the file PutReqSimple.xml into C:\SWIFTAdapterTutorial\Fileact\FileRequestDropRealTime.  
  
2.  Verify that after a moment, the PutReqSimple.xml file disappears from the folder.  
  
3.  Verify that the Sample_Put.txt file is transferred from: C:\SWIFTAdapterTutorial\Fileact\ClientLocation to C:\SWIFTAdapterTutorial\Fileact\ServerLocation, and that responses appear in C:\SWIFTAdapterTutorial\Fileact\ResponseClient and C:\SWIFTAdapterTutorial\Fileact\ResponseServer.  
  
4.  Check status event (c:\SWIFTAdapterTutorial\Fileact\StatusEvents) folder for three HandleFileEventRequest messages. These messages should contain the following Transfer status:  
  
     HandleFileEventRequest message\<Sw-TransferStatus\>Accepted\</Sw-TransferStatus\>  
  
     HandleFileEventRequest message \<Sw-TransferStatus\>Initiated\</Sw-TransferStatus\>  
  
     HandleFileEventRequest message \<Sw-TransferStatus\>Completed\</Sw-TransferStatus\>  
  
## See Also  
 [Step 4: Test FileAct Real-Time End-to-End Scenario](../../adapters-and-accelerators/fileact-interact/step-4-test-fileact-real-time-end-to-end-scenario.md)   
 [Step 4A: Start the SWIFTNet Service for the FileAct Real-Time Scenario](../../adapters-and-accelerators/fileact-interact/step-4a-start-the-swiftnet-service-for-the-fileact-real-time-scenario.md)   
 [Step 4B: Start the Send Ports and Receive Ports for the FileAct Real-Time Scenario](../../adapters-and-accelerators/fileact-interact/step-4b-start-the-send-and-receive-ports-for-the-fileact-real-time-scenario.md)   
 [Step 4C: Create a Test Instance for the FileAct Real-Time Scenario](../../adapters-and-accelerators/fileact-interact/step-4c-create-a-test-instance-for-the-fileact-real-time-scenario.md)
