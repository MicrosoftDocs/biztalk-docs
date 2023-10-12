---
description: "Learn more about: Step 2B: Add FILE Send Ports to Capture the Sw:HandleFileRequest and Sw:HandleSnFRequest Messages for the FileAct Store and Forward (Pull) Scenario"
title: "Step 2B: Add FILE Send Ports to Capture the Sw:HandleFileRequest and Sw:HandleSnFRequest Messages for the FileAct Store and Forward (Pull) Scenario"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Step 2B: Add FILE Send Ports to Capture the Sw:HandleFileRequest and Sw:HandleSnFRequest Messages for the FileAct Store and Forward (Pull) Scenario
Before you begin this step, you must complete the [Step 2A: Add FILE Receive Locations for the FileAct Store and Forward (Pull) Scenario](../../adapters-and-accelerators/fileact-interact/step-2a-add-file-receive-locations-for-fileact-store-and-forward-scenario.md) section.  

### To add a FILE send port to capture the Sw: HandleFileRequest message  

1. Start **BizTalk Server Administration**.  

2. In the console tree, expand the BizTalk group, and then expand the BizTalk application for which you want to create a send port.  

3. Right-click **Send Ports**, point to **New**, and then click **Static One-way Send Port.**  

4. In the **Send Port Properties** window, name the send port, **Tutorial_FA_SendPullResponsetoReceiver**.  

5. In the **Send Port Properties** window, from the **Transport type** drop-down list, select **FILE**, and then click **Configure**.  

6. In the **FILE Transport Properties** dialog box, in the **Destination folder** box, type **C:\SWIFTAdapterTutorial\FileAct\PullResponse**, and then click **OK**.  

7. In the **Send Port Properties** window, do the following:  


   |   **Use this**    |                        **To do this**                         |
   |-------------------|---------------------------------------------------------------|
   | **Send handler**  | From the drop-down list, select **BizTalkServerApplication**. |
   | **Send pipeline** |       From the drop-down list, select **XMLTransmit**.        |


8. Click **OK**.  

9. Repeat step 1 and 2.  

10. Right-click **Send Ports**, point to **New**, and then click **Dynamic Solicit-Response Send Port**.  

11. In the **Send Port Properties** window, name the send port<strong>, Tutorial_IA_DynamicSendPort</strong>.  

12. In the **Send Port Properties** window, do the following:  


    |     **Use this**     |                  **To do this**                  |
    |----------------------|--------------------------------------------------|
    |  **Send pipeline**   | From the drop-down list, select **XMLTransmit**. |
    | **Receive pipeline** | From the drop-down list, select **XMLReceive**.  |


13. Click **OK**.  

## See Also  
 [Step 2A: Add FILE Receive Locations for the FileAct Store and Forward (Pull) Scenario](../../adapters-and-accelerators/fileact-interact/step-2a-add-file-receive-locations-for-fileact-store-and-forward-scenario.md)   
 [Step 2C: Add a FILEACT Send Port for the FileAct Store and Forward (Pull) Scenario](../../adapters-and-accelerators/fileact-interact/step-2c-add-a-fileact-send-port-for-fileact-store-and-forward-pull-scenario.md)
