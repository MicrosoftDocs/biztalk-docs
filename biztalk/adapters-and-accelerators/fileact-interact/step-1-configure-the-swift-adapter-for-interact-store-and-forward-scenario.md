---
title: "Step 1: Configure the SWIFT Adapter for the InterAct Store and Forward (Pull) Scenario | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4182021c-36c9-4c96-b2fa-e23c87862cfe
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Step 1: Configure the SWIFT Adapter for the InterAct Store and Forward (Pull) Scenario
Before you begin this step, you must complete [Preparing to Use the Tutorial](../../adapters-and-accelerators/fileact-interact/preparing-to-use-the-tutorial1.md).  
  
### To configure the SWIFT adapter  
  
1.  Start **BizTalk Server Administration**.  
  
2.  In the console tree, expand BizTalk Server Administration, expand the BizTalk group, expand **Platform Settings**, expand **Adapter**, right-click **INTERACT**, point to **New**, and then click **Send Handler**.  
  
3.  In the **INTERACT – Adapter Handler Properties** dialog box, on the **General** tab, from the **Host name** drop-down list, select **interacthost**, and then click **Properties**.  
  
4.  In the **INTERACT Transport Properties** dialog box, on the **Properties** tab, do the following:  
  
    |**Use this**|**To do this**|  
    |------------------|--------------------|  
    |**Arguments**|Type the following argument: –SagMessagePartner \<Interact Client Message Partner created in SAG> **Note:**  The client in the argument is the MessagePartner you configured in SAG.|  
    |**Crypto Mode**|From the drop-down list, select **Advanced**.|  
    |**LogMessageBody**|From the drop-down list, select **FALSE**. **Note:**  If you set to TRUE, it preserves the message body in the BizTalk Tracking database. However, for security reasons, the message body can never be viewed in the BAM portal.|  
    |**LogMessages**|From the drop-down list, select **TRUE**. This enables the message events to be captured and tracked in the BAM portal.|  
    |**Enable**|False.|  
    |**Password**|Type the password you use to connect to SAG. See SAG Help for more information.|  
    |**Username**|Type the user name you use to connect to SAG.|  
  
5.  Click **OK** to close the INTERACT Transport Properties dialog box.  
  
6.  Click **OK** to close the INTERACT – Adapter Handler Properties dialog box.  
  
7.  In the message box, click **OK**, and then restart the InterAct host instance.  
  
8.  Repeat step 1.  
  
9. In the console tree, expand BizTalk Server Administration, expand the **BizTalk** group, expand **Platform Settings**, expand **Adapter**, select INTERACT, open **BizTalkServerApplication** and then, click **Properties**.  
  
10. In the **INTERACT Transport Properties** dialog box, on the **Properties** tab, do the following:  
  
    |**Use this**|**To do this**|  
    |------------------|--------------------|  
    |**Arguments**|Type the following argument: –SagMessagePartner \<Interact Client Message Partner created in SAG> **Note:**  The client in the argument is the MessagePartner you configured in SAG.|  
    |**Crypto Mode**|From the drop-down list, select **Advanced**.|  
    |**LogMessageBody**|From the drop-down list, select **FALSE**. **Note:**  If you set to TRUE, it preserves the message body in the BizTalk Tracking database. However, for security reasons, the message body can never be viewed in the BAM portal.|  
    |**LogMessages**|From the drop-down list, select **TRUE**. This enables the message events to be captured and tracked in the BAM portal.|  
    |**Enable**|True|  
    |**Password**|Type the password you use to connect to SAG. See SAG Help for more information.|  
    |**Username**|Type the user name you use to connect to SAG.|  
  
11. Click **OK** to close the INTERACT Transport Properties dialog box.  
  
12. Select **make this the default handler** option.  
  
13. Click **OK** to close the INTERACT– Adapter Handler Properties dialog box.  
  
14. In the Message box, click **OK**, and then restart the **BizTalkServerApplication** host instance.  
  
## See Also  
 [Step2: Create Send Ports and Receive Ports for the InterAct Store and Forward (Pull) Scenario](../../adapters-and-accelerators/fileact-interact/step-2-create-send-ports-and-receive-ports-for-the-interact-store-and-forward.md)   
 [Step3: Create an orchestration with  dynamic send port for the InterAct Store and Forward (Pull) Scenario](../../adapters-and-accelerators/fileact-interact/step-3-create-orchestration-with-dynamic-send-for-interact-store-and-forward.md)   
 [Step 4: Test the InterAct Store and Forward (Pull) End-to-End Scenario](../../adapters-and-accelerators/fileact-interact/step-4-test-the-interact-store-and-forward-pull-end-to-end-scenario.md)