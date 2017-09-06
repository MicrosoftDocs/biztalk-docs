---
title: "Step 3B: Add an INTERACT Receive Location for the InterAct Real-Time Scenario | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 59780635-e1b6-4e74-a89a-73ec26d6c670
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Step 3B: Add an INTERACT Receive Location for the InterAct Real-Time Scenario
Complete [Step 3A: Add a FILE Receive Location for the InterAct Real-Time Scenario](../../adapters-and-accelerators/fileact-interact/step-3a-add-a-file-receive-location-for-the-interact-real-time-scenario.md) before you begin this step.
  
## Add an INTERACT receive location  
  
1.  Start **BizTalk Server Administration**.  
  
2.  In the console tree, expand the BizTalk group, and then expand the BizTalk application for which you want to create a receive port.  
  
3.  Right-click **Receive Ports**, point to **New**, and then click **One-way Receive Port.**  
  
4.  In the **Receive Port Properties** window, name the receive port, **Tutorial_IA_HandleRequestOneWay_RealTime**.  
  
5.  In the **Receive Port Properties** window, on the **Receive Locations** tab, click **New**.  
  
6.  In the **Receive Location Properties** window, on the **General** tab, from the **Transport type** drop-down list, select **INTERACT**, and then click **Configure**.  
  
7.  In the **INTERACT Transport Properties** dialog box, do the following:  
  
    |**Use this**|**To do this**|  
    |------------------|--------------------|  
    |**Password**|Type the password you use to connect to SAG. See SAG Help for more information.|  
    |**User name**|Type the user name you use to connect to SAG.|  
    |**Application name**|Type the Server \<*Application Interface Name*> for the SAG box routing set.|  
    |**Crypto Mode**|From the drop-down list, select **Advanced**.|  
    |**LogMessageBody**|From the drop-down list, select **FALSE**. **Note:**  If you set to TRUE, it preserves the message body in the tracking database. However, for security reasons, the message body can never be viewed in the BAM portal.|  
    |**LogMessages**|From the drop-down list, select **TRUE**. This enables the message events to be captured and tracked in the BAM portal.|  
    |**Message format**|From the drop-down list, select **InterActMessage**.|  
    |**MemberRef**|From the drop-down list, select **ResponseHeader**.|  
    |**Non-Repudiation Indicator**|From the drop-down list, select **FALSE**.|  
    |**Responder**|Type the appropriate \<*ResponderDN*> string, based on your provisioning with SWIFT.|  
    |**ResponseCrypto**|From the drop-down list, select **FALSE**.|  
    |**Timeout**|Type an appropriate number of seconds before connection timeout should occur.|  
    |**Acquire queue**|Leave the default value for this property. This property is used for Store-and-Forward scenarios.|  
    |**ForceAcquire**|Leave the default value for this property. This property is used for Store-and-Forward scenarios.|  
    |**Order by**|Leave the default value for this property. This property is used for Store-and-Forward scenarios.|  
    |**Push session**|Leave the default value for this property. This property is used for Store-and-Forward scenarios.|  
    |**Recovery mode**|Leave the default value for this property. This property is used for Store-and-Forward scenarios.|  
    |**SNL end-point**|Leave the default value for this property. This property is used for Store-and-Forward scenarios.|  
  
8.  Click **OK**.  
  
9. In the **Receive Location Properties** window, on the **General** tab, do the following:  
  
    |**Use this**|**To do this**|  
    |------------------|--------------------|  
    |**Receive handler**|From the drop-down list, select **BizTalkServerIsolatedHost**.|  
    |**Receive pipeline**|From the drop-down list, select **XMLReceive**.|  
  
10. Click **OK**.  
  
## See Also  
 [Step 3: Create Send and Receive Ports for the InterAct Real-Time Scenario](../../adapters-and-accelerators/fileact-interact/step-3-create-send-and-receive-ports-for-the-interact-real-time-scenario.md)   
 [Step 3A: Add a FILE Receive Location for the InterAct Real-Time Scenario](../../adapters-and-accelerators/fileact-interact/step-3a-add-a-file-receive-location-for-the-interact-real-time-scenario.md)   
 [Step 3C: Add a FILE Send Port to Capture the Sw:HandleRequest Message for the InterAct Real-Time Scenario](../../adapters-and-accelerators/fileact-interact/step-3c-add-file-send-port-to-get-sw-handlerequest-interact-real-time-scenario.md)   
 [Step 3D: Add a FILE Send Port to Capture the Sw:HandleResponse Message for the InterAct Real-Time Scenario](../../adapters-and-accelerators/fileact-interact/step-3d-add-file-send-port-to-get-sw-handleresponse-message-for-interact.md)   
 [Step 3E: Add an INTERACT Send Port for the InterAct Real-Time Scenario](../../adapters-and-accelerators/fileact-interact/step-3e-add-an-interact-send-port-for-the-interact-real-time-scenario.md)