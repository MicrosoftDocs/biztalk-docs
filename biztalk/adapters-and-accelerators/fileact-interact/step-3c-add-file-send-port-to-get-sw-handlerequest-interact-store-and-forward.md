---
description: "Learn more about: Step 3C: Add FILE send port to get Sw:HandleRequest-InterAct Store and Forward"
title: "Step 3C: Add FILE send port to get Sw:HandleRequest-InterAct Store and Forward"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Step 3C: Add FILE send port to get Sw:HandleRequest-InterAct Store and Forward
Before you begin this step, you must complete [Step 3B: Add an INTERACT Receive Location for the InterAct Store and Forward Scenario](../../adapters-and-accelerators/fileact-interact/step-3b-add-interact-receive-location-for-interact-store-and-forward-scenario.md).  
  
### To add a FILE send port to capture the Sw:HandleRequest message  
  
1.  Start **BizTalk Server Administration**.  
  
2.  In the console tree, expand the BizTalk group, and then expand the BizTalk application for which you want to create a send port.  
  
3.  Right-click **Send Ports**, point to **New**, and then click **Static One-way Send Port.**  
  
4.  In the **Send Port Properties** window, name the send port, Tutorial_IA_SendResponseToReceiver.  
  
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
    |**Value**|Type **Tutorial_IA_InputRequest_SnF**.|  
    |**Group by**|Leave the default value.|  
  
9. Click **OK**.  
  
## See Also  
 [Step 3: Create Send Ports and Receive Ports for the InterAct Store and Forward Scenario](../../adapters-and-accelerators/fileact-interact/step-3-create-send-and-receive-ports-for-interact-store-and-forward-scenario.md)   
 [Step 3A: Add a FILE Receive Location for the InterAct Store and Forward Scenario](../../adapters-and-accelerators/fileact-interact/step-3a-add-a-file-receive-location-for-interact-store-and-forward-scenario.md)   
 [Step 3B: Add an INTERACT Receive Location for the InterAct Store and Forward Scenario](../../adapters-and-accelerators/fileact-interact/step-3b-add-interact-receive-location-for-interact-store-and-forward-scenario.md)   
 [Step 3D: Add an INTERACT Send Port for the InterAct Store and Forward Scenario](../../adapters-and-accelerators/fileact-interact/step-3d-add-an-interact-send-port-for-the-interact-store-and-forward-scenario.md)
