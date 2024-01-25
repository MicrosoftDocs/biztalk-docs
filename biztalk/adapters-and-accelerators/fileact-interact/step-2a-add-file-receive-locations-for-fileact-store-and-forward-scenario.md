---
title: "Step 2A- Add FILE Receive Locations"
description: Step 2A- Add FILE Receive Locations for the FileAct Store and Forward (Pull) Scenario in BizTalk Server
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---

# Step 2A: Add FILE Receive Locations for the FileAct Store and Forward (Pull) Scenario
Before you begin this step, you must complete [Step 1: Configure the SWIFT Adapter for the FileAct Store and Forward (Pull) Scenario](step-1-configure-the-swift-adapter-for-fileact-store-and-forward-pull-scenario.md).  
  
## Add a FILE Receive location  
  
1.  Start **BizTalk Server Administration**.  
  
2.  In the console tree, expand the BizTalk group, and then expand the BizTalk application for which you want to create a receive port.  
  
3.  Right-click **Receive Ports**, point to **New**, and then click **One-way Receive Port.**  
  
4.  In the **Receive Port Properties** window, name the receive port, **Tutorial_FA_InputRequest_SnF**.  
  
5.  In the **Receive Port Properties** window, on the **Receive Locations** tab, click **New**.  
  
6.  In the **Receive Location Properties** window, on the **General** tab, from the **Transport type** drop-down list, select **FILE**, and then click **Configure**.  
  
7.  In the **FILE Transport Properties** dialog box, type **C:\SWIFTAdapterTutorial\Fileact\FileRequestDropSnF**, and then click **OK**.  
  
8.  In the **Receive Location Properties** window, on the **General** tab, do the following:  
  
    |**Use this**|**To do this**|  
    |------------------|--------------------|  
    |**Receive handler**|From the drop-down list, select **BizTalkServerApplication**.|  
    |**Receive pipeline**|From the drop-down list, select **XMLReceive**.|  
  
9. Click **OK**.  
  
10. Repeat steps 1 and 2.  
  
11. Right-click **Receive Ports**, point to **New**, and then click **One-way Receive Port.**  
  
12. In the **Receive Port Properties** window, name the receive port, **Tutorial_ FA_InputRequest_PullMode**.  
  
13. In the **Receive Port Properties** window, on the **Receive Locations** tab, click **New**.  
  
14. In the **Receive Location Properties** window, on the **General** tab, from the **Transport type** drop-down list, select **FILE**, and then click **Configure**.  
  
15. In the **FILE Transport Properties** dialog box, type **C:\SWIFTAdapterTutorial\Interact\PullRequest**, and then click **OK**.  
  
16. In the **Receive Location Properties** window, on the **General** tab, do the following:  
  
    |**Use this**|**To do this**|  
    |------------------|--------------------|  
    |**Receive handler**|From the drop-down list, select **BizTalkServerApplication**.|  
    |**Receive pipeline**|From the drop-down list, select **XMLReceive**.|  
  
17. Click **OK**.  
  
## Next steps
-  [Step 2B: Add FILE Send Ports to Capture the Sw:HandleFileRequest and Sw:HandleSnFRequest Messages for the FileAct Store and Forward (Pull) Scenario](step-2b-add-file-send-ports--get-sw-handlefilerequest-and-sw-handlesnfrequest.md)   
-  [Step 2C: Add a FILEACT Send Port for the FileAct Store and Forward (Pull) Scenario](step-2c-add-a-fileact-send-port-for-fileact-store-and-forward-pull-scenario.md)