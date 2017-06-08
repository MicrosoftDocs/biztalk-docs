---
title: "Step 1: Configure the SWIFT Adapter for the FileAct Store and Forward Scenario | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 18653322-b748-4954-93f7-9a7a39e406f8
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Step 1: Configure the SWIFT Adapter for the FileAct Store and Forward Scenario
Complete [Preparing to Use the Tutorial](../../adapters-and-accelerators/fileact-interact/preparing-to-use-the-tutorial1.md) before you begin this step.
  
## Configure the SWIFT adapter  
  
1.  Start **BizTalk Server Administration**.  
  
2.  In the console tree, expand **BizTalk Server Administration**, expand the BizTalk group, expand **Platform Settings**, expand **Adapter**, right-click **FILEACT**, point to **New**, and then click **Send Handler**.  
  
3.  In the **FILEACT – Adapter HandlerProperties** dialog box, on the **General** tab, from the **Host name** drop-down list, select **fileacthost**, and then click **Properties**.  
  
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
    |**PollingInterval**|Type the appropriate interval (in seconds) after which the adapter checks for the status of file transfer.|  
    |**Password**|Type the password you use to connect to SAG. See SAG Help for more information.|  
    |**User Name**|Type the user name you use to connect to SAG.|  
  
5.  Click **OK** to close the FILEACT Transport Properties dialog box.  
  
6.  Click **OK** to close the FILEACT – Adapter Handler Properties dialog box.  
  
7.  In the Message box, click **OK**, and then restart the FileAct host instance.  
  
## Complete steps
 [FileAct Store and Forward Scenario](../../adapters-and-accelerators/fileact-interact/fileact-store-and-forward-scenario.md)   
 [Step 2: Add SWIFTNet Configuration to the Paramfile for the FileAct Store and Forward Scenario](../../adapters-and-accelerators/fileact-interact/step-2-add-swiftnet-configuration-to-paramfile-for-fileact-store-and-forward.md)   
 [Step 3: Create Send Ports and Receive Ports for the FileAct Store and Forward Scenario](../../adapters-and-accelerators/fileact-interact/step-3-create-send-ports-and-receive-ports-for-the-fileact-store-and-forward.md)   
 [Step 4: Test FileAct Store and Forward End-to-End Scenario](../../adapters-and-accelerators/fileact-interact/step-4-test-fileact-store-and-forward-end-to-end-scenario.md)