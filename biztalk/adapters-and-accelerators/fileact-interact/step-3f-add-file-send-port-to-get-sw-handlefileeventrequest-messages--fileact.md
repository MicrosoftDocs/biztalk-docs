---
description: "Learn more about: Step 3F: Add a FILE Send Port for the FileAct Real-Time Scenario to Capture Sw-HandleFileEventRequest Messages"
title: "Step 3F: Add a FILE Send Port for the FileAct Real-Time Scenario to Capture Sw-HandleFileEventRequest Messages"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: how-to
---
# Step 3F: Add a FILE Send Port for the FileAct Real-Time Scenario to Capture Sw-HandleFileEventRequest Messages
Before you begin this step, you must complete [Step 3E: Add a FILE Send Port to Capture Sw:ExchangeFileResponse Message for the FileAct Real-Time Scenario](../../adapters-and-accelerators/fileact-interact/step-3e-add-file-send-port-to-get-sw-exchangefileresponse-message-for-fileact.md)  
  
### To add a FILE send port to capture Status Events:  
  
1.  Start **BizTalk Server Administration**.  
  
2.  In the console tree, expand the BizTalk group, and then expand the BizTalk application for which you want to create a send port.  
  
3.  Right-click **Send Ports**, point to **New**, and then click **Static One-way Send Port**.  
  
4.  In the **Send Port Properties** window, name the send port, Tutorial_ GetStatusReports.  
  
5.  In the **Send Port Properties** window, from the **Transport type** drop-down list, select **FILE**, and then click **Configure**.  
  
6.  In the **FILE Transport Properties** dialog box, in the **Destination folder** box, type C:\SWIFTAdapterTutorial\Fileact\ StatusEvents, and then click **OK**.  
  
7.  In the **Send Port Properties** window, do the following:  
  
    |**Use this**|**To do this**|  
    |------------------|--------------------|  
    |**Send handler**|From the drop-down list, select **BizTalkServerApplication**.|  
    |**Send pipeline**|From the drop-down list, select **XMLTransmit**.|  
  
8.  In the **Send Port Properties** window, on the **Filters** tab, do the following:  
  
    |**Use this**|**To do this**|  
    |------------------|--------------------|  
    |**Property**|Select BTS. MessageType|  
    |**Operator**|Select ==|  
    |**Value**|Type Sw-HandleFileEventRequest|  
    |**Group**|Or|  
    |**Property**|Select BTS. MessageType|  
    |**Operator**|Select ==|  
    |**Value**|Type Sw-ExchangeSnFResponse|
