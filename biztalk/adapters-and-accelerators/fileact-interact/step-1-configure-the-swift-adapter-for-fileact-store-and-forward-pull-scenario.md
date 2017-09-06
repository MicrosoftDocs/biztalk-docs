---
title: "Step 1: Configure the SWIFT Adapter for FileAct Store and Forward pull scenario | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fc271544-6bc8-4d62-aba0-3fe3295f2a2a
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Step 1: Configure the SWIFT Adapter for FileAct Store and Forward pull scenario
Complete [Preparing to Use the Tutorial](../../adapters-and-accelerators/fileact-interact/preparing-to-use-the-tutorial1.md) before you begin this step.
  
## Configure the SWIFT adapter  
  
1.  Start **BizTalk Server Administration**.  
  
2.  In the console tree, expand **BizTalk Server Administration**, expand the BizTalk group, expand **Platform Settings**, expand **Adapter**, right-click **FILEACT**, point to **New**, and then click **Send Handler**.  
  
3.  In the **FILEACT – Adapter HandlerProperties** dialog box, on the **General** tab, from the **Host name** drop-down list, select **FileActHost**, and then click **Properties**.  
  
4.  In the **FILEACT Transport Properties** dialog box, on the **Properties** tab, do the following:  
  
    |**Use this**|**To do this**|  
    |------------------|--------------------|  
    |**Arguments**|Type the following argument: -SagMessagePartner \<Fileact Client Message Partner created in SAG> **Note:**  The client in the argument is the MessagePartner you configured in SAG.|  
    |**Crypto Mode**|From the drop-down list, select **Advanced**.|  
    |**FACryptoMode**|From the drop-down list, select **Advanced**.|  
    |**LogMessages**|From the drop-down list, select **TRUE**. This enables the message events to be captured and tracked in the BAM portal.|  
    |**Enable**|False|  
    |**Event end-point**|Type the appropriate SAG end-point.|  
    |**PhysicalFolderName**|Type the name of the folder on the server. For example, C:\Fileact\ServerLocation.|  
    |**PollingInterval**|Type the appropriate value for PollingInterval. For example, 5. This indicates the interval (in seconds) after which the adapter checks for the status of file transfer.|  
    |**Password**|Type the password you use to connect to SAG. See SAG Help for more information.|  
    |**User Name**|Type the user name you use to connect to SAG.|  
  
5.  Click **OK** to close the FILEACT Transport Properties dialog box.  
  
6.  Click **OK** to close the FILEACT – Adapter Handler Properties dialog box.  
  
7.  In the Message box, click **OK**, and then restart the FileAct host instance.  
  
8.  Repeat step 1.  
  
9. In the console tree, expand **BizTalk Server Administration**, expand the **BizTalk** group, expand **Platform Settings**, expand **Adapter**, select **FILEACT**, open **BizTalkServerApplication** and then, click **Properties**.  
  
10. In the **FILEACT Transport Properties** dialog box, on the **Properties** tab, do the following:  
  
    |**Use this**|**To do this**|  
    |------------------|--------------------|  
    |**Arguments**|Type the following argument: –SagMessagePartner \<Fileact Client Message Partner created in SAG> **Note:**  The client in the argument is the MessagePartner you configured in SAG.|  
    |**Crypto Mode**|From the drop-down list, select **Advanced**.|  
    |**LogMessageBody**|From the drop-down list, select **TRUE**. This enables the message events to be captured and tracked in the BAM portal. **Note:**  If you set to TRUE, it preserves the message body in the BizTalk Tracking database. However, for security reasons, the message body can never be viewed in the BAM portal.|  
    |**LogMessages**|From the drop-down list, select **TRUE**. This enables the message events to be captured and tracked in the BAM portal.|  
    |**Enable**|**True**|  
    |**Event end-point**|Type the appropriate SAG end-point.|  
    |**PhysicalFolderName**|Type the name of the folder on the server. For example, C:\Fileact\ServerLocation.|  
    |**PollingInterval**|Type the appropriate value for PollingInterval. For example, 5. This indicates the interval (in seconds) after which the adapter checks for the status of file transfer.|  
    |**Password**|Type the password you use to connect to SAG. See SAG Help for more information.|  
    |**Username**|Type the user name you use to connect to SAG.|  
  
11. Click OK to close the FILEACT Transport Properties dialog box.  
  
12. Select make this the default handler option.  
  
13. Click OK to close the FILEACT – Adapter Handler Properties dialog box.  
  
14. In the Message box, click OK, and then restart the BizTalkServerApplication host instance.  
  
## See Also  
 [Step 2: Create Send Ports and Receive Ports for the FileAct Store and Forward (Pull) Scenario](../../adapters-and-accelerators/fileact-interact/step-2-create-send-and-receive-ports-for-fileact-store-and-forward-scenario.md)   
 [Step 3: Create and bind an orchestration with dynamic send port  for the File Act Store and Forward (Pull) Scenario](../../adapters-and-accelerators/fileact-interact/step-3-create-and-bind-an-orchestration-with-dynamic-send-port-for-file-act.md)   
 [Step 4: Test FileAct Store and Forward (Pull) End-to-End Scenario](../../adapters-and-accelerators/fileact-interact/step-4-test-fileact-store-and-forward-pull-end-to-end-scenario.md)