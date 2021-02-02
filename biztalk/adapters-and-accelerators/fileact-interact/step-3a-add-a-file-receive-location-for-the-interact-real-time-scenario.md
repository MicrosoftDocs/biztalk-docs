---
description: "Learn more about: Step 3A: Add a FILE Receive Location for the InterAct Real-Time Scenario"
title: "Step 3A: Add a FILE Receive Location for the InterAct Real-Time Scenario | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e5579375-8c05-4583-bcaa-b483ac275d8a
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Step 3A: Add a FILE Receive Location for the InterAct Real-Time Scenario
Set up a receive location that enables you to easily drop test files for validation. You use this location to test the scenario.  
  
## Add a FILE receive location  
  
1.  Start **BizTalk Server Administration**.  
  
2.  In the console tree, expand the BizTalk group, and then expand the BizTalk application for which you want to create a receive port.  
  
3.  Right-click **Receive Ports**, point to **New**, and then click **One-way Receive Port.**  
  
4.  In the **Receive Port Properties** window, name the receive port, **Tutorial_IA_InputRequest_RealTime**.  
  
5.  In the **Receive Port Properties** window, on the **Receive Locations** tab, click **New**.  
  
6.  In the **Receive Location Properties** window, on the **General** tab, from the **Transport type** drop-down list, select **FILE**, and then click **Configure**.  
  
7.  In the **FILE Transport Properties** dialog box, in the **Receive folder** box, type **C:\SWIFTAdapterTutorial\Interact\InputRequest_RealTime**, and then click **OK**.  
  
8.  In the **Receive Location Properties** window, on the **General** tab, do the following:  
  
    |**Use this**|**To do this**|  
    |------------------|--------------------|  
    |**Receive handler**|From the drop-down list, select **BizTalkServerApplication**.|  
    |**Receive pipeline**|From the drop-down list, select **XMLReceive**.|  
  
9. Click **OK**.  
  
## See Also  
 [Step 3: Create Send and Receive Ports for the InterAct Real-Time Scenario](../../adapters-and-accelerators/fileact-interact/step-3-create-send-and-receive-ports-for-the-interact-real-time-scenario.md)   
 [Step 3B: Add an INTERACT Receive Location for the InterAct Real-Time Scenario](../../adapters-and-accelerators/fileact-interact/step-3b-add-an-interact-receive-location-for-the-interact-real-time-scenario.md)   
 [Step 3C: Add a FILE Send Port to Capture the Sw:HandleRequest Message for the InterAct Real-Time Scenario](../../adapters-and-accelerators/fileact-interact/step-3c-add-file-send-port-to-get-sw-handlerequest-interact-real-time-scenario.md)   
 [Step 3D: Add a FILE Send Port to Capture the Sw:HandleResponse Message for the InterAct Real-Time Scenario](../../adapters-and-accelerators/fileact-interact/step-3d-add-file-send-port-to-get-sw-handleresponse-message-for-interact.md)   
 [Step 3E: Add an INTERACT Send Port for the InterAct Real-Time Scenario](../../adapters-and-accelerators/fileact-interact/step-3e-add-an-interact-send-port-for-the-interact-real-time-scenario.md)
