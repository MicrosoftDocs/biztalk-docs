---
title: "Step 3B: Add a FILEACT Receive Location for the FileAct Store and Forward Scenario | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0f30bb7d-1efb-4350-8809-be35f5634ea0
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Step 3B: Add a FILEACT Receive Location for the FileAct Store and Forward Scenario
Before you begin this step, you must complete [Step 3A: Add a FILE Receive Location for the FileAct Store and Forward Scenario](../../adapters-and-accelerators/fileact-interact/step-3a-add-a-file-receive-location-for-the-fileact-store-and-forward-scenario.md).  
  
### To add an FILEACT receive location  
  
1.  Start **BizTalk Server Administration**.  
  
2.  In the console tree, expand the BizTalk group, and then expand the BizTalk application for which you want to create a receive port.  
  
3.  Right-click **Receive Ports**, point to **New**, and then click **One-way Receive Port.**  
  
4.  In the **Receive Port Properties** window, name the receive port, Tutorial_FA_HandleRequestOneWay_SnF.  
  
5.  In the **Receive Port Properties** window, on the **Receive Locations** tab, click **New**.  
  
6.  In the **Receive Location Properties** window, on the **General** tab, from the **Transport type** drop-down list, select **FILEACT**, and then click **Configure**.  
  
7.  In the **FILEACT Transport Properties** dialog box, do the following:  
  
    |**Use this**|**To do this**|  
    |------------------|--------------------|  
    |**Password**|Type the password you use to connect to SAG. See SAG Help for more information.|  
    |**User name**|Type the user name you use to connect to SAG.|  
    |**Application name**|Type the Server \<Application Interface Name> for the SAG box routing set.|  
    |**Crypto Mode**|From the drop-down list, select **Advanced**.|  
    |**FACrypto Mode**|From the drop-down list, select **Advanced**.|  
    |**LogMessages**|From the drop-down list, select **TRUE**. This enables the message events to be captured and tracked in the BAM portal.|  
    |**MemberRef**|From the drop-down list, select **ResponsePayload**.|  
    |**Non-Repudiation Indicator**|From the drop-down list, select **FALSE**.|  
    |**Responder**|Type the appropriate \<Responder> string, based on your provisioning with SWIFT.|  
    |**ResponseCrypto**|From the drop-down list, select **FALSE**.|  
    |**Acknowledgement Indicator**|From the drop-down list, select **ResponsePayload**.|  
    |**FileCompression**|From the drop-down list, select None.|  
    |**PhysicalFolderName**|Type the name of the folder on the server. For example, C:\Fileact\ServerLocation.|  
    |**SubscribeFileEvents**|From the drop-down list, select **FALSE**.|  
    |**TransferAnswer**|From the drop-down list, select **Accepted**.|  
    |**AllFileEvents**|From the drop-down list, select **TRUE**.|  
    |**Event end-point**|Type the appropriate SAG end-point.|  
    |**FullFileStatus**|From the drop-down list, select **TRUE**.|  
    |**Timeout**|Type an appropriate number of seconds before timeout should occur.|  
    |**Acquire queue**|Type the queue name, based on your provisioning with SWIFT.|  
    |**ForceAcquire**|From the drop-down list, select **TRUE**.|  
    |**Order by**|From the drop-down list, select **FileAct**.|  
    |**Push session**|From the drop-down list, select **TRUE**.|  
    |**Recovery mode**|From the drop-down list, select **FALSE**.|  
    |**SNL end-point**|Type the appropriate end-point for the SAG routing set. This value should match the SnL endpoint you configured in SAG.|  
  
8.  Click **OK**.  
  
9. In the **Receive Location Properties** window, on the **General** tab, do the following:  
  
    |**Use this**|**To do this**|  
    |------------------|--------------------|  
    |**Receive handler**|From the drop-down list, select **BizTalkServerIsolatedHost**.|  
    |**Receive pipeline**|From the drop-down list, select **XMLReceive**.|  
  
10. Click **OK**.  
  
## See Also  
 [Step 3: Create Send Ports and Receive Ports for the FileAct Store and Forward Scenario](../../adapters-and-accelerators/fileact-interact/step-3-create-send-ports-and-receive-ports-for-the-fileact-store-and-forward.md)   
 [Step 3A: Add a FILE Receive Location for the FileAct Store and Forward Scenario](../../adapters-and-accelerators/fileact-interact/step-3a-add-a-file-receive-location-for-the-fileact-store-and-forward-scenario.md)   
 [Step 3C: Add a FILE Send Port to Capture the Sw:HandleFileRequest and Sw:HandleSnFRequest Messages for the FileAct Store and Forward Scenario](../../adapters-and-accelerators/fileact-interact/step-3c-add-file-send-port-to-get-sw-handlefilerequest-and-sw-handlesnfrequest.md)   
 [Step 3D: Add a FILEACT Send Port for the FileAct Store and Forward Scenario](../../adapters-and-accelerators/fileact-interact/step-3d-add-a-fileact-send-port-for-the-fileact-store-and-forward-scenario.md)