---
title: "Step 3C: Add FILE send port to get Sw:HandleRequest-InterAct real-time scenario | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 31e9c942-ba74-4ae2-b6e1-5266d0fbcb14
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Step 3C: Add FILE send port to get Sw:HandleRequest-InterAct real-time scenario
When you send a message to your partner, SWIFT transforms the message header and forwards the message to your partner as a Sw:HandleRequest message. Before you begin this step, you must complete [Step 3B: Add an INTERACT Receive Location for the InterAct Real-Time Scenario](../../adapters-and-accelerators/fileact-interact/step-3b-add-an-interact-receive-location-for-the-interact-real-time-scenario.md).  
  
### To add a FILE send port to capture Sw:HandleRequest message  
  
1.  Start **BizTalk Server Administration**.  
  
2.  In the console tree, expand the BizTalk group, and then expand the BizTalk application for which you want to create a send port.  
  
3.  Right-click **Send Ports**, point to **New**, and then click **Static One-way Send Port.**  
  
4.  In the **Send Port Properties** window, name the send port **Tutorial_IA_SendResponseToReceiver**.  
  
5.  In the **Send Port Properties** window, from the **Transport type** drop-down list, select **FILE**, and then click **Configure**.  
  
6.  In the **FILE Transport Properties** dialog box, in the **Destination folder** box, type C:\SWIFTAdapterTutorial\Interact\HandleRequest, and then click **OK**.  
  
7.  In the **Send Port Properties** window, do the following:  
  
    |**Use this**|**To do this**|  
    |------------------|--------------------|  
    |**Send handler**|From the drop-down list, select **BizTalkServerApplication**.|  
    |**Send pipeline**|From the drop-down list, select **XMLTransmit**.|  
  
8.  In the **Send Port Properties** window, on the **Filters** tab, do the following:  
  
    |**Use this**|**To do this**|  
    |------------------|--------------------|  
    |**Property**|From the drop-down list, select **BTS.ReceivePortName**.|  
    |**Operator**|From the drop-down list, select **==**.|  
    |**Value**|Type **Tutorial_IA_HandleRequestOneWay_RealTime.**|  
    |**Group by**|Leave the default value.|  
  
9. Click **OK**.  
  
## See Also  
 [Step 3: Create Send and Receive Ports for the InterAct Real-Time Scenario](../../adapters-and-accelerators/fileact-interact/step-3-create-send-and-receive-ports-for-the-interact-real-time-scenario.md)   
 [Step 3A: Add a FILE Receive Location for the InterAct Real-Time Scenario](../../adapters-and-accelerators/fileact-interact/step-3a-add-a-file-receive-location-for-the-interact-real-time-scenario.md)   
 [Step 3B: Add an INTERACT Receive Location for the InterAct Real-Time Scenario](../../adapters-and-accelerators/fileact-interact/step-3b-add-an-interact-receive-location-for-the-interact-real-time-scenario.md)   
 [Step 3D: Add a FILE Send Port to Capture the Sw:HandleResponse Message for the InterAct Real-Time Scenario](../../adapters-and-accelerators/fileact-interact/step-3d-add-file-send-port-to-get-sw-handleresponse-message-for-interact.md)   
 [Step 3E: Add an INTERACT Send Port for the InterAct Real-Time Scenario](../../adapters-and-accelerators/fileact-interact/step-3e-add-an-interact-send-port-for-the-interact-real-time-scenario.md)