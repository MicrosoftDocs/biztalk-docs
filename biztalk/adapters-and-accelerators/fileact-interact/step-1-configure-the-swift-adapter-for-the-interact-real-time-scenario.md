---
description: "Learn more about: Step 1: Configure the SWIFT Adapter for the InterAct Real-Time Scenario"
title: "Step 1: Configure the SWIFT Adapter for the InterAct Real-Time Scenario"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Step 1: Configure the SWIFT Adapter for the InterAct Real-Time Scenario
The following steps explain how to configure the send handler for the Interact adapter. Before you begin the procedure, you must complete the requirements listed in [Preparing to Use the Tutorial](../../adapters-and-accelerators/fileact-interact/preparing-to-use-the-tutorial1.md).  
  
### To configure the SWIFT adapter  
  
1.  Start **BizTalk Server Administration**.  
  
2.  In the console tree, expand **BizTalk Server Administration**, expand the BizTalk group, expand **Platform Settings**, expand **Adapter**, right-click **INTERACT**, point to **New**, and then click **Send Handler**.  
  
3.  In the **INTERACT – Adapter Handler Properties** dialog box, on the **General** tab, from the **Host name** drop-down list, select **interacthost**, and then click **Properties**.  
  
4.  In the **INTERACTTransport Properties** dialog box, on the **Properties** tab, do the following:  
  
    |**Use this**|**To do this**|  
    |------------------|--------------------|  
    |**Arguments**|Type the following argument: **SagMessagePartner**\<Interact Client Message Partner created in SAG\> **Note:**  The client in the argument is the MessagePartner you configured in SAG.|  
    |**Crypto Mode**|From the drop-down list, select **Advanced**.|  
    |**LogMessageBody**|From the drop-down list, select `FALSE`. **Note:**  If you set to `TRUE`, it preserves the message body in the tracking database. However, for security reasons, the message body can never be viewed in the BAM portal.|  
    |**LogMessages**|From the drop-down list, select `TRUE`. This enables the message events to be captured and tracked in the BAM portal.|  
    |**Enable**|False|  
    |**Password**|Type the password you use to connect to SAG. See SAG Help for more information.|  
    |**User Name**|Type the user name you use to connect to SAG.|  
  
5.  Click **OK** to close the INTERACT Transport Properties dialog box.  
  
6.  Click **OK** to close the INTERACT – Adapter Handler Properties dialog box.  
  
7.  In the message box, click **OK**, and then restart the Interact host instance.  
  
## See Also  
 [InterAct Real-Time Scenario](../../adapters-and-accelerators/fileact-interact/interact-real-time-scenario.md)   
 [Step 1: Configure the SWIFT Adapter for the InterAct Real-Time Scenario](../../adapters-and-accelerators/fileact-interact/step-1-configure-the-swift-adapter-for-the-interact-real-time-scenario.md)   
 [Step 2: Add SWIFTNet Configuration to the Paramfile for the InterAct Real-Time Scenario](../../adapters-and-accelerators/fileact-interact/step-2-add-swiftnet-configuration-to-paramfile-for-interact-real-time-scenario.md)   
 [Step 3: Create Send and Receive Ports for the InterAct Real-Time Scenario](../../adapters-and-accelerators/fileact-interact/step-3-create-send-and-receive-ports-for-the-interact-real-time-scenario.md)   
 [Step 4: Test the InterAct Real-Time End-to-End Scenario](../../adapters-and-accelerators/fileact-interact/step-4-test-the-interact-real-time-end-to-end-scenario.md)
