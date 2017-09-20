---
title: "Step 3E: Add a FILE Send Port to Capture Sw:ExchangeFileResponse Message for the FileAct Real-Time Scenario | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b9314f86-a2c9-4ef3-8474-b7e2e2f8bf66
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Step 3E: Add a FILE Send Port to Capture Sw:ExchangeFileResponse Message for the FileAct Real-Time Scenario
Before you begin this step, you must complete [Step 3D: Add a FILEACT Send Port for the FileAct Real-Time Scenario](../../adapters-and-accelerators/fileact-interact/step-3d-add-a-fileact-send-port-for-the-fileact-real-time-scenario.md).  
  
### To add a FILE send port to capture Sw:ExchangeFileResponse message  
  
1.  Start **BizTalk Server Administration**.  
  
2.  In the console tree, expand the BizTalk group, and then expand the BizTalk application for which you want to create a send port.  
  
3.  Right-click **Send Ports**, point to **New**, and then click **Static One-way Send Port.**  
  
4.  In the **Send Port Properties** window, name the send port, Tutorial_FA_SendResponseToSender.  
  
5.  In the **Send Port Properties** window, from the **Transport type** drop-down list, select **FILE**, and then click **Configure**.  
  
6.  In the **FILE Transport Properties** dialog box, in the **Destination folder** box, type C:\SWIFTAdapterTutorial\Fileact\ResponseClient, and then click **OK**.  
  
7.  In the **Send Port Properties** window, do the following:  
  
    |**Use this**|**To do this**|  
    |------------------|--------------------|  
    |**Send handler**|From the drop-down list, select **BizTalkServerApplication**.|  
    |**Send pipeline**|From the drop-down list, select **XMLTransmit**.|  
  
8.  In the **Send Port Properties** window, on the **Filters** tab, do the following:  
  
    |**Use this**|**To do this**|  
    |------------------|--------------------|  
    |**Property**|From the drop-down list, select **BTS.SPName**.|  
    |**Operator**|From the drop-down list, select **==**.|  
    |**Value**|Type Tutorial_FA_SendRequest_RealTime.|  
    |**Group by**|Leave the default value.|  
  
9. Click **OK**.  
  
## See Also  
 [Step 3: Create the Send Ports and Receive Ports for the FileAct Real-Time Scenario](../../adapters-and-accelerators/fileact-interact/step-3-create-the-send-ports-and-receive-ports-for-fileact-real-time-scenario.md)   
 [Step 3A: Add a FILE Receive Location for the FileAct Real-Time Scenario](../../adapters-and-accelerators/fileact-interact/step-3a-add-a-file-receive-location-for-the-fileact-real-time-scenario.md)   
 [Step 3B: Add a FILEACT Receive Location for the FileAct Real-Time Scenario](../../adapters-and-accelerators/fileact-interact/step-3b-add-a-fileact-receive-location-for-the-fileact-real-time-scenario.md)   
 [Step 3C: Add a FILE Send Port to Capture Sw:HandleRequest Message for the FileAct Real-Time Scenario](../../adapters-and-accelerators/fileact-interact/step-3c-add-file-send-port-to-get-sw-handlerequest-message-for-fileact.md)   
 [Step 3D: Add a FILEACT Send Port for the FileAct Real-Time Scenario](../../adapters-and-accelerators/fileact-interact/step-3d-add-a-fileact-send-port-for-the-fileact-real-time-scenario.md)