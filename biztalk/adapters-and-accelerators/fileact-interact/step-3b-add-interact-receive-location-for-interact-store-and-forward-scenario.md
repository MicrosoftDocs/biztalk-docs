---
description: "Learn more about: Step 3B: Add an INTERACT Receive Location for the InterAct Store and Forward Scenario"
title: "Step 3B: Add an INTERACT Receive Location for the InterAct Store and Forward Scenario"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: how-to
---
# Step 3B: Add an INTERACT Receive Location for the InterAct Store and Forward Scenario
Complete [Step 3A: Add a FILE Receive Location for the InterAct Store and Forward Scenario](../../adapters-and-accelerators/fileact-interact/step-3a-add-a-file-receive-location-for-interact-store-and-forward-scenario.md) before you begin this step.
  
## Add an INTERACT receive location  
  
1.  Start **BizTalk Server Administration**.  
  
2.  In the console tree, expand the BizTalk group, and then expand the BizTalk application for which you want to create a receive port.  
  
3.  Right-click **Receive Ports**, point to **New**, and then click **One-way Receive Port.**  
  
4.  In the **Receive Port Properties** window, name the receive port, Tutorial_IA_HandleRequestOneWay_SnF.  
  
5.  In the **Receive Port Properties** window, on the **Receive Locations** tab, click **New**.  
  
6.  In the **Receive Location Properties** window, on the **General** tab, from the **Transport type** drop-down list, select **INTERACT**, and then click **Configure**.  
  
7.  In the **INTERACT Transport Properties** dialog box, do the following:  
  
    |**Use this**|**To do this**|  
    |------------------|--------------------|  
    |**Password**|Type the password you use to connect to SAG. See SAG Help for more information.|  
    |**User name**|Type the user name you use to connect to SAG.|  
    |**Application name**|Type the Server \<Application Interface Name\> for the SAG box routing set.|  
    |**Crypto Mode**|From the drop-down list, select **Advanced**.|  
    |**LogMessageBody**|From the drop-down list, select **FALSE**. **Note:**  If you set to TRUE, it preserves the message body in the BizTalk Tracking database. However, for security reasons, the message body can never be viewed in the BAM portal.|  
    |**LogMessages**|From the drop-down list, select **TRUE**. This enables the message events to be captured and tracked in the BAM portal.|  
    |**Message format**|From the drop-down list, select **InterActMessage**.|  
    |**MemberRef**|From the drop-down list, select **ResponseHeader**.|  
    |**Non-Repudiation Indicator**|From the drop-down list, select **FALSE**.|  
    |**Responder**|Type the appropriate \<Responder\> string, based on your provisioning with SWIFT.|  
    |**ResponseCrypto**|From the drop-down list, select **FALSE**.|  
    |**Timeout**|Type an appropriate number of seconds before timeout should occur.|  
    |**Acquire queue**|Type the queue name, based on your provisioning with SWIFT.|  
    |**ForceAcquire**|From the drop-down list, select **TRUE**.|  
    |**Order by**|From the drop-down list, select **Interact**.|  
    |**Push session**|From the drop-down list, select **TRUE**.|  
    |**Recovery mode**|From the drop-down list, select **TRUE**.|  
    |**SNL end-point**|Type the appropriate end-point for the SAG routing set. This value should match the SnL endpoint you configured in SAG.|  
  
8.  Click **OK**.  
  
9. In the **Receive Location Properties** window, on the **General** tab, do the following:  
  
    |**Use this**|**To do this**|  
    |------------------|--------------------|  
    |**Receive handler**|From the drop-down list, select **BizTalkServerIsolatedHost**.|  
    |**Receive pipeline**|From the drop-down list, select **XMLReceive**.|  
  
10. Click **OK**.  
  
## Complete steps
 [Step 3: Create Send Ports and Receive Ports for the InterAct Store and Forward Scenario](../../adapters-and-accelerators/fileact-interact/step-3-create-send-and-receive-ports-for-interact-store-and-forward-scenario.md)   
 [Step 3A: Add a FILE Receive Location for the InterAct Store and Forward Scenario](../../adapters-and-accelerators/fileact-interact/step-3a-add-a-file-receive-location-for-interact-store-and-forward-scenario.md)   
 [Step 3C: Add a FILE Send Port to Capture the Sw:HandleRequest Message for the InterAct Store and Forward Scenario](../../adapters-and-accelerators/fileact-interact/step-3c-add-file-send-port-to-get-sw-handlerequest-interact-store-and-forward.md)  
 [Step 3D: Add an INTERACT Send Port for the InterAct Store and Forward Scenario](../../adapters-and-accelerators/fileact-interact/step-3d-add-an-interact-send-port-for-the-interact-store-and-forward-scenario.md)
