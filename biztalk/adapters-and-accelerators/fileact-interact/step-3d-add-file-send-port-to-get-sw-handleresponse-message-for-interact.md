---
title: "Step 3D: Add a FILE Send Port to Capture the Sw:HandleResponse Message for the InterAct Real-Time Scenario | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e05e4d20-4cf2-402f-aaea-66987cb6515a
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Step 3D: Add a FILE Send Port to Capture the Sw:HandleResponse Message for the InterAct Real-Time Scenario
Complete [Step 3C: Add a FILE Send Port to Capture the Sw:HandleRequest Message for the InterAct Real-Time Scenario](../../adapters-and-accelerators/fileact-interact/step-3c-add-file-send-port-to-get-sw-handlerequest-interact-real-time-scenario.md) before you begin this step.
  
## Add a FILE send port to capture Sw:HandleResponse message  
  
1.  Start **BizTalk Server Administration**.  
  
2.  In the console tree, expand the BizTalk group, and then expand the BizTalk application for which you want to create a send port.  
  
3.  Right-click **Send Ports**, point to **New**, and then click **Static One-way Send Port.**  
  
4.  In the **Send Port Properties** window, name the send port **Tutorial_IA_SendResponseToSender**.  
  
5.  In the **Send Port Properties** window, from the **Transporttype** drop-down list, select **FILE**, and then click **Configure**.  
  
6.  In the **FILE Transport Properties** dialog box, in the **Destination folder** box, type **C:\SWIFTAdapterTutorial\Interact\Response**, and then click **OK**.  
  
7.  In the **Send Port Properties** window, do the following:  
  
    |**Use this**|**To do this**|  
    |------------------|--------------------|  
    |**Send handler**|From the drop-down list, select **BizTalkServerApplication**.|  
    |**Send pipeline**|From the drop-down list, select **XMLTransmit**.|  
  
8.  In the **Send Port Properties** window, on the **Filters** tab, do the following:  
  
    |**Use this**|**To do this**|  
    |------------------|--------------------|  
    |First row: **Property**|From the drop-down list, select **BTS.SPName**.|  
    |First row: **Operator**|From the drop-down list, select **==**.|  
    |First row: **Value**|Type **Tutorial_IA_HandleRequest_RealTime**.|  
    |First row: **Group by**|From the drop-down list, select **OR**.|  
    |Second row: **Property**|From the drop-down list, select **BTS.MessageType**.|  
    |Second row: **Operator**|From the drop-down list, select **==**.|  
    |Second row: **Value**|Type **SwInt-ExchangeResponse**.|  
    |Second row: **Group by**|Leave the default value.|  
  
9. Click **OK**.  
  
## See Also  
 [Step 3: Create Send and Receive Ports for the InterAct Real-Time Scenario](../../adapters-and-accelerators/fileact-interact/step-3-create-send-and-receive-ports-for-the-interact-real-time-scenario.md)   
 [Step 3A: Add a FILE Receive Location for the InterAct Real-Time Scenario](../../adapters-and-accelerators/fileact-interact/step-3a-add-a-file-receive-location-for-the-interact-real-time-scenario.md)   
 [Step 3B: Add an INTERACT Receive Location for the InterAct Real-Time Scenario](../../adapters-and-accelerators/fileact-interact/step-3b-add-an-interact-receive-location-for-the-interact-real-time-scenario.md)   
 [Step 3C: Add a FILE Send Port to Capture the Sw:HandleRequest Message for the InterAct Real-Time Scenario](../../adapters-and-accelerators/fileact-interact/step-3c-add-file-send-port-to-get-sw-handlerequest-interact-real-time-scenario.md)   
 [Step 3E: Add an INTERACT Send Port for the InterAct Real-Time Scenario](../../adapters-and-accelerators/fileact-interact/step-3e-add-an-interact-send-port-for-the-interact-real-time-scenario.md)